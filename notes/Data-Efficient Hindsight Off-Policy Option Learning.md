#RL #MLE #option-learning #HO2

![[Pasted image 20250315233611.png]]
- background: option learning
	- generalization of the concept of an action -> "option"
	- option policies introduce temporal and action abstraction (see image above)
	- an option in this work is defined as triple $(I(s_t,o_t),\pi^L(a_t\mid,s_t,o_t),\beta(s_t,o_t))$
		- initial condition $I$ describes an option's probability to start in a state and is simplified to $1\forall s_t\in S$
		- termination condition $b_t\in\beta(s_t,o_t)$ is Bernoulli, describing the option's probability to terminate in any given state
		- $\pi^L(a_t\mid s_t,o_t)$describes action distribution for a given option
- introduced method *HO2* (Hindsight Off-policy Options)
	- learns option policies in an off-policy manner
	- policy improvement algorithm is based on (weighted) maximum likelihood estimation and goes like this
		1. update critic
		2. generated intermediate, non-parametric policy based on critic
		3. update parametric policy to align with the non-parametric improvement
	- idea: learn both high-level controller and low-level options
		- -> beside the low-level policies $\pi^L$, there's also high-level probabilities $\pi^H$
		- both are simultaneously learned via a single end-to-end optimization procedure
	- can be seen as describing policies with an autoregressive, discrete latent space
- experiments break things down to these two things
	- action abstraction (via mixture policies)
	- temporal abstraction (via options)

🗓️ 2021

✍️
- [[Markus Wulfmeier]]
- [[Dushyant Rao]]
- [[Roland Hafner]]
- [[Thomas Lampe]]
- [[Abbas Abdolmaleki]]
- [[Tim Hertweck]]
- [[Michael Neunert]]
- [[Dhruva Tirumala]]
- [[Noah Siegel]]
- [[Nicolas Heess]]
- [[Martin Riedmiller]]
