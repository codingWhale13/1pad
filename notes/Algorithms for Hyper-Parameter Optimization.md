#hyperparameter-optimization #DBN #SMBO #EI #GP #TPE

- motivation
	- large neural nets, such as Deep Belief Networks (DBNs) can have dozens of hyperparameters -> algorithmically finding them becomes more desirable
- scope
	- in general, a hyperparameter can affect values and relevance of other hyperparameters ->  graph-structured configuration space
	- this paper considers only tree-structured configuration space
- background
	- SMBO (Sequential Model-Based Global Optimization)
		- active-learning-type algorithm
		- repeatedly queries $f$ (model to be optimized) at the most promising $x^*$, according to surrogate model and then updates the surrogate model
	- expected improvement criterion: $\text{EI}_{y^*}(x)=\int_{-\infty}^{\infty}\max (y^*-y,0)p_M(y\vert x)dy$
		- $M$ is model of $f:\mathcal X\to\mathbb R^N$
	- GP (Gaussian Process) is useful in model-based optimization literature, both for finding candidate $x^*$ and fitting a model $M_t$
		- GP runtime is cubic, but usually function evaluation $f(x^*)$ dominates so it's okay
- contributions
	- random search is competitive with manual optimization of DBNs
	- random search is insufficient for training DBNs
		- -> proposed automatic sequential optimizations (see below) are better
	- proposed sequential optimization 1: hierarchical GP estimator
		- why hierarchical? because some HPs are not in use, conditional on others
	- proposed sequential optimization 2: TPE (tree-structured Parzen estimator)

🗓️ 2011

✍️
- [[James Bergstra]]
- [[Rémi Bardenet]]
- [[Yoshua Bengio]]
- [[Balázs Kégl]]
