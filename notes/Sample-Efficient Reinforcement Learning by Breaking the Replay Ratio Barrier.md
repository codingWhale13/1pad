#RL #SPR #SR-SPR #SAC #SR-SAC

![[Pasted image 20250301162134.png]]
- motivation
	- tendency of neural nets to lose their ability to learn and generalize from new information during training (a lot of references mentioned, confirming this finding) -> most RL methods don't have countermeasures -> main roadblock in achieving better sample efficiency through replay ratio scaling
- background
	- replay ratio: number of agent updates per env step
	- replay ratio scaling: change in an agent's performance caused by doing more updates for a fixed umber of env steps
	- replay ratio scaling is intertwined with online RL paradigm: making better use of data -> different behavior in next rollout -> different data distribution next time (this can be good or bad, the point is, the two things have a close relationship)
- introduced method: *SR* (Scaled-by-Resetting) modification
	- -> SR-SAC: Scaled-by-Resetting SAC
	- -> SR-SPR: Scaled-by-Resetting SPR
		- unlike original SPR, separate target EMA network is used for targets and action selection
	- core idea: scaling the replay ratio to get more out of the data collected during env interaction
	- reset strategy: variant of *Shrink and Perturb*
		- $\theta^t=\alpha\theta^{t-1}+(1-\alpha)\phi$ where $phi\sim\text{initializer}$
			- authors use $\alpha=0.8$
- tandem setting
	- higher replay ratio -> more similar to offline RL
	- to take this to the extreme, the authors experiment with a tandem setting
		- active agent: SR-SPR, running $\text{replay ratio}$ updates per env step
		- passive agent: same architecture and algorithm as active agent, but never interacts with the env directly
		- results: passive agent performs learns in a similar way, but unperforms compared to active agent
	- => interacting with the env (at least from time to time) provides an implicit regularization, improving performance

🗓️ 2023

✍️
- [[Pierluca D'Oro]]
- [[Max Schwarzer]]
- [[Evgenii Nikishin]]
- [[Pierre-Luc Bacon]]
- [[Marc G. Bellemare]]
- [[Aaron Courville]]
