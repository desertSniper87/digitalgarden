---
{"dg-publish":true,"permalink":"/x-road-encryption/"}
---

# Encryption Methods in the X-Road Data Exchange Layer

## 1. Introduction to X-Road Security Architecture

The X-Road data exchange layer serves as a secure and standardized method for organizations to exchange information over the internet.1 A fundamental aspect of its design is the assurance of confidentiality, integrity, and interoperability between participating entities.2 Security is not merely an add-on but a core tenet of X-Road, with robust mechanisms in place for authentication, authorization, and the secure transit of data.1

The Security Server stands as a critical component within the X-Road infrastructure, bearing the responsibility for managing various security aspects. These encompass the handling of cryptographic keys, digital certificates, message signing processes, and encryption functionalities.1 The design of X-Road prioritizes security at multiple layers. The concept of a "trusted network" 2 underscores the foundational nature of security within the system. This approach suggests a layered defense strategy where a combination of authentication, authorization, encryption, and integrity checks are employed to protect data exchanged through the platform. The central role of the Security Server in overseeing cryptographic operations and managing security keys 11 highlights its significance for understanding encryption within X-Road. Given its pivotal function, the security of the Security Server itself is paramount to the integrity of the entire ecosystem.

## 2. Securing Communication Channels with TLS

To safeguard data transmitted across the public internet, X-Road employs bidirectional HTTP over Transport Layer Security (TLS).1 This protocol is implemented to provide robust protection against eavesdropping and tampering, thereby ensuring the confidentiality and integrity of messages exchanged between X-Road participants.1

Furthermore, X-Road establishes mutual authentication between Security Servers through the use of authentication certificates. These certificates are issued by trusted Certification Authorities (CAs).1 Each Security Server is required to register its authentication certificate with the central server.17 In addition to securing communication between Security Servers, X-Road-internal TLS certificates are utilized to establish secure connections between the Security Server and the information systems that consume and provide services within the X-Road framework.1

The selection of TLS for securing communication channels indicates a reliance on a widely accepted and rigorously vetted cryptographic protocol. The implementation of bidirectional authentication adds a significant layer of security by verifying the identities of both the communicating client and server. The involvement of trusted CAs in the issuance of authentication certificates 1 underscores the importance of a Public Key Infrastructure (PKI) within X-Road's security framework. This PKI ensures a chain of trust, allowing participants to confidently verify the identities of others within the ecosystem.

## 3. Encryption for Data at Rest on the Security Server

The X-Road Security Server provides several options for encrypting data at rest, enhancing the protection of sensitive information stored within the system.20 These options include backup encryption, message log archive encryption, and message log database encryption.

### 3.1 Backup Encryption

The Security Server offers an opt-in feature to encrypt configuration backups, safeguarding sensitive data such as keys, certificates, and database credentials.20 This functionality is disabled by default.20 To enable backup encryption, the parameter backup-encryption-enabled must be set to true under the [proxy] section of the /etc/xroad/conf.d/local.ini configuration file.20 Administrators can also specify additional public keys for encryption using the backup-encryption-keyids parameter, which accepts a comma-separated list of key IDs.20 While a default backup encryption key is generated during the Security Server's initialization, it is strongly recommended to configure at least one additional key as a contingency in case the Security Server's private key is lost or compromised.20

Key management for backup encryption relies on GPG. To utilize additional encryption keys, the public key of each key must be exported from its storage location using the command gpg --output backupadmin.publickey --armor --export <key_identifier>, where <key_identifier> is the identifier of the key (e.g., email address).20 The exported public key file (backupadmin.publickey) then needs to be transferred to the Security Server and imported into the backup GPG keyring using the command gpg --homedir /etc/xroad/gpghome --import backupadmin.publickey.20 After importing, the key's trust level should be edited to add ultimate trust. This is done using the command gpg --homedir /etc/xroad/gpghome/ --edit-key <key_id>, where <key_id> is the ID of the imported key. At the gpg> prompt, the following sequence of commands should be entered: trust, followed by 5, then y, and finally quit.20 The Key ID obtained during the import process must then be added to the backup-encryption-keyids parameter in the /etc/xroad/conf.d/local.ini file.20

An example configuration snippet for enabling backup encryption with an additional key would be:

  

Ini, TOML

  
  

[proxy]  
backup-encryption-enabled = true  
backup-encryption-keyids = 96F20FF6578A5EF90DFBA18D8C003019508B5637  
  

20

