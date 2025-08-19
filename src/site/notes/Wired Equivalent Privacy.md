---
{"dg-publish":true,"permalink":"/wired-equivalent-privacy/"}
---

#### WEP Challenge-Response Handshake

The challenge-response handshake is a process to establish a secure connection between a WAP and a client device in a wireless network that uses the WEP security protocol. This involves exchanging packets between the WAP and the client device to authenticate the device and establish a secure connection.

| **Step** | **Who**  | **Description**                                                                                                                              |
| -------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| 1        | `Client` | Sends an association request packet to the WAP, requesting access.                                                                           |
| 2        | `WAP`    | Responds with an association response packet to the client, which includes a challenge string.                                               |
| 3        | `Client` | Calculates a response to the challenge string and a shared secret key and sends it back to the WAP.                                          |
| 4        | `WAP`    | Calculates the expected response to the challenge with the same shared secret key and sends an authentication response packet to the client. |

## vs [[WiFi Protected Access\|WPA]]

`WEP` uses a `40-bit` or `104-bit` key to encrypt data, while `WPA using AES` uses a `128-bit` key. Longer keys provide more robust encryption and are more resistant to attacks. However, it is vulnerable to various attacks that can allow an attacker to decrypt data transmitted over the network. In addition, WEP is not compatible with newer devices and operating systems and is generally no longer considered secure. Finally, `WEP` uses the `RC4 cipher` encryption algorithm, which makes it vulnerable to attacks.

However, WEP uses a `shared key` for authentication, which means the same key is used for encryption and authentication. There are two versions of the WEP protocol:

- `WEP-40`/`WEP-64`
- `WEP-104`

`WEP-40`, also known as `WEP-64`, uses a `40-bit` (secret) key, while `WEP-104` uses a `104-bit` key. The key is divided into an [Initialization Vector](https://en.wikipedia.org/wiki/Initialization_vector) (`IV`) and a `secret key`.

The `IV` is a small value included in the packet header along with the encrypted data and is used to create the key for both `WEP-40` and `WEP-104` and is included to ensure that each key is unique. The secret key is a series of random bits used to encrypt the data. However, the `WEP-104` has a `80-bits` long `secret key`. Let us look at the following table to see the differences clearly:

|**Protocol**|**IV**|**Secret Key**|
|---|---|---|
|`WEP-40`/`WEP-64`|24-bit|40-bit|
|`WEP-104`|24-bit|80-bit|

However, since the IV in WEP is relatively small, we can brute force it, try every possible combination of characters for it, and determine the correct value. Afterward, we can use it to decrypt the data in the packet. This allows us to access the data transmitted over the wireless network and potentially compromise the network's security.