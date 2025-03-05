#RL #regression #classification #cross-entropy-loss

![[Pasted image 20250305233202.png]]
- motivation
	- value functions are a core component in deep RL but training them with MSE regression doesn't scale well
	- compare this to supervised learning: cross-entropy classification loss allows massive scaling
	- => idea: let's train value functions with categorical cross-entropy
- framing regression as classification
	- probabilistic approach: model the target as a conditional distribution $Y\mid x\sim\mathcal N(\mu=\hat y(x;\theta),\sigma^2)$ where
		- variance $\sigma^2$ is fixed
		- predictor function $\hat y:\mathbb R^d\times R^k\to\mathbb R$ is parameterized by $\theta\in\mathbb R^k$
	- instead of learning the mean of the conditional distribution directly, the authors learn a distribution over the target value
	- Q is represented as the expected value of a categorical distribution $Z\in\mathcal Z$ which in turn is parameterized by probabilities $\hat p_i(s,a;\theta)$ for each "class" $z_i$ which are derived from the softmax logits
	- for more math and critical discussion, see paper
- results
	- using HL-Gauss cross-entropy loss improves performance and scalability of value-based RL methods in the following benchmarks
		- online Atari
		- offline multi-game Atari
		- Wordle
		- robotic manipulation
		- chess without search
	- HL-Gauss cross-entropy loss outperforms two-hot cross-entropy loss

🗓️ 2024

✍️
- [[Jesse Farebrother]]
- [[Jordi Orbay]]
- [[Quan Vuong]]
- [[Adrien Ali Taïga]]
- [[Yevgen Chebotar]]
- [[Ted Xiao]]
- [[Alex Irpan]]
- [[Sergey Levine]]
- [[Pablo Samuel Castro]]
- [[Aleksandra Faust]]
- [[Aviral Kumar]]
- [[Rishabh Agarwal]]
