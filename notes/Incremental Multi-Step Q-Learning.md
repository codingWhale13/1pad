#RL #Q-learning #Q-lambda-learning #DP #actor-critic  #TD-lambda

- motivation
	- there are two useful dynamic programming techniques
		- Q-learning
		- TD($\lambda$) return estimation, typically used in actor-critic setting
	- let's combine them
- backound
	- TD($\lambda$)-returns
		- class of methods for estimating $V^\pi$
		- uses corrected n-step truncated returns: $r_t^{(n)}=r_t+\gamma r_{t+1}+\dots+\gamma^{n-1}r_{t+n-1}+\gamma^n \hat V_{t+n}^\pi(x_{t+n})$
			- $\hat V_t^\pi$: estimate of $V^\pi$ at time step $t$
			- has "error-reduction property", meaning $\mathbb E[r_t^{(n)}]$ is closer to $V^\pi$ than $\hat V^\pi$ is
		- TD($\lambda$) is defined by Sutton as
			- $r_t^\lambda=(1-\lambda)[r_t^{(1)}+\gamma r_t^{(2)}+\gamma^2r_t^{(3)}+\dots]$
			- or recursively: $r_t^\lambda=r_t+\gamma(1-\lambda)\hat V_t^\pi (x_{t+1})+\gamma\lambda r_{t+1}^\lambda$
	- 1-step Q-learning
		- $Q^*(x,a)=R(x,a)+\gamma\sum_{y} P_{xy}(a)V^*(y)$
			- $R(x,a)=\mathbb E[r_0\mid x_0=x,a_0=0]$
			- $P_{xy}(a)$ is probability of reaching $y$ when taking $a$ in $x$
		- let's estimate $Q^*$ with $\hat Q^*$
		- TD error: $r+\gamma \hat V^*(y)-\hat Q^*(x,y)$
		- update using TD(0): $\hat Q^*(x,a)=(1-\alpha)\hat Q^*(x,a)+\alpha r^0$
			- note
				- $\hat Q^*$ implicitly defines greedy policy, always taking $\arg\max$ action
				- i.e. we don't specify what actions the agents should take
				- -> Q-learning is not "experimentation-sensitive"
- introduced method: *Q($\lambda$)-learning*
	- TD($\lambda$)-returns + 1-step Q-learning = Q($\lambda$)-learning
		- where TD($\lambda$)-returns use maximum Q-value at each state visited
	- $r_t^\lambda-\hat Q_t (x_t,a_t)=e'_t+\gamma\lambda e_{t+1}+\gamma^2\lambda^2e_{t+2}+\dots+\sum_{n=1}^\infty (\gamma\lambda)^n[\hat V_{t+n}(x_{t+n})-\hat V_{t+n-1}(x_{t+n})]$
		- $e_t=r_t+\gamma\hat V_t(x_{t+1})-\hat V_t(x_t)$
		- $e'_t=r_t+\gamma\hat V_t(x_{t+1})-\hat Q_t(x_t,a_t)$

🗓️ 1996

✍️
- [[Jing Peng]]
- [[Ronald J. Williams]]