Encrypted backup files can be decrypted using the corresponding private key with the command gpg --homedir /etc/xroad/gpghome --decrypt <backup_name> --output <output_file_name>.20 The reliance on GPG for backup encryption 20 signifies that X-Road leverages a well-established and trusted external tool for these critical cryptographic operations. This approach demonstrates a commitment to utilizing proven security solutions. The recommendation to configure additional encryption keys 20 highlights a crucial security best practice: ensuring redundancy in key management. By having multiple keys capable of decrypting backups, the risk of losing access to critical configuration data due to a single key compromise or loss is significantly reduced.

### 3.2 Message Log Archive Encryption

X-Road also provides the option to encrypt archived message log files using GPG.20 Similar to backup encryption, this feature is disabled by default.20 To enable it, the archive-encryption-enabled parameter must be set to true under the [message-log] section of the /etc/xroad/conf.d/local.ini file.20 The encryption process utilizes GnuPG, with the server's signing keypair, typically located in /etc/xroad/gpghome (and often the same as the backup keypair), serving to both sign the archive files and act as a fallback encryption key.20

For environments requiring more granular control, X-Road allows the configuration of member-specific encryption keys for message log archives. This can be achieved by setting the archive-grouping parameter to either member or subsystem and then defining the mappings between members or subsystems and their respective encryption keys in the file specified by the archive-encryption-keys-config parameter (the default path is /etc/xroad/messagelog/archive-encryption-mapping.ini).20 The archive-default-encryption-key parameter can be used to specify an alternative default encryption key ID that will be used when no member-specific key is defined or when archive-grouping is set to none.20

To configure member-specific encryption, a GPG keypair must be generated for each member. This can be done using the command gpg [--homedir <member_gpghome>] --quick-generate-key <member_identifier> default default never, where <member_identifier> is the member's X-Road identifier and <member_gpghome> is an optional specific GPG home directory for the member's keys.20 The public key then needs to be exported using gpg [--homedir <member_gpghome>] --export <member_identifier> > <output_file>.pgp.20 This exported public key file should be imported into the GPG keyring located at /etc/xroad/gpghome on the Security Server using the command gpg --homedir /etc/xroad/gpghome --import <public_key_file>.pgp.20 After importing, the trust level of the key should be edited to add ultimate trust, following the same procedure as outlined for backup encryption.20 Finally, the archive-encryption-mapping.ini file needs to be created or edited to include the mapping between the member's X-Road identifier and the Key ID of their public key, in the format INSTANCE/memberClass/memberCode = <key_id>.20

An example configuration for message log archive encryption with member-specific keys would be:

  

Ini, TOML

  
  

[message-log]  
archive-encryption-enabled = true  
archive-grouping = member  
archive-encryption-keys-config = /etc/xroad/messagelog/archive-encryption-mapping.ini  
archive-default-encryption-key = <default_key_id>  
  

20

Decryption of encrypted message log archives can be performed using the command gpg [--homedir <gpghome>] --decrypt <archive_name> --output <output_file_name>.20 The ability to configure member-specific encryption for message log archives 20 provides a valuable layer of fine-grained security control, allowing individual organizations within an X-Road ecosystem to protect their log data with encryption keys that they manage. This is particularly important in scenarios where multiple organizations share an X-Road instance. The use of the archive-encryption-keys-config file 20 enables a centralized and organized approach to managing the association between members and their respective encryption keys for log archives, simplifying the administrative overhead.

### 3.3 Message Log Database Encryption

The X-Road Security Server also offers an option to encrypt the message bodies stored within its message log database.20 This feature is disabled by default.20 To enable it, the messagelog-encryption-enabled parameter must be set to true under the [message-log] section of the /etc/xroad/conf.d/local.ini file.20 Additionally, the path to the keystore file must be specified using the messagelog-keystore parameter, along with the keystore password using messagelog-keystore-password, and the ID or alias of the encryption key within the keystore using messagelog-key-id.20

For managing the keys used in message log database encryption, X-Road leverages Java Keytool. A keystore can be created using the command keytool -genkey -alias <key_id> -keyalg AES -keysize 256 -keystore <keystore_path> -storetype pkcs12 -storepass <keystore_password>, where <key_id> is the desired key alias, <keystore_path> is the path to the keystore file (e.g., /etc/xroad/messagelog/messagelog.p12), and <keystore_password> is the password for the keystore.20 Alternatively, an existing key can be imported into a keystore using the command keytool -keystore <keystore_path> -storetype pkcs12 -importpassword -alias <key_id>.20 After creating or importing the key, the messagelog-keystore, messagelog-keystore-password, and messagelog-key-id parameters in the /etc/xroad/conf.d/local.ini file should be updated with the appropriate values.20

