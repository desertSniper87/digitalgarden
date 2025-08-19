---
{"dg-publish":true,"permalink":"/dominating-set/"}
---


- [Wikipedia](https://en.wikipedia.org/wiki/Dominating_set#:~:text=In%20graph%20theory%2C%20a%20dominating,smallest%20dominating%20set%20for%20G.)


> In [[graph theory\|graph theory]], a dominating set for a **graph G** is a **subset D** of its vertices, such that any vertex of G is in D, or has a neighbor in D. The domination number γ(G) is the number of vertices in a smallest dominating set for G

every vertex in the graph is:
- in the dominating set
- or adjacent to a vertex in the dominating set.

![dominating set](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e1/Dominating-set.svg/300px-Dominating-set.svg.png)
## Variations

```ad-note
#perplexity 
1. **[[Total Dominating Set]] Problem**:
    
    - In this variant, a total dominating set is considered, where vertices do not cover themselves. It involves finding a subset of vertices in a graph such that every vertex has a neighbor in the set.
    
2. **[[Connected Dominating Sets]]**:
    
    - This variant focuses on finding dominating sets where every vertex not in the set is adjacent to at least one vertex in the dominating set.
    
3. **[[Power Domination]]**:
    
    - Power domination is another variant where a minimum-size vertex set is determined such that each vertex is either in the set or adjacent to at least one vertex in the set.
    
4. **[[Paired-Domination]]**:
    
    - Paired-domination is a variant where two dominating sets are sought, and the sum of their sizes along with their intersection is minimized.
```
## Videos

- https://youtu.be/0jKRpZch81I

## Example of Dominating Set Problems

- [[Roman Domination\|Roman Domination]]
- [[Double Roman Domination\|Double Roman Domination]]