---
{"dg-publish":true,"permalink":"/net/total-order-multicast/","dgPassFrontmatter":true}
---

#cse6603 

Also known as or atomic order multicast


- Processes collectively agree on sequence numbers (or priority) in three rounds.
    1. The sender sends the **message m** _with a unique identifier_ to all receivers.
    2. Receivers suggest **priority** (sequence number) and reply to sender with the **proposed priority**.
    3. The sender collects all **proposed priorities**
        - decides on the final priority (breaking ties with process ids)
        - Re-sends the agreed final priority for message m.


See [https://www.andrew.cmu.edu/course/15-446/applications/ln/l3.html](https://www.andrew.cmu.edu/course/15-446/applications/ln/l3.html)

[https://courses.engr.illinois.edu/cs425/fa2009/L5tmp.pdf](https://courses.engr.illinois.edu/cs425/fa2009/L5tmp.pdf)