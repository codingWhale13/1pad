#DreamerV3 #PPO #RL #actor-critic #symlog #two-hot-encoding #EMA #percentile-scaling #unimix-categoricals #DMC-suite #atari-2600

- motivation
	- DreamerV3 is a SOTA model-based RL method that introduces many "tricks"
	- can these also be used to improve PPO?
		- this work disentangles the "tricks" from other changes, e.g. scaled architecture
	- surprising answer
		- no! PPO+DreamerV3 tricks performs similar to simply PPO + reward clipping
		- interestingly, the tricks don't seem to be generally useful, at least not "out of the box"
- background
	- PPO loss: $L(\theta)=\mathbb E_t[\min(r_t(\theta)\hat A_t,\text{clip}(r_t(\theta),1-\epsilon,1+\epsilon)\hat A_t)]$
		- $r_t(\theta)=\frac{\pi_\theta (a_t\mid s_t)}{\pi_{\theta_\text{old}}(a_t\mid s_t)}$
		- $\hat A_t$ is the estimated advantage function
		- $\epsilon$  is a hyperparameter controlling the size of the trust region
- the following "tricks" from DreamerV3 can also be used in model-free actor-critic
	- symlog predictions: transformation applied to the targets of a neural network, helping to smooth predictions of different magnitudes
	- two-hot encoding: discrete regression objective representing continuous values as a weighting of two adjacent buckets
	- critic EMA regularizer: Regularizes the critic outputs towards its own weight EMA to improve stability during training
	- percentile scaling: scales returns by an exponentially decaying average of the range between their 5th and 95th batch percentile to improve robustness to outliers and varying reward scales
	- unimix categoricals: combines 99% actor network outputs with 1% uniform random sampling to inject entropy into action selection
- experiments
	- base algo: PPO from CleanRL, used in many benchmarks
	- rigorously tested different settings to explore which features have most impact
		- all-tricks
		- add-one
		- drop-one
	- take-aways
		- symlog and twohot encoding are effective as return normalization tools but underperform when returns are already normalized to reasonable ranges

🗓️ 2023

✍️
- [[Ryan Sullivan]]
- [[Akarsh Kumar]]
- [[Shengyi Huang]]
- [[John P. Dickerson]]
- [[Joseph Suarez]]
