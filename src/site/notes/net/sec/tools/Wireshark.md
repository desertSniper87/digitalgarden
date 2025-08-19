---
{"dg-publish":true,"permalink":"/net/sec/tools/wireshark/"}
---

- [User guide](https://www.wireshark.org/docs/wsug_html_chunked/)
- [[Wireshark - Decrypting TLS\|Wireshark - Decrypting TLS]]
- [[Wireshark - FTP Dissector\|Wireshark - FTP Dissector]]

- `Wireshark` is a free and open-source [[network traffic\|network traffic]] analyzer much like [[tcpdump\|tcpdump]] but with a graphical interface
- Wireshark is multi-platform and **capable of capturing live data** off many different interface types:
	 - WiFi
	 - USB
	 - Bluetooth 
- Can save the traffic to several different formats

## Capabilities

- [[IEEE 802.3\|Ethernet]], [[IEEE 802.11\|IEEE 802.11]], [[Point-to-Point Protocol\|PPP]]/[[High-Level Data Link Control\|HDLC]], [[ATM\|ATM]], [[IEEE 802.15\|Bluetooth]], [[USB Drive\|USB]], [[Token Ring\|Token Ring]], [[Frame Relay\|Frame Relay]], [[Fiber Distributed Data Interface\|FDDI]]
- Decryption capabilities for [[Internet Protocol Security\|IPSec]], [[Internet Security Association and Key Management\|ISAKMP]], [[net/sec/Kerberos\|Kerberos]], [[net/protocols/Simple Network Management Protocol\|SNMPv3]], SSL/TLS, WEP, and WPA/WPA2

Alternative: [[tcpflow\|tcpflow]], [[tshark\|tshark]], [[termshark\|termshark]]
## Statistics

#todo




## The Statistics and Analyze Tabs


- The Statistics and Analyze tabs can provide us with great insight into the data we are examining
- It can show us everything from the top talkers in our environment to specific conversations and even breakdown by IP and protocol.

### Statistics Tab

![Wireshark interface showing address statistics, protocol hierarchy, and conversation details for network traffic analysis, including IP addresses, packet counts, and protocol breakdowns.](https://academy.hackthebox.com/storage/modules/81/wireshark-statistics.png)

### Analyze


- From the Analyze tab
	 - we can utilize plugins that allow us to do things such as 
		 - following TCP streams
		 - filter on conversation types
		 - prepare new packet filters and examine the expert info Wireshark generates about the traffic

#### Analyze Tab

![Wireshark Analyze menu showing options for display filters, applying filters, enabled protocols, and expert information.](https://academy.hackthebox.com/storage/modules/81/analyze.png)

#### Following TCP Streams


- Wireshark can stitch TCP packets back together to recreate the entire stream in a readable format
- This ability also allows us to pull data (`images, files, etc.`) out of the capture
- This works for almost any protocol that utilizes TCP as a transport mechanism.

To utilize this feature:

- right-click on a packet from the stream we wish to recreate.
- select follow → TCP
- this will open a new window with the stream stitched back together. From here, we can see the entire conversation.

### Follow A Stream Via GUI

![GIF showcasing the 'Follow a Stream' functionality.](https://academy.hackthebox.com/storage/modules/81/follow-tcp.gif)

Alternatively, we can utilize the filter `tcp.stream eq #` to find and track conversations captured in the pcap file.

## Filter For A Specific TCP Stream

![Wireshark capture showing TCP and Telnet packets between IPs 10.100.18.5 and 10.100.16.1, with sequence and acknowledgment numbers.](https://academy.hackthebox.com/storage/modules/81/tcp-stream.gif)


- Notice that the first three packets in the image above have a full TCP handshake
- Following those packets, we can see the stream transferring data
- We have cleared anything not related out of view by utilizing the filter, and we now can see the conversation in order.

To extract files from a stream:

- stop your capture.
- Select the File radial → Export → , then select the protocol format to extract from.
- (DICOM, HTTP, SMB, etc.)

### Extract Files From The GUI

![GIF showcasing the extraction of files from an HTTP stream.](https://academy.hackthebox.com/storage/modules/81/extract-http.gif)


- Another exciting way to grab data out of the [[PCAP\|PCAP]] file comes from [[File Transfer Protocol\|FTP]]
- The File Transfer Protocol moves data between a server and host to pull it out of the raw bytes and reconstruct the file (image, text documents, etc.) 
- FTP utilizes [[net/protocols/Transmission Control Protocol\|TCP]] as its transport protocol and uses ports `20 & 21` to function
- **TCP port 20 is used to transfer data between the server and host, while port 21 is used as the FTP control port**
- Any commands such as login, listing files, and issuing download or uploads happen over this port


