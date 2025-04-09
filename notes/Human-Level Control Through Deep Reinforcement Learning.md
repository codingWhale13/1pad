#DL #RL #atari-2600 #Q-learning #DQN #CNN #experience-replay #fitted-Q-iteration #SGD

![[Pasted image 20250409220919.png]]
- motivation
	- create a single algorithm that can solve diverse domains, end-to-end from high-dimensional input
	- fitted Q-iteration tried the same, but has to repeat 100s of iterations -> very slow
- introduced method: *DQN* (Deep Q-Network)
	- key aspect: use a neural net (a CNN, because pixel-based input) to learn $Q$ function
	- known issues with nonlinear function approximation in RL are addressed
		- correlations in the sequence of observations
			- solution: experience replay
		- small $Q$ updates may significantly change the policy -> change of data distribution
			- solution: iterative update with targets that are held fixed for some duration
	- loss function: $L_i(\theta_i)=\mathbb E_{(s,a,r,s')\sim U(D)}[r+\gamma\max_{a'}Q(s',a';\bar{\theta}_i)-Q(s,a;\theta_i)^2]$
		- $\bar{\theta_i}$ are target weights at iteration $i$
		- $U(D)$ is uniform distribution of transitions $(s,a,r,s')\sim D$ stored in replay buffer
		- => basically 1-step Q-learning
- results
	- success: first large neural net trained with SGD on an RL problem in a stable manner
	- t-SNE shows: representations learned by DQN do indeed generalize to data generated from policies other than its own

🗓️ 2015

✍️
- [[Volodymyr Mnih]]
- [[Koray Kavukcuoglu]]
- [[David Silver]]
- [[Andrei A. Rusu]]
- [[Joel Veness]]
- [[Marc G. Bellemare]]
- [[Alex Graves]]
- [[Martin Riedmiller]]
- [[Andreas K. Fidjeland]]
- [[Georg Ostrovski]]
- [[Stig Petersen]]
- [[Charles Beattie]]
- [[Amir Sadik]]
- [[Ioannis Antonoglou]]
- [[Helen King]]
- [[Dharshan Kumaran]]
- [[Daan Wierstra]]
- [[Shane Legg]]
- [[Demis Hassabis]]
