---
{"dg-publish":true,"permalink":"/cloud/dynamic-capacity-provisioning/follow-the-workload/"}
---


#cse6603 

## Related Paper
[Online Dynamic Capacity Provisioning in Data Centers](http://rsrg.cms.caltech.edu/greenIT/papers/dcp-allerton.pdf)

- How many servers to be kept active
- How much workload to be **delayed** for energy saving while meeting every deadline.
- We present an offline LP formulation for capacity provisioning by dynamic deferral and give two online algorithms to:
	- determine the capacity of the data center
	- the assignment of workload to servers dynamically.

### **Cited by**

- [Dynamic Deferral of Workload for Capacity Provisioning in Data Centers - Adnan](https://arxiv.org/pdf/1109.3839.pdf)
- [A 2-Competitive Algorithm For Online Convex
Optimization With Switching Costs](https://drops.dagstuhl.de/opus/volltexte/2015/5297/pdf/7.pdf)
        - [Cloud Computing Operations Research](https://www.labri.fr/perso/eyraud/pmwiki/uploads/Main/CloudOR.pdf)
        - [Characterizing the Impact of the Workload on the Value of Dynamic Resizing in Data Centers✩](https://arxiv.org/pdf/1207.6295.pdf)
- Lazy capacity provisioning (LCP)
    - Dynamically turns on/off servers in a data center to minimize energy cost and delay cost for scheduling workload
    - Aims at minimizing the average delay (penalizing delay)
    - 3-competitive solution
    - No bounds on maximum delay.

##### Variation [[Cloud/Dynamic Capacity Provisioning/Valley Filling Workload|Valley Filling Workload]]
