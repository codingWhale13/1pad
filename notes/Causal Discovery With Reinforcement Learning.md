#causality #RL

![[Pasted image 20250714105600.png]]
- motivation
	- there are different approaches to causal discovery
	- can RL help search for an appropriate DAG?
- introduced method (unnamed): use RL to search for causal graph
	- one scalar variable per node
	- uses transformer encoder and single-layer decoder
	- reward combines two components
		- BIC score: residual sum of squares + number of edges
		- acyclicity constraints
- limitations
	- restrictively slow for graphs with 50+ nodes

🗓️ 2020

✍️
- [[Shengyu Zhu]]
- [[Ignavier Ng]]
- [[Zhitang Chen]]