An example configuration for message log database encryption would be:

  

Ini, TOML

  
  

[message-log]  
messagelog-encryption-enabled = true  
messagelog-keystore = /etc/xroad/messagelog/messagelog.p12  
messagelog-keystore-password = somepassword  
messagelog-key-id = key1  
  

20

Encrypted messages stored in the database can be viewed using the ASIC web service, which is documented in the X-Road Security Server User Guide.20 The ASIC web service automatically handles the decryption of message bodies if they are encrypted. The choice of Java Keytool for managing database encryption keys 20 aligns with the fact that the Security Server is primarily a Java-based application.15 This integration with the Java platform's security features allows for a consistent approach to securing data within the application's components. However, this also implies that administrators responsible for configuring and maintaining database encryption need to possess familiarity with Java's security tools and concepts, which might differ from the tools and procedures used for managing GPG keys.

## 4. The Role of Digital Signatures in Message Integrity

In addition to encryption for confidentiality, X-Road employs digital signatures to ensure the integrity of transmitted messages. The X-Road transport message is signed within the security server, and this signature can be either a regular signature or a batch signature.17 For messages that include attachments, batch signatures are mandatory.17

Digital signatures serve multiple crucial purposes, including message authentication, ensuring data integrity, and providing non-repudiation.1 The management of signing keys and certificates is handled by the Security Server.1 These signing certificates are issued by trusted CAs to the member organizations participating in the X-Road ecosystem.1 To facilitate the verification of message parts, the x-hash-algorithm HTTP header is included in messages to indicate the specific hash algorithm used for calculating the hashes of the message parts.17

The utilization of both regular and batch signatures 17 suggests an optimization strategy for handling messages with varying complexities, particularly those containing attachments. Batch signing likely enhances performance by streamlining the signing process for multi-part messages. While digital signatures play a vital role in ensuring the integrity and authenticity of messages, it is important to note that they do not, by themselves, provide confidentiality for the message content during transit at the application level. The confidentiality of data in transit is primarily achieved through the TLS encryption established at the transport layer, while encryption at rest mechanisms protect stored data on the Security Server.

## 5. Advanced Encryption Considerations

As previously discussed, X-Road's primary mechanism for ensuring the confidentiality of data during transit is TLS.1 This transport layer security encrypts the communication channel between Security Servers, protecting the data as it travels across the network.

Based on the reviewed material, the core X-Road protocols do not inherently implement end-to-end encryption at the application level for the message payload itself. Mechanisms like JSON Web Encryption (JWE), which would encrypt the message content from the original sender to the final recipient, are not described as a standard feature of the X-Road message protocol. However, the X-Road protocol, particularly the REST message protocol, is designed to support any type of payload.25 This flexibility allows organizations with specific requirements for end-to-end confidentiality to implement their own encryption mechanisms at the application level, encrypting the payload before it is transmitted through the X-Road infrastructure. The absence of a built-in end-to-end payload encryption mechanism suggests that the confidentiality of the message content between the initial sender and the ultimate receiver relies mainly on the security provided by the TLS connection established between the Security Servers. Organizations that have stringent end-to-end confidentiality needs beyond what TLS offers can leverage the flexibility of the protocol to implement their own encryption solutions within the message payload.

## 6. Configuration Examples and Best Practices

To illustrate the configuration of encryption features on the X-Road Security Server, the following examples are provided. These configurations are typically performed by editing the /etc/xroad/conf.d/local.ini file.

  

Ini, TOML

  
  

[proxy]  
backup-encryption-enabled = true  
backup-encryption-keyids = <additional_key_id>  
  
[message-log]  
archive-encryption-enabled = true  
archive-grouping = member  
archive-encryption-keys-config = /etc/xroad/messagelog/archive-encryption-mapping.ini  
archive-default-encryption-key = <default_key_id>  
messagelog-encryption-enabled = true  
messagelog-keystore = /etc/xroad/messagelog/messagelog.p12  
messagelog-keystore-password = <password>  
messagelog-key-id = <key_alias>  
  

For managing GPG keys used in backup and message log archive encryption, common commands include:

- Exporting a public key: gpg --output backupadmin.publickey --armor --export <key_identifier>
    
