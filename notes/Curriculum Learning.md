#curriculum-learning

![[Pasted image 20250306230840.png]]
- motivation
	- animals learn better when examples are presented in a meaningful order, introducing gradually more concepts, and gradually more complex ones
	- let's do the same with machine learning
- introduced paradigm: *curriculum learning*
	- consider random variable $z$, representing an example for the learner
	- let $P(z)$ be the target training distribution of interest
	- let $0\leq W_\lambda(z)\leq 1$ be the weight applied to example $z$ at step $\lambda$, with $0\leq\lambda\leq 1$ and $W_1(z)=1$
	- then, the training distribution at step $\lambda$ is defined as $Q_\lambda (z)\propto W_\lambda (z)P(z)$, $\forall z$, such that $\int Q_\lambda (z)dz=1$
		- it follows $Q_1(z)=P(z)$, $\forall z$
	- the sequence of distributions $Q_\lambda$ are called a curriculum if
		- the entropy of these distributions increases, i.e. $H(Q_\lambda)<H(Q_{\lambda+\epsilon})$, $\forall\epsilon>0$
		- and $W_\lambda(z)$ is monotonically increasing in $\lambda$, i.e.$W_{\lambda+\epsilon}(z)\geq W_\lambda(z)$, $\forall z,\forall\epsilon>0$
	- in my own words: the weights $W_\lambda (z)$ determine the growing interest in example $z$, potentially starting from 0, and certainly ending up at 1. This interest can never shrink, but by increasing $W_{\lambda+\epsilon}(y)$ for some $y\neq z$, we can reduce the relative interest in $z$, i.e. shifting focus. no matter how many examples and what the weights are, we always scale them such that their integral is 1
- experiments supporting the efficacy of curriculum learning
	- SVM learns to classify between two 2D Gaussians
	- shape recognition
	- language modeling
		- next word prediction on Wikipedia articles, but first ignoring all but the 5k most frequent words, then all but the 10k most frequent words etc.
		- the image above shows the eagerness to learn once the vocab size grows
- interesting distinction: difficult examples can be more informative than easy examples but they can also just be more noisy, confusing the learner
- my open question: how is "easy set of training examples" to "full set" a curriculum? the entropy is not increasing for every step, it can stay constant... maybe this is nit-picky, but I wonder why the entropy requirement above does not use a $\leq$ rather than a $<$

🗓️ 2009

✍️
- [[Yoshua Bengio]]
- [[Jérôme Louradour]]
- [[Ronan Collobert]]
- [[Jason Weston]]
