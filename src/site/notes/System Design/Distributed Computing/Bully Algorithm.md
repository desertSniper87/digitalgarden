---
{"dg-publish":true,"permalink":"/system-design/distributed-computing/bully-algorithm/"}
---

#cse6603 

See, [Wikipedia](https://en.wikipedia.org/wiki/Bully_algorithm), [Bhanu Priya](https://www.youtube.com/watch?v=R1FfoED7OGo), [colostate (good example)](https://www.cs.colostate.edu/~cs551/CourseNotes/Synchronization/BullyExample.html)

- Select the process with the ==highest process-id==.
- Any process can initiate an election if
    - it just recovered from a **failure** or 
    - it suspects that the current coordinator has **failed**.
	    - Cannot communicate with leader.
- Three types of messages are used: **election**, *ok*, and ==I won==.

#### Bully Algo Steps
1. An initiating process p sends **election** messages to all processes with higher IDs and awaits for *ok* messages.
2. If a process receives an **election** message, it returns an *ok* message and starts an **election**.
    - election message comes from process of lower IDs.
    - Repeat step 1.
3. If it receives any *ok* messages, it drops out and waits for an ==I won== message.
    - *ok* message comes from process having higher id.
4. If no *ok* messages are received, p becomes the coordinator and sends ==I won== to all processes with lower IDs.
5. If a process receives an ==I won== message, then the sender is the coordinator.