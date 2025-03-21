#RL #TD-MPC #MTRL #MBRL

- motivation
	- improve sample-efficiency by learning generalist world models
	- scaling MTRL learning: make bigger network learn more tasks
- background MPC (Model Predictive Control)
	- MPC is a general framework for model-based control that optimizes action sequences such that return is maximized over the finite time horizon H
- introduced method: *TD-MPC2* (Temporal Difference Learning for Model Predictive Control v2)
	- TD-MPC2 is an improvement of TD-MPC, by the same authors
	- model-based RL algorithm, using MPC
		- MPC is not enough to solve the full RL problem (formulated as infinite horizon), so TD-MPC2 addresses this shortcoming of local trajectory optimization by bootstrapping return estimates beyond horizon H with a learned terminal value function
	- uses just an encoder, no decoder
		- intuition: there's no point in predicting the next real observation to the pixel-level; it's easier just to stay in latent space
		- this is key to modeling large datasets with modest model sizes
	- major changes that make TD-MPC2 more scalable than TD-MPC2
		- improved algorithmic robustness by revisiting core design choices
		- careful design of an architecture that can accommodate datasets with multiple embodiments and action spaces without relying on domain knowledge
	- the following components are jointly learned
		- encoder
		- latent dynamics
		- reward prediction (using cross-entropy)
		- Q-network (using cross-entropy)
			- TD-MPC2 learns ensemble of Q functions (concretely 5) to generate TD targets using an EMA of each Q function, denoted as $\bar Q$
				- targets are  then computed as the minimum of two randomly sub-sampled $\bar Q$-functions
	- additionally, there's the policy prior
		- trained with maximum entropy RL
	- task embeddings are learned
		- crucial not just to differentiate between tasks (e.g. with one-hot) but also  to learn task relations to take advantage of similarities in the tasks
		- all 5 components are conditioned on task embeddings
		- To improve training stability, we constrain the $l2$-norm of e to be $\leq 1$
	- action masking
		- TD-MPC2 learns to perform tasks with a variety of observation and action spaces, without any domain knowledge
		- to do so, we zero-pad all model inputs and outputs to their largest respective dimensions, and mask out invalid action dimensions in predictions made by the policy prior $p$ during both training and inference
		- this ensures that prediction errors in invalid dimensions do not influence TD-target estimation, and prevents p from falsely inflating its entropy for tasks with small action spaces
		- we similarly only sample actions along valid dimensions during planning
	- 5M parameter model
		- Encoder parameters: 167,936
		- Dynamics parameters: 843,264
		- Reward parameters: 631,397
		- Policy parameters: 582,668
		- Q parameters: 3,156,985
		- Task parameters: 7,680
		- Total parameters: 5,389,930
- results
	- benchmarked: 104 continuous control tasks, multiple domains
		- DMControl Suite
		- Meta-World
		- ManiSkill2
		- MyoSuite
	- good results, even with single set of hyper-parameters -> shows robustness
	- performs well on multi-task RL: learning 80 tasks with a single model (317M params)
		- note regarding MTRL Setting
			- step 1: collect experience from single-task TD-MPC2 agents
				- this is not exclusively "expert data", but entire replay buffers
			- step 2: train MTRL agent on this dataset in an offline manner
		- scales when getting more parameters (unlike TD-MPC)
	- task embedding similarity appears to align more closely with task dynamics (embodiment, objects) than objective (walk, run)
		- "this makes intuitive sense, as dynamics are tightly coupled with control"
	- [dataset](https://www.tdmpc2.com/dataset) with experience from 240 agents per environment
- my open question: Is performance for multi-task model better than the single-task models?

🗓️ 2024

✍️
- [[Nicklas Hansen]]
- [[Hao Su]]
- [[Xiaolong Wang]]
