#RL #interpretability #decision-tree

- motivation
	- we want interpretability in RL, but we also want good performance - what is the price of interpretability?
- background
	- (k, d)-maze is a MDP defined by k obstacles in d-dimensional integer space
		- number of states: $\infty$ ($\mathbb Z^d$), one of them being the goal state
		- number of actions: $2d$ (can go -1 or +1 in every dimension)
- method
	- instead of using standard methods like policy iteration (which are not interpretable), the authors describe a simple and efficient algorithm for finding a decision tree solution, because a decision tree is the "gold standard" for interpretable models
		- input (root): state
		- output (leaf): action
		- authors focus on linear function at each inner node
	- run-time is O(log k + 2^d)
		- at first I thought, "for (k, d), this is O(log k)" covers up the scalability issue of large mazes
		- but then I realized: d is the dimensionality, not the height/width of a 2d maze - so yes, for say 50-dimensional mazes, this is intractable but in the real world, 2d or 3d often suffices

🗓️ 2022

✍️
- [[Yishay Mansour]]
- [[Michael Moshkovitz]]
- [[Cynthia Rudin]]