- Importing a public key: gpg --homedir /etc/xroad/gpghome --import backupadmin.publickey
    
- Decrypting a backup file: gpg --homedir /etc/xroad/gpghome --decrypt <backup_name> --output <output_file_name>
    

For managing keystores and keys used in message log database encryption, Java Keytool commands are essential:

- Creating a new keystore and key: keytool -genkey -alias <key_alias> -keyalg AES -keysize 256 -keystore /etc/xroad/messagelog/messagelog.p12 -storetype pkcs12 -storepass <password>
    

In addition to proper configuration, adhering to security best practices is crucial for maintaining a robustly encrypted X-Road environment. These practices include:

- Employing strong and unique passwords for all encryption keys and keystores.
    
- Ensuring the secure, preferably offline, storage of private keys and backup encryption keys. Consider the use of Hardware Security Modules (HSMs) for enhanced protection of sensitive cryptographic keys.13
    
- Implementing regular rotation of encryption keys in accordance with organizational security policies.
    
- Proactively monitoring the validity and expiry of TLS certificates and ensuring their timely renewal.
    
- Enabling encryption for backups and message logs, especially when they contain sensitive data.
    
- In multi-tenant X-Road environments, implementing member-specific encryption for message log archives to provide enhanced data isolation and security.
    
- Conducting regular audits of encryption configurations and key management practices to identify and address any potential vulnerabilities.
    
- For use cases with stringent end-to-end confidentiality requirements, considering the implementation of application-level encryption within the message payload to provide an additional layer of protection.
    
- Ensuring that appropriate access controls are in place for the Security Server and its associated configuration files to prevent unauthorized modifications.
    
- Keeping the X-Road Security Server software updated to benefit from the latest security patches and features, which often include improvements to encryption algorithms and protocols.22
    

The provided configuration examples serve as a practical foundation for administrators looking to implement encryption within their X-Road deployments. However, it is imperative that these examples are adapted to the specific needs and security requirements of each unique environment. The outlined best practices emphasize that security management is an ongoing process that demands continuous attention to the lifecycle of keys and certificates, as well as regular reviews of security configurations.

## 7. Conclusion

The X-Road data exchange layer incorporates a comprehensive security framework that includes various encryption methods to protect the confidentiality of data. It relies on TLS for securing communication channels between Security Servers and offers several opt-in encryption options for data at rest on the Security Server, such as backup encryption, message log archive encryption, and message log database encryption. The proper configuration and diligent management of these encryption mechanisms, alongside robust key and certificate management practices, are essential for establishing and maintaining a secure X-Road ecosystem. While X-Road provides strong transport layer security and encryption for stored data, organizations with specific needs for end-to-end confidentiality of message payloads may need to implement additional encryption measures at the application level. Complementing these encryption methods, digital signatures play a critical role in ensuring the integrity, authenticity, and non-repudiation of messages exchanged through the X-Road platform, contributing to a holistic security posture for data exchange.

#### Works cited

