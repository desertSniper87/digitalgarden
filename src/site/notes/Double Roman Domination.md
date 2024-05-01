---
{"dg-publish":true,"permalink":"/double-roman-domination/"}
---

## Problem Definition

(from beeler.2016) 

For a graph $G = (V, E)$

**a double Roman dominating function** is a function

$f : V \rightarrow \{0, 1, 2, 3\}$

having the property that 
- if $f(v) = 0$, 
	- then vertex $v$  must have at least two neighbors assigned 2 under $f$  or one neighbor with $f(w) = 3$,
- if $f(v) = 1$, 
	- then vertex $v$ must have at least one neighbor with $f(w) \ge2$ .

- The weight($w$) of a double Roman dominating function  is the sum $\sum_{v\epsilon_V}f(v)$, and the minimum weight of a double Roman dominating function on  is the double Roman domination number of .


## Solution

- [[Meta Heuristics\|Meta Heuristics]]

## [[Star Graph\|Star Graph]]: $K_{1, n-1}$

![Double Roman Domination](https://www.researchgate.net/profile/Ana-Klobucar-Barisic/publication/346053100/figure/fig1/AS:962284222418944@1606437845398/Double-Roman-domination-on-star-graph.png)
 
$\gamma_{dR} (K_{1,n−1}) = 3$

## Resources

- [Mathematics | Free Full-Text | Double Roman Domination: A Survey (mdpi.com)](https://www.mdpi.com/2227-7390/11/2/351)
- [Double Roman domination - ScienceDirect](https://www.sciencedirect.com/science/article/pii/S0166218X1630155X?via%3Dihub) - **(Beeler et al. 2016)**
- [IEEE Xplore Full-Text PDF: DRD - A survey](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=8694775)
- [Some Properties of Double Roman Domination (hindawi.com)](https://www.hindawi.com/journals/ddns/2020/6481092/)


### [[Bipartite Graph\|Bipartite Graph]]

TBD
## Github Repos

- [maticdragan/sdrdp: This is a public repo containing instances and rough results on ILP models for solving Signed double Roman domination and Perfect double Roman domination problems (github.com)](https://github.com/maticdragan/sdrdp)
