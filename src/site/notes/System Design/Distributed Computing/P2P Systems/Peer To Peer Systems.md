---
{"dg-publish":true,"permalink":"/system-design/distributed-computing/p2-p-systems/peer-to-peer-systems/"}
---

#cse6603 

- An overlay organizes: 
    - the way different sites **communicate** with each other
    - the **storing of data objects** at the different sites.
- Overlays provide a method for retrieving objects, and typically support two basic operations using a key value pair:
    - **Set**: Insert the key-value tuple in the overlay.
    - **Get**: lookup and return the corresponding value using key.
- Overlays are typically represented as a graph,
    - Sites as nodes, 
    - Edges connecting these sites,
    - Categorized into:
        - **Unstructured** overlays.
        - **Structured** overlays.

### Unstructured Overlays

No specific structure on logical graph between the peers.

- Napster
- Gnutella


### Structured Overlays

- Impose a well-defined data structure on the various peers.

See, [[System Design/Distributed Computing/P2P Systems/Distributed Hash Tables (DHTs)|Distributed Hash Tables (DHTs)]]

See, [[System Design/Distributed Computing/Consistent Hashing|Consistent Hashing]]

