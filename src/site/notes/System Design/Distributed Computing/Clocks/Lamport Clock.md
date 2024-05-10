---
{"dg-publish":true,"permalink":"/system-design/distributed-computing/clocks/lamport-clock/"}
---



#cse6603 
- A process is modeled as a **sequence** of **totally ordered events**.


![Pasted image 20221031124205.png](/img/user/attachments/Pasted%20image%2020221031124205.png)


[Lamport Clock Algorithm](https://youtu.be/x-D8iFU1d-o?t=166)
 ![Pasted image 20221015213658.png](/img/user/attachments/Pasted%20image%2020221015213658.png)

- e → f then clock(e) < clock(f)
	If event *e* happend before event *f*, clock(e) < clock(f)

![Pasted image 20221031132426.png](/img/user/attachments/Pasted%20image%2020221031132426.png)


Improvement [[System Design/Distributed Computing/Clocks/Vector Clocks\|vector clocks]]