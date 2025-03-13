#RL #MTRL #DL  #API #AVI #Gaussian-complexity #regression #FQI #DQN #DDPG

![[Pasted image 20250313112710.png]]
- preliminaries
	- $B(\mathcal X)$: space of bounded measurable functions w.r.t. the $\sigma$-algebra $\sigma_\mathcal X$
		- or simply $\mathcal X$
		- this is used to denote the input space
	- $B(\mathcal X,L)$: $B(\mathcal X)$ bounded by $L<\infty$
	- set of MDPs for MTRL
	- optimal Bellman operator
	- representation complexity
		- $\bar{\mathbf X}\in\mathcal X^{Tn}$: set of $n$ input samples for each task $t\in\{1,\dots T\}$
		- $\mathcal H$: class of $k\in\{1,\dots,K\}$ functions
		- $\mathcal H(\bar{\mathcal X})=\{(h_k(X_{ti})):h\in\mathcal H\}\subseteq \mathbb R^{KTn}$: random set
		- $\gamma_{tki}$: independent standard normal variables
		- $G(\mathcal H(\bar{\mathbf X}))=\mathbb E[\sup_{h\in\mathcal H}\sum_{tki}\gamma_{tki}h_k(X_{ti})\vert X_{ti}]$: Gaussian complexity (a variant of Rademacher complexity)
	- a quantity from Maurer (2016)
		- $\gamma$: vector of $m$ random standard normal variables
		- $Y\subseteq \mathbb R^n$
		- $\mathcal F$: function class with $f\in\mathcal F:Y\to\mathbb R^m$
		- $O(\mathcal F)=\sup_{y,y'\in Y,y\neq y'}\mathbb E[\sup_{f\in F}\frac{\langle y,f(y)-f(y')\rangle}{\lVert y-y'\rVert}]$
	- $L(\mathcal F)$: upper bound of the Lipschitz constant of all functions $f\in\mathcal F$
-  assumptions
	- all functions in the hypothesis classes are Lipschitz continuous
	- loss function $\ell:\mathbb R\times \mathbb R\to[0,1]$ is 1-Lipschitz in the first argument for every value of the second argument
		- 1-Lipschitz is the special case $K=1$ of the constraint $\vert f(x)-f(y)\vert\leq K\vert x - y\vert$
		- this assumption is just used for convenience and can be easily lifted
	- stationary sampling distribution
- formulation of multi-task representation learning
	- $\mathbf\mu=(\mu_1,\dots,\mu_T)$: set of $T$ tasks, modeled as probability measures of the space of possible input-output pairs $(x, y)$, where $x\in\mathcal X$ and $y\in\mathbb R$
	- we split up the journey from input to output like so:
		- $w\in\mathcal W:\mathcal X\to\mathbb R^J$
		- $h\in\mathcal H:\mathbb R^J\to\mathbb R^K$
		- $f\in\mathcal F:\mathbb R^K\to\mathbb R$
		- see image above for a visualization
	- regression problem then is
		- $\min\{\frac 1{nT}\sum_{t=1}^T\sum_{i=1}^N l(f_t(h(w_t(x_{ti}))),Y_{ti}):\mathbf f\in \mathcal F^T,h\in\mathcal H,\mathbf w\in\mathcal W^T\}$
			- $\mathbf f=(f_1,\dots,f_T)$
			- $\mathbf w=(w_1,\dots,w_T)$
			- minimizers are $\hat{\mathbf w}, \hat{h}, \hat{\mathbf f}$
	- expected loss over tasks is the task-averaged risk
		- $\varepsilon_{\text{avg}}(\mathbf w,h,\mathbf f)=\frac 1 T \sum_{t=1}^T\mathbb E[\ell(f_t(h(w_t(X))),Y)]$
		- $\varepsilon_\text{avg}^*$: minimum task-averaged risk, with minimizers $\mathbf w^*,h^*,\mathbf f^*$
- theorems (a lot of math -> omitted here)
	- goal:  extending finite-time bounds of AVI (Approximate Value-Iteration)
	- theorem 2: extends AVI bound from Farahmand (2011) to multi-task
		- task-averaged approximation error
		- => small approximation error is critical to improve convergence toward optimal action-value function
	- theorem 3: multi-task approximation error bound
		- bounds the $\epsilon_{\text{avg}}$ constructed in theorem 2
		- =>cost of learning the shared representation of each AVI iteration is mitigated by using multiple tasks
		- => cost of learning meta-state spaces $\mathbf w$ and task-specific $\mathbf f$ mappings is the same: $\mathcal O(\frac 1 {\sqrt n})$
		- => cost of learning core $h$ : $\mathcal O(\frac 1 {\sqrt{nT}})$, vanishing in the multi-task limit $T\to\infty$
		- => cost of learning shared rep decreases with a factor of $\mathcal O(\frac 1{\sqrt T})$, compared to single-task learning
- empirical results
	- introduction of multi-task extensions of FQI, DQN, and DDPG
	- multi-task version outperforms single-task versions in terms of performance and sample-efficiency
- limitations
	- generally, contributions in MTRL assume that properties of different tasks, e.g. dynamics and reward function, are generated from a common generative mode

🗓️ 2020

✍️
- [[Carlo D'Eramo]]
- [[Davide Tateo]]
- [[Andrea Bonarini]]
- [[Marcello Restelli]]
- [[Jan Peters]]
