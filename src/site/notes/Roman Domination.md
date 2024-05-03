---
{"dg-publish":true,"permalink":"/roman-domination/"}
---


A subset of [[dominating set\|Dominating Set]] Problems

***a strategy of Emperor Constantine for defending the Roman Empire.***

Roman dominating function is **a colouring of the vertices of a graph with the colours {0; 1; 2} such that every vertex coloured 0 is adjacent to at least one vertex coloured 2**

>    An interesting variety of domination that is popular because of its historical signifi cance is called Roman domination. In the 4th century Emperor Constantine, in order to defend the Roman Empire, decreed that two types of armies should be placed in cities in such a way that the entire Empire could be secured. The first type of army was **highly trained and mobile**, and could move from city to city to defend against any attack. The second type of army was a **local militia** that was **permanently stationed at a given city**. The Emperor decreed that ***no mobile army could ever leave a city to defend another if in doing so it left the originating city undefended***. Thus, two armies were stationed at some cities, only a local militia at others, and other cities had no army.

- [[NP-hard\|NP-hard]] combinatorial [[optimization problem\|optimization problem]]
- [[Undirected Graph\|Undirected Graph]] (Simple)

### Problem Statement

Given a graph, a Roman Dominating Function is a function that labels the vertices of the graph with an integer between 0,1,2, satisfying the condition that every vertex labeled by 0 is adjacent to at least one vertex labeled by 2. The weight of a Roman Dominating Function is the sum of all the labels, and the minimum weight is called the Roman Domination Number. The Roman Domination Problem is to find such number and function

## Variants

- [[Double Roman Domination\|Double Roman Domination]]
- [[Signed Roman Domination\|Signed Roman Domination]]
- [[Signed Roman Domination\|Signed Total Roman Domination]]

## Resources

- https://www.sciencedirect.com/science/article/pii/S0012365X03004473
- https://math.uchicago.edu/~may/REU2015/REUPapers/Xu,Linfeng.pdf
- Original Problem - [Defendens Imperium Romanum: A Classical Problem in Military Strategy on JSTOR](https://www.jstor.org/stable/2589113)
- [Upper bounds on Roman domination numbers of graphs - ScienceDirect](https://www.sciencedirect.com/science/article/pii/S0012365X11005899)
- [080733085 (siam.org)](https://epubs.siam.org/doi/pdf/10.1137/080733085)
- [On the k-Strong Roman Domination Problem - ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S0166218X20302675)
- ***Ivanović***
	- [IMPROVED MIXED INTEGER LINEAR PROGRAMING FORMULATIONS FOR ROMAN DOMINATION PROBLEM](http://elib.mi.sanu.ac.rs/files/journals/publ/119/publn119p51-58.pdf)
	- [VARIABLE NEIGHBORHOOD SEARCH APPROACH FOR SOLVING ROMAN AND WEAK ROMAN DOMINATION PROBLEMS ON GRAPHS](https://www.researchgate.net/profile/Marija-Ivanovic-6/publication/332739420_Variable_Neighborhood_Search_Approach_for_Solving_Roman_and_Weak_Roman_Domination_Problems_on_Graphs/links/5cc765494585156cd7bbaed6/Variable-Neighborhood-Search-Approach-for-Solving-Roman-and-Weak-Roman-Domination-Problems-on-Graphs.pdf) ***(Ivanović and Urošević)***
		- VNS
- [A novel approach to partial coverage in wireless sensor networks via the Roman dominating set](https://ietresearch.onlinelibrary.wiley.com/doi/full/10.1049/ntw2.12034)
- [Solving the signed Roman domination and signed total Roman domination problems with exact and heuristic methods](https://arxiv.org/pdf/2201.00394) - ***[[Signed Roman Domination\|SRD]], [[Signed Roman Domination\|STRD]]***

### PhD Thesis

### Curro Et Al 2014
- [CurroThesis.pdf (unict.it)](https://www.iris.unict.it/retrieve/67e47719-c53c-4d47-9f82-a0808aeffd8f/CurroThesis.pdf)
	- [[Genetic Algorithm\|Genetic Algorithm]]s

### Nolassi et al 2013

- [NolassiThesis.pdf](http://archivia.unict.it/bitstream/10761/1560/1/NLSSVT80M16C351B-NolassiThesis.pdf)

 Topic: The Roman Domination Problem on Grid Graphs.

#### Datasets

[[grid graphs\|grid]], [[Gilbert random graphs\|random]], [[bipartite graphs\|bipartite]], net, [[planar graphs\|planer]], and recursive

 -  [[Gilbert random graphs\|Gilbert random graphs]]
 -  [[Barabási-Albert random graphs\|Barabási-Albert random graphs]]
 -  [[bipartite graphs\|bipartite graphs]]
 -  [[planar graphs\|planar graphs]]
 -  [[grid graphs\|grid graphs]]


## [[Meta Heuristics\|Meta Heuristics]] Solutions

### greihuber et. al. 23
 
<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/rdp-greihuber-et-al-23/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">





- [greilhuber-schober-iurlano-raidl-23.pdf (tuwien.ac.at)](https://www.ac.tuwien.ac.at/files/pub/greilhuber-schober-iurlano-raidl-23.pdf) -  (See experimental eval (6))
	- [Connected Papers](https://www.connectedpapers.com/main/9884d5726f0364545db85944fada435995fc798d/A-Simulated-Annealing-Based-Approach-for-the-Roman-Domination-Problem/graph)
	- [people:raidl/](https://www.ac.tuwien.ac.at/people/raidl/)




</div></div>



## Domination Number

- Roman domination number of the Cartesian products of paths and cycles

## Github Repos

- [roman-domination/qtrd_v2.py at master · Itasuka/roman-domination (github.com)](https://github.com/Itasuka/roman-domination/blob/master/qtrd_v2.py)
- [Louisliuzy/k-Strong_Roman_Domination (github.com)](https://github.com/Louisliuzy/k-Strong_Roman_Domination)
- [XDnl/CUDARomanGraph: Roman domination graphs implementation in CUDA (github.com)](https://github.com/XDnl/CUDARomanGraph) - Most probably [[Roman Domination#Nolassi et al 2013\|#Nolassi et al 2013]]
- [gurjaranchal/Roman-Domination-Problem-Using-PSO (github.com)](https://github.com/gurjaranchal/Roman-Domination-Problem-Using-PSO)

