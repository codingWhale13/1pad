#RL #ADP #tetris #CPI #VI #PI

- motivation
	- prior work attempted to solve Tetris by using value-based algorithms
		- i.e. first defining a value function representation and then searching in that value function space, which finally leads to the policy
	- searching directly in the space of policies has yielded much better scores
		- e.g. cross-entropy or genetic algorithms
		- CE method cleared 35M lines, rather than only a few thousand
	- to get good at tetris, we should search in policy space
	- => authors try out the Classification-based Policy Iteration (CPI), which is an ADP (approximate dynamic programming) method that fits this goal
- input and output specs
	- state space: current board config and piece to place
	- action space: location and orientation for one piece, max 32 possibilities
- overview of methods
	- MPI (Modified Policy Iteration)
		- let $m\geq 1$ be an integer -> $m$-step Bellman operator
		- let $T_{\pi_k}$ be the Bellman operator of policy $\pi_k$
		- evaluation step $v_k=(T_{\pi_k})^m v_{k-1}$
		- greedy step: $\pi_{k+1}=\mathcal G_{v_k}[(T_{\pi_k})^m v_{k-1}]$
			- $G_{v_k}$ acts greedily w.r.t. $v_k$
		- MPI is a generalization of VI ($m=1$) and PI ($m=\infty$)
	- CMPI (Classification-based Modified Policy Iteration)
		- approximation of MPI
		- set up regression problem
			- use $m$-step rollout to get estimate $\widehat v_k(s^{(i)})=\sum_{t=0}^{m-1}\gamma^tr_t^{(i)}+\gamma^m v_{k-1}(s_m^{(i)})$
			- regression loss: $\widehat L_k^{\mathcal F}(\widehat\mu;v)=\frac 1 N\sum_{i=1}^N(\widehat v_k(s^{(i)})-v(s^{(i)}))^2$
			- solution minimizing this loss is $v_k$, our best guess for the true function
			- the authors use a linear function approximator $\widehat v_k(s^{(i)})=\phi (s^{(i)})w$
		- classification problem
			- classification loss: $\widehat L_k^{\Pi}(\widehat \mu;\pi)=\frac{1}{N'}\sum_{i=1}^{N'}[\max_{a\in\mathcal A}\widehat Q_k (s^{(i)},a)-\widehat Q_k(s^{(i)},\pi(s^{(i)}))]$
		- let $M$ be number of rollouts
		- begins with arbitrary $\pi_1\in\Pi$ and $v_0\in\mathcal F$
			- $\Pi$ and $\mathcal F$ are defined by choice of regressor and classifier
		- estimate $\widehat Q_k(s^{(i)},a)=\frac 1 M\sum_{j=1}^M R_k^j(s^{(i)},a)$ of true action-value function
			- uses rollout estimate $R_k^j(s^{(i)},a)=\sum_{t=0}^m \gamma^t r_t^{(i,j)}+\gamma^{m+1} v_{k-1} (s_{m+1}^{(i, j)})$
	- DPI (Direct Policy Iteration)
		- same algo as CMPI, but without a regressor
		- -> we must use $m$-truncated rollouts $R_k^j(s^{(i)},a)=\sum_{t=0}^m \gamma^t r_t^{(i,j)}$ to compute the estimates $\widehat Q_k (s^{(i)},a)$ since $v_k$ is not available anymore
- my comments
	- the authors call equation (1) an unbiased estimate; it is only unbiased because $\gamma=1$
	- also in equation (4), they say unbiased, but I disagree - it would only be unbiased if $m=\infty$ i.e. in practice, we use the full MC rollouts

🗓️ 2013

✍️
- [[Victor Gabillon]]
- [[Mohammad Ghavamzadeh]]
- [[Bruno Scherrer]]