1. X-Road Security Architecture | X-Road, accessed May 7, 2025, [https://docs.x-road.global/Architecture/arc-sec_x_road_security_architecture.html](https://docs.x-road.global/Architecture/arc-sec_x_road_security_architecture.html)
    
2. X-Road – The Free and Open Source Data Exchange Layer - API Conference, accessed May 7, 2025, [https://apiconference.net/blog-en/x-road-the-free-and-open-source-data-exchange-layer/](https://apiconference.net/blog-en/x-road-the-free-and-open-source-data-exchange-layer/)
    
3. From X-Road® to LEX Road? Confidentiality, Integrity, and Interoperability with the X-Road® Open Source Data Exchange Layer - ComplexDiscovery, accessed May 7, 2025, [https://complexdiscovery.com/from-x-road-to-lex-road-confidentiality-integrity-and-interoperability-with-the-x-road-open-source-data-exchange-layer/](https://complexdiscovery.com/from-x-road-to-lex-road-confidentiality-integrity-and-interoperability-with-the-x-road-open-source-data-exchange-layer/)
    
4. [EE03] X-Road - Interoperable Europe Portal, accessed May 7, 2025, [https://interoperable-europe.ec.europa.eu/sites/default/files/inline-files/EE03%20X-Road_v1.00_0.pdf](https://interoperable-europe.ec.europa.eu/sites/default/files/inline-files/EE03%20X-Road_v1.00_0.pdf)
    
5. x-Road – interoperability services - e-Estonia, accessed May 7, 2025, [https://e-estonia.com/solutions/x-road-interoperability-services/x-road/](https://e-estonia.com/solutions/x-road-interoperability-services/x-road/)
    
6. Why digital sovereignty matters and how X-Road makes it happen - Nortal, accessed May 7, 2025, [https://nortal.com/insights/why-digital-sovereignty-matters-and-how-x-road-makes-it-happen](https://nortal.com/insights/why-digital-sovereignty-matters-and-how-x-road-makes-it-happen)
    
7. X-Road® - Gaia-X, accessed May 7, 2025, [https://gaia-x.eu/wp-content/uploads/2024/11/X-RoadNIIS.pdf](https://gaia-x.eu/wp-content/uploads/2024/11/X-RoadNIIS.pdf)
    
8. Architecture Guidelines for Service Providers and Consumers | Handbook, accessed May 7, 2025, [https://docs.devland.is/products/x-road/x-road-architecture-guidelines-for-service-providers-and-consumers](https://docs.devland.is/products/x-road/x-road-architecture-guidelines-for-service-providers-and-consumers)
    
9. X-Road® Architecture, accessed May 7, 2025, [https://x-road.global/architecture](https://x-road.global/architecture)
    
10. X-Road® Technology Overview, accessed May 7, 2025, [https://x-road.global/x-road-technology-overview](https://x-road.global/x-road-technology-overview)
    
11. X-Road® — Security, accessed May 7, 2025, [https://x-road.global/security](https://x-road.global/security)
    
12. X-Road®, accessed May 7, 2025, [https://x-road.global/](https://x-road.global/)
    
13. High-Performance Qualified Digital Signatures for X-Road - Cybernetica - Research Library, accessed May 7, 2025, [https://research.cyber.ee/~janwil/publ/batchsignatures.pdf](https://research.cyber.ee/~janwil/publ/batchsignatures.pdf)
    
14. X-Road/doc/Architecture/arc-sec_x_road_security_architecture.md at develop - GitHub, accessed May 7, 2025, [https://github.com/nordic-institute/X-Road/blob/develop/doc/Architecture/arc-sec_x_road_security_architecture.md](https://github.com/nordic-institute/X-Road/blob/develop/doc/Architecture/arc-sec_x_road_security_architecture.md)
    
15. X-Road: Security Server Architecture, accessed May 7, 2025, [https://docs.x-road.global/Architecture/arc-ss_x-road_security_server_architecture.html](https://docs.x-road.global/Architecture/arc-ss_x-road_security_server_architecture.html)
    
16. X-Road/doc/Architecture/arc-ss_x-road_security_server_architecture.md at develop - GitHub, accessed May 7, 2025, [https://github.com/ria-ee/X-Road/blob/develop/doc/Architecture/arc-ss_x-road_security_server_architecture.md](https://github.com/ria-ee/X-Road/blob/develop/doc/Architecture/arc-ss_x-road_security_server_architecture.md)
    
17. X-Road: Message Transport Protocol, accessed May 7, 2025, [https://docs.x-road.global/Protocols/pr-messtransp_x-road_message_transport_protocol.html](https://docs.x-road.global/Protocols/pr-messtransp_x-road_message_transport_protocol.html)
    
18. X-Road: 7.5.1 - X-tee iseteenindus, accessed May 7, 2025, [https://x-tee.ee/docs/live/xroad/terms_x-road_docs.html](https://x-tee.ee/docs/live/xroad/terms_x-road_docs.html)
    
19. X-Road Knowledge Base - NIIS Confluence, accessed May 7, 2025, [https://nordic-institute.atlassian.net/wiki/spaces/XRDKB/pages/16252930](https://nordic-institute.atlassian.net/wiki/spaces/XRDKB/pages/16252930)
    
20. SECURITY SERVER USER GUIDE | X-Road, accessed May 7, 2025, [https://docs.x-road.global/7.4.2/Manuals/ug-ss_x-road_6_security_server_user_guide.html](https://docs.x-road.global/7.4.2/Manuals/ug-ss_x-road_6_security_server_user_guide.html)
    
21. X-Road v7.3.0 Release Notes, accessed May 7, 2025, [https://nordic-institute.atlassian.net/wiki/spaces/XRDKB/pages/196313089/X-Road+v7.3.0+Release+Notes](https://nordic-institute.atlassian.net/wiki/spaces/XRDKB/pages/196313089/X-Road+v7.3.0+Release+Notes)
    
22. X-Road v7.0.0 Release Notes - NIIS Confluence, accessed May 7, 2025, [https://nordic-institute.atlassian.net/wiki/spaces/XRDKB/pages/4915897/X-Road+v7.0.0+Release+Notes](https://nordic-institute.atlassian.net/wiki/spaces/XRDKB/pages/4915897/X-Road+v7.0.0+Release+Notes)
    
23. Protecting Data at Rest in X-Road 7 - Nordic Institute for Interoperability Solutions, accessed May 7, 2025, [https://www.niis.org/blog/2021/10/2/protecting-data-at-rest-in-x-road-7](https://www.niis.org/blog/2021/10/2/protecting-data-at-rest-in-x-road-7)
    
24. Table of contents - X-Road Knowledge Base - NIIS Confluence, accessed May 7, 2025, [https://nordic-institute.atlassian.net/wiki/display/XRDKB/Migration+Guide+from+X-Road+6+to+X-Road+7?src=contextnavpagetreemode](https://nordic-institute.atlassian.net/wiki/display/XRDKB/Migration+Guide+from+X-Road+6+to+X-Road+7?src=contextnavpagetreemode)
    
25. How X-Road Supports REST APIs? - Interoperable Europe Portal, accessed May 7, 2025, [https://interoperable-europe.ec.europa.eu/sites/default/files/event/attachment/2020-10/2020-09-25-How_Petteri.pdf](https://interoperable-europe.ec.europa.eu/sites/default/files/event/attachment/2020-10/2020-09-25-How_Petteri.pdf)
    
26. Signatures & consent - SDG Digital Acceleration Agenda, accessed May 7, 2025, [https://www.sdg-digital.org/technical-enablers/signatures-consent](https://www.sdg-digital.org/technical-enablers/signatures-consent)
    
27. X-Road Logs Explained – Part 2 - Nordic Institute for Interoperability Solutions, accessed May 7, 2025, [https://www.niis.org/blog/2018/6/3/x-road-logs-explained-part-2](https://www.niis.org/blog/2018/6/3/x-road-logs-explained-part-2)
    
28. Signed Document Download and Verification Manual - X-Road, accessed May 7, 2025, [https://docs.x-road.global/Manuals/ug-sigdoc_x-road_signed_document_download_and_verification_manual.html](https://docs.x-road.global/Manuals/ug-sigdoc_x-road_signed_document_download_and_verification_manual.html)
    
29. X-Road Knowledge Base - NIIS Confluence, accessed May 7, 2025, [https://nordic-institute.atlassian.net/wiki/spaces/XRDKB/pages/4916191](https://nordic-institute.atlassian.net/wiki/spaces/XRDKB/pages/4916191)
    
30. X-Road: Message Protocol for REST, accessed May 7, 2025, [https://docs.x-road.global/Protocols/pr-rest_x-road_message_protocol_for_rest.html](https://docs.x-road.global/Protocols/pr-rest_x-road_message_protocol_for_rest.html)
    
31. X-Road Message Protocol for REST - Squarespace, accessed May 7, 2025, [https://static1.squarespace.com/static/59ba41ee64b05fd6531f498d/t/5bb45ac253450a1e7e6f802f/1538546370830/X-Road_Message_Protocol_for_REST-v0.1.0.pdf](https://static1.squarespace.com/static/59ba41ee64b05fd6531f498d/t/5bb45ac253450a1e7e6f802f/1538546370830/X-Road_Message_Protocol_for_REST-v0.1.0.pdf)
    
32. X-Road communication protocol - Suomi.fi Data Exchange Layer ..., accessed May 7, 2025, [https://kehittajille.suomi.fi/services/data-exchange-layer/support-articles/data-exchange/x-road-communication-protocol](https://kehittajille.suomi.fi/services/data-exchange-layer/support-articles/data-exchange/x-road-communication-protocol)
    
33. Two Steps from X-Road REST Support - Nordic Institute for Interoperability Solutions, accessed May 7, 2025, [https://www.niis.org/blog/2019/3/25/two-steps-from-the-x-road-rest-support](https://www.niis.org/blog/2019/3/25/two-steps-from-the-x-road-rest-support)
    
34. aws-samples/aws-best-practices-for-xroad-security-servers: Best Practices for Deploying X-Road Security Servers on AWS - GitHub, accessed May 7, 2025, [https://github.com/aws-samples/aws-best-practices-for-xroad-security-servers](https://github.com/aws-samples/aws-best-practices-for-xroad-security-servers)
    

