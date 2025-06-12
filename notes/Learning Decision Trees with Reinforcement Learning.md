#RL #decision-tree #RNN #REINFORCE

![[Pasted image 20250612125510.png]]
- motivation
	- decision trees are useful due to their intepretability
	- but finding an optimal decision tree is NP-complete
	- greedy search is common and yields okay results, but is generally sub-optimal due to local-only decisions
	- can RL help?
- introduced method: *RLBDT* (Reinforcement Learning Based Decision Tree)
	- idea: use sequential output of an RNN to predict the choice for a learning task; this has been applied in neural architecture search, neural optimizer search, combinatorial optimization, and device placement
	- learning a decision tree in 2 steps:
		1. choose splitting feature <- done with RNN
		2. choose splitting value <- choose greedily the value that maximizes the information gain
	- RL algo: REINFORCE
	- assumptions
		- decision tree is a complete binary tree with depth $k$ -> number of non-leaf noes is $2^k-1$
		- nodes are indexed uniquely
- results
	- RLBDT outperforms CART baseline in all datasets

🗓️ 2017

✍️
- [[Zheng Xiong]]
- [[Wenpeng Zhang]]
- [[Wenwu Zhu]]
