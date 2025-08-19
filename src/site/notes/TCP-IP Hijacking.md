---
{"dg-publish":true,"permalink":"/tcp-ip-hijacking/"}
---


In TCP/IP hijacking, an attacker intercepts an established connection between two communicating parties by using spoofed packets and then pretends to be one of those parties. In this approach, the attacker uses spoofed packets to redirect the TCP traffic to their own machine. Once this is successful, the victim's connection hangs, and the attacker is able to communicate with the host’s machine on behalf of the victim. To launch a TCP/IP hijacking attack, both the victim and attacker must be on the same network. The target server and the victim machines can be located anywhere. By using this technique, an attacker can easily attack systems that use one-time passwords. TCP/IP hijacking is performed through the following steps. ▪ The attacker sniffs the victim's connection and uses the victim’s IP address to send a spoofed packet with the predicted sequence number.
▪ The receiver processes the spoofed packet, increments the sequence number, and sends an acknowledgement to the victim's IP address.
▪ The victim machine is unaware of the spoofed packet. Therefore, it ignores the receiver machine’s ACK packet and turns off sequence number count.
▪ Consequently, the receiver receives packets with the incorrect sequence number. ▪ The attacker forces the victim’s connection with the receiver machine into a desynchronized state.
▪ The attacker tracks sequence numbers and continuously spoofs packets that originate from the victim’s IP address.
▪ The attacker continues to communicate with the receiver machine, while the victim’s connection hangs.
According to above figure, the next expected sequence number is 1420. If the attacker transmits that packet sequence number before the user does, they can desynchronize the connection between the user and server.
If the attacker sent the data with the expected sequence number before the user could, the server would be synchronized with the attacker. This leads to the establishment of a connection between the attacker and server. Then, the server would drop the data sent by the user with the correct sequence number, believing it to be a resent packet. The user is unaware of the attacker’s action and may resend the data packet because the user does not receive an ACK for their TCP packet. However, the server would drop all the packets resent by the user. Thus, the local session hijacking attack is successfully completed.
![TCP-IP Hijacking-1755268211903.webp|777x572](/img/user/TCP-IP%20Hijacking-1755268211903.webp)