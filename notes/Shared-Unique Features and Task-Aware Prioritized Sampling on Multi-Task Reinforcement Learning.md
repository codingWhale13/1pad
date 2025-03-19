#MTRL #STARS #triplet-loss #PER

![[Pasted image 20250319234105.png]]
- motivation
	- current MTRL methods suffer from performance imbalance -> very poor performance on a few tasks
- introduced methods: *STARS* (Share-unique features and task-aware Prioritized Sampling)
	- STARS = SAC + 2 new components
	- component 1: shared-unique feature extractor
		- task-focused shared features learn knowledge between different tasks, using shared set of knowledge parameters
		- task-unique features give attention to specific tasks, using triplet loss $L_\text{tri}=\frac 1 M\sum_{i=1}^M \max(0,m+d(f^u_{i,a},f^u_{i,p})-d(f^u_{i,a},f^u_{i,n}))$
			- $M$: number of sampled pairs
			- $f^u_a$: anchor
			- $f^u_p$: positive sample from same task
			- $f^u_n$: negative sample from different task
			- $d(\cdot,\cdot)$: Euclidian distance
	- component 2: task-aware sampling strategy with prioritize experience replay
		- multi-task prioritized experience replay buffer stores transitions from all tasks
		- sampling is done w.r.t. two things:
			- transition's priority(larger TD error -> higher priority)
			- task probability (each task has its own prioritized experience replay)

🗓️ 2024

✍️
- [[Po-Shao Lin]]
- [[Jia-Fong Yeh]]
- [[Yi-Ting Chen]]
- [[Winston H.Hsu]]
