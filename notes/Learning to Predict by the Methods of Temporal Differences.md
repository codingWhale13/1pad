#RL #TD #TD-lambda #supervised-learning

![[Pasted image 20250404231003.png]]
- motivation
	- the credit-assignment problem has been traditionally solved by comparing predicted and actual outcomes
	- but there's a more memory-efficient and accurate way: using temporal differences
	- while other works have used temporal difference learning in a goal oriented way (most famously in checkers), they have not been studied independently, and in the more general case of predicting arbitrary events
- relation to supervised-learning procedures
	- interestingly, the author doesn't make a clear cut between RL and supervised learning; instead, it's all about "learning-to-predict" problems
	- any prediction problem can be cast to supervised learning
		- first item is the data based on which a prediction must be made
		- second item is the actual outcome, what the prediction should have been
		- example: predicting Sunday's weather on Monday, Tuesday, ... can be broken down into the following, ignoring sequential structure
			- predicting Sunday's weather, based on Monday's weather
			- predicting Sunday's weather, based on Tuesday's weather
			- etc.
	- whereas single-step prediction problems need to be addressed by supervised learning, this work considers multi-step prediction problems
		- the weather example above is such a problem: the true correctness is only revealed on Sunday, but partial information is already released earlier than that
	- hot-take: real-world problems are predominantly multi-step, and are just cast as single-step prediction problems for algorithmic convenience
	- crucial fact: TD methods try to take advantages of the information provided by the temporal sequence of states, whereas supervised-learning methods ignore it
		- compare this with the image above: the sequence shown with dashed arrows (novel -> bad -> win) would lead a supervised-learning system to assume the novel state is fantastic, having led to a win 1 out of 1 times - TD captures the more subtle truth by updating it based on the bad intermediate step
- introduced class of algorithms: *TD* (Temporal Differences)
	- consider observation-outcome sequence $x_1,x_2,\dots,x_m,z$
		- weights $w$ are updated once for the entire sequence for now
		- $\Delta w_t$ is the parameter change we want to perform
		- $P_t$ is the prediction of $x_t$, and can be computed by a MLP
		- TD enables the following
			- going from $\Delta w_t=\alpha(z-P_t)\nabla_w P_t$
			- to $\Delta w_t=\alpha (P_{t+1}-P_t)\sum_{k=1}^t\nabla_wP_k$
				- can be computed incrementally, saving memory
	- more generally, we can describe the TD($\lambda$) family of learning procedures, using
		- $\Delta w_t=\alpha (P_{t+1}-P_t)\sum_{k=1}^t\gamma^{t-k}\nabla_wP_k$
			- using $\lambda=1$, we get the above TD(1) instantiation
			- exponential weighting allows for incremental computation
- proof of convergence
	- linear TD(0) converges for terminating data sequences
		- see paper for proof
		- the episodic nature is important to the proof, so as to get grounded in reality after some finite amount of steps; interestingly though, Samuel's 1959 checker's program did not use a terminal constraint and still performed well
- note on different notions of optimality
	- "many kinds of optimality, and choosing among them is often a critical decision"
	- if the a priori distribution of possible Markov processes is known, we can can optimize the MSE by using Bayes' rule
		- BUT we usually don't have a priori assumptions about Markov processes
	- enter: maximum-likelihood estimate <- this is what we care about
		- gives most likely estimate, given observations
	- example: we flip a coin and it gives tails 7/10 times
		- best estimate of the next outcome can't be uniquely determined, because we don't have the a priori information about how likely it is that our coin is fair
		- ML estimate meanwhile: 7/10

🗓️ 1988

✍️
- [[Richard S. Sutton]]
