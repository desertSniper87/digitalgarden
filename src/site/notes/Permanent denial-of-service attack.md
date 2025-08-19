---
{"dg-publish":true,"permalink":"/permanent-denial-of-service-attack/"}
---

*DoS attack where an attacker sends e-mails, Internet relay chats (IRCs), tweets, and posts videos with fraudulent content for hardware updates to the victim with the intent of modifying and corrupting the updates with vulnerabilities or defective firmware*

Permanent denial-of-service (PDoS), also known loosely as phlashing, is an attack that damages a system so badly that it requires replacement or reinstallation of hardware
- Unlike the distributed denial-of-service attack, a PDoS attack exploits security flaws which allow **remote administration on the management interfaces of the victim's hardware, such as [[Routers\|Routers]], [[printer\|printer]]s, or other networking hardware**
- The attacker uses these vulnerabilities to replace a device's firmware with a modified, corrupt, or defective firmware image—a process which when done legitimately is known as flashing
- The intent is to brick the device, rendering it unusable for its original purpose until it can be repaired or replaced
- The PDoS is a pure hardware-targeted attack that can be much faster and requires fewer resources than using a botnet in a DDoS attack
- Because of these features, and the potential and high probability of security exploits on network-enabled embedded devices, this technique has come to the attention of numerous hacking communities
- BrickerBot, a piece of malware that targeted IoT devices, used PDoS attacks to disable its targets
- PhlashDance is a tool created by Rich Smith (an employee of Hewlett-Packard's Systems Security Lab) used to detect and demonstrate PDoS vulnerabilities at the 2008 EUSecWest Applied Security Conference in London, UK.


## Example

Bob is frustrated with his competitor, Brownies Inc., and he decides to launch an attack that would result in severe financial losses to his competitor
- He plans and executes his attack carefully at an appropriate moment
- Meanwhile, Trent, an administrator at Brownies Inc., realized that their primary financial transaction server had been attacked
- As a result, one of their pieces of network hardware is rendered unusable, and he needs to replace or reinstall it to resume services
- This process involves human interaction to fix it.   