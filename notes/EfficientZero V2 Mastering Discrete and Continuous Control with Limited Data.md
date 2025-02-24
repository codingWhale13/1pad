#RL  #MBRL #EfficientZeroV2 #TDMPC2 #DreamerV3 #Gumbel-search

- introduced method: *EfficientZero V2* (or *EZ-V2*)
	- general framework for sample-efficient RL algorithms
		- continuous and discrete actions
		- visual and low-dimensional inputs
	- claims new SOTA, beating DreamerV3 in 50/66 tasks
	- in some aspects, EZ-V2 is similar to original EZ version
		- learns a predictive model in latent space
		- performs planning over actions using this model
		- uses self-supervised consistency loss
	- new features
		- sampled-based tree search for action planning -> policy improvements in continuous space
			- instead of MCTS (used in original EfficientZero), which is unable to handle high-dimensional action spaces, especially in continuous control, EZ-V2 uses Gumbel search
		- search-based value estimation strategy -> make better use of data
			- when expanding the search tree, imagined trajectories are generated that provide bootstrapped samples
			- the mean of these empirical estimations is now used as target

🗓️ 2024

✍️
- [[Shengjie Wang]]
- [[Shaohuai Liu]]
- [[Weirui Ye]]
- [[Jiacheng You]]
- [[Yang Gao]]
