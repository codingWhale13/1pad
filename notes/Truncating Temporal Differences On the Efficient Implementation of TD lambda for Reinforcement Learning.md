#RL #TD-lambda #TD #TTD #Q-learning #online-RL

![[Pasted image 20250403235434.png]]
- motivation
	- in 1995, most TD-based RL used TD(0), only taking immediate reward into account
	- while TD($\lambda$) is promising to be more sample-efficient in many scenarios, it is more expensive to implement
	- this paper implements TD($\lambda$) with similar efficiency as TD(0)
- background: temporal difference (TD)
	- TD allows improving a policy without waiting for the final outcome
		- in contrast to Monte Carlo, where we have to wait until episode termination
	- core idea: difference between successive predictions is used as the training error
	- TD($\lambda$) is a class of methods, where $\lambda\in[0,1]$ called recency factor
		- TD(0) means: we just care about the 1-step corrected return (see below), i.e. the sum of immediate reward and discounted predicted utility for next state
		- TD(1) means: we consider exactly the discounted sum of all rewards (=return)
		- remember: $\lambda\neq\gamma$, we're not talking about the discount factor here!
		- => $\lambda$ is the recency factor
	- so, how does it work?
		- TD return for time $t$ is defined as $z_t=\sum_0^\infty \gamma^k r_{t+k}$
			- let $U(x_t)$ be the prediction of $z_t$
			- -> perfect predictions give $U(x_t)=z_t=r_t+\gamma z_{t+1}+\gamma U(x_{t+1})$
		- TD error is $r_t+\gamma U(x_{t+1})-U(x_t)$
		- TD($\lambda$) equation: $\Delta_x(t)=(r_t+\gamma U_t (x_{t+1})-U_t (x_t))\sum_{k=0}^t (\gamma\lambda)^{t-k}\chi_x(k)$
			- where $\chi_x(t)=\begin{cases}1&\text{ if }x_t=x\\0&\text{otherwise}\end{cases}$ is an identity function
	- okay, but how do we implement this? enter: eligibility traces
		- they allow us to not keep track of $\chi_x(t)$ values for each $x$ and $t$
		- we only need to maintain the whole sums $\sum_{k=0}^{t-k}\chi_x(k)$ for all $x$ and the current $t$
		- $e_x(0)=\begin{cases}1&\text{ if }x_0=x\\0&\text{ otherwise}\end{cases}$
		- $e_x(t)=\begin{cases}\gamma\lambda e_x (t-1)+1&\text{ if }x_t=x\\\gamma\lambda e_x (t-1)&\text{ otherwise}\end{cases}$
			- -> if a state is visited, it's activity goes up and then decays exponentially
		- now we can write: $\Delta_x(t)=(r_t+\gamma U_t (x_{t+1})-U_t (x_t))e_x(t)$
- introduced method: *TTD* (Truncated Temporal Differences)
	- some math derivation, swapping $\sum_x\sum_t$ to $\sum_t\sum_x$ to make it suitable for online RL
	- consider $m$-step truncated TD return: $z_t^{[m]}=\sum_{k=0}^{m-1}\lambda^k r_{t+k}$
		- we can improve by taking the rejected terms into account (bootstrapping)
		- corrected $m$-step return $z_t^{(m)}=(\sum_{k=0}^{m-1}\lambda^k r_{t+k})+\gamma^m U_{t+m-1}(x_{t+m})$
	- finally, we have the TTD procedure, which makes such returns feasible in online RL
		- see image for the TTD($\gamma,m$) procedure
- experimental demonstration is done with AHC and Q-learning

🗓️ 1995

✍️
- [[Paweł Cichosz]]
