---
dg-publish: true
---
#cse6603 

[https://www.cs.princeton.edu/courses/archive/fall19/cos418/docs/L8-dhts.pdf](https://www.cs.princeton.edu/courses/archive/fall19/cos418/docs/L8-dhts.pdf)
- Hash table using [[System Design/Distributed Computing/Consistent Hashing\|Consistent Hashing]]
- No central index server. 
- Maps objects(files) to sites, 
- Key value lookup.
- Each site also maintains a table that defines the next-hop for lookup operations (Hash table in every node.)

## Videos

### [Distributed Hash Tables: In a nutshell - YouTube](https://www.youtube.com/watch?v=tz-Q-eW8FbQ)

- 


#### See, [[System Design/Distributed Computing/P2P Systems/Chords\|Chords]] and [[System Design/Distributed Computing/P2P Systems/BitTorrent\|BitTorrent]]