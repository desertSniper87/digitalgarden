---
{"dg-publish":true,"permalink":"/double-roman-domination/","tags":["drdp"]}
---

---
- [[drdp - example graphs\|drdp - example graphs]]

{ .block-language-dataview}
## Problem Definition

(from [[#Resources|beeler.2016]]) 

For a graph $G = (V, E)$

**a double Roman dominating function** is a function

$f : V \rightarrow \{0, 1, 2, 3\}$

having the property that 
- if $f(v) = 0$, 
	- then vertex $v$ must have at least **two neighbours assigned *$f(w) = 2$*** under $f$ or **one neighbor with $f(w) = 3$,**
- if $f(v) = 1$, 
	- then vertex $v$ must have at least one neighbor with $f(w) \ge2$ .

- The weight($w$) of a double Roman dominating function is the sum $\sum_{v\epsilon_V}f(v)$, and the minimum weight of a double Roman dominating function on is the double Roman domination number of .


## Solution

### [[Meta Heuristics\|Meta Heuristics]]

### Agarwal et. al. 24


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



[F​​e​tc​h​in​​g ​T​​it​le​​](https://www.sciencedirect.com/science/article/pii/S1568494624000802)

</div></div>


#### [[Ant Colony Optimization\|ACO]] Solution

- [[Double Roman Domination - Ant Colony Optimization Solution\|Double Roman Domination - Ant Colony Optimization Solution]]
## [[Star Graph\|Star Graph]]: $K_{1, n-1}$

![Double Roman Domination|302x351](https://www.researchgate.net/profile/Ana-Klobucar-Barisic/publication/346053100/figure/fig1/AS:962284222418944@1606437845398/Double-Roman-domination-on-star-graph.png)
 
$\gamma_{dR} (K_{1,n−1}) = 3$

- 𝛾𝑑𝑅(𝐺) is the minimum weight of a DROMDF on 𝐺
- 𝑉 (𝐺) represent the vertex set 

## Resources

- [Mathematics | Free Full-Text | Double Roman Domination: A Survey (mdpi.com)](https://www.mdpi.com/2227-7390/11/2/351)
- [Double Roman domination - ScienceDirect](https://www.sciencedirect.com/science/article/pii/S0166218X1630155X?via%3Dihub) - **(Beeler et al. 2016)**
- [IEEE Xplore Full-Text PDF: DRD - A survey](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=8694775)
- [Some Properties of Double Roman Domination (hindawi.com)](https://www.hindawi.com/journals/ddns/2020/6481092/)


### [[Bipartite Graph\|Bipartite Graph]]

TBD
## Github Repos

- [maticdragan/sdrdp: This is a public repo containing instances and rough results on ILP models for solving Signed double Roman domination and Perfect double Roman domination problems (github.com)](https://github.com/maticdragan/sdrdp)

![Double Roman Domination-1754424007701.webp](/img/user/Double%20Roman%20Domination-1754424007701.webp)


- [[Heuristics vs Meta Heuristics\|Heuristics vs Meta Heuristics]]
- [[Approximation Factor\|Approximation Factor]]