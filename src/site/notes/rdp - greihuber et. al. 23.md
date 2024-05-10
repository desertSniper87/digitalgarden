---
{"dg-publish":true,"permalink":"/rdp-greihuber-et-al-23/"}
---


- [greilhuber-schober-iurlano-raidl-23.pdf (tuwien.ac.at)](https://www.ac.tuwien.ac.at/files/pub/greilhuber-schober-iurlano-raidl-23.pdf) -  (See experimental eval (6))
	- [Connected Papers](https://www.connectedpapers.com/main/9884d5726f0364545db85944fada435995fc798d/A-Simulated-Annealing-Based-Approach-for-the-Roman-Domination-Problem/graph)
	- [people:raidl/](https://www.ac.tuwien.ac.at/people/raidl/)



## Algorithm Explanation
#claude 
The pseudocode takes a graph `G = (V, E)` as input, where `V` is the set of vertices, and `E` is the set of edges.

First, it initializes two variables `du(v)` and `d2u(v)` for each vertex `v` in the graph. `du(v)` represents the number of undominated neighbors of vertex `v`, and `d2u(v)` represents the number of vertices at distance exactly 2 from vertex `v`. These variables will be used as heuristics to guide the selection of vertices.

The code then initializes an array `f` of the same size as `V`, where `f(v)` represents the status of vertex `v`. Initially, all vertices are marked as "unlabeled" (`f(v) = unlabeled`).

The algorithm then enters a loop that iterates until there is no vertex in `S` (initially set to `V`) with two or more undominated neighbors (`du(v) >= 2`). In each iteration, it selects the vertex `v` from `S` with the largest `du` value. If the tiebreaker option is enabled, it prefers vertices with lower `d2u` values in case of ties.

For the selected vertex `v`, it sets `f(v)` to 2 (representing a dominating vertex) and marks all its unlabeled neighbors as dominated by setting `f(n)` to 0 for all `n` in `N(v)`, the set of neighbors of `v`.

After the loop terminates, all remaining unlabeled vertices are labeled with 1 (representing dominated vertices).

The code then performs a post-processing step, which is a local improvement step. It iterates over all vertices `v` with `f(v) = 2` (dominating vertices). For each such vertex `v`, it temporarily sets `f(v)` to 0 (non-dominating) and checks if the Roman Domination condition is violated for any neighbor `u` of `v`. If the condition is violated for any neighbor, it reverts `f(v)` back to 2 (dominating). If the condition is not violated for any neighbor but is violated for `v` itself, it sets `f(v)` to 1 (dominated).

Finally, the algorithm returns the updated `f` array, which represents the Roman Dominating Function (RDF) for the input graph.

The pseudocode uses a greedy approach to select dominating vertices based on the `du` and `d2u` heuristics, followed by a local improvement step to refine the solution. However, it's important to note that this is not the typical simulated annealing algorithm, as it does not incorporate the core aspects of simulated annealing, such as a cooling schedule, acceptance probability, and stochastic perturbations.
