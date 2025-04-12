#Q-transformer #MTRL #offline-RL #CNN #transformer

![[Pasted image 20250412173224.png]]
- motivation
	- train multi-task policies from large offline datasets
	- leverage both human demonstrations and autonomously collected data
- notes on the task setup
	- sparse rewards, i.e. success or failure
	- offline dataset
		- 39k successful episodes
		- 20k failed episodes -> also contain valuable data!
- introduced method: *Q-Transformer*
	- key idea: replace CNN with Transformer
	- this is a value-based aproach, so we learn the Q-function $Q(s, a)$
	- dealing with offline datasets
		- problem: $a_{t+1}$ maximizing $Q(s_{t+1},a_{t+1})$ can be out-of-distribution
		- solution approach: use conservative penalty that pushes down the Q-values $Q(s,a)$ for any $a$ outside of the dataset
	- 3 main ingredients
		1. tokenize inputs by discretizing each action dimension
			- each dimension of the action space is treated as a separate RL time
				- reason: avoid curse of dimensionality, number of action dims doesn't make things blow up
		2. perform maximization of Q-values over discretized actions
			- particular conservative Q-function regularizer minimizes values of every action that was *not* taken in dataset
			- per-dimension Bellman update
				- $Q(s_{t-w:t}, a_t^{1:i-1}, a_t^i) \leftarrow  \begin{cases}  \max_{a_t^{i+1}} Q(s_{t-w:t}, a_t^{1:i+1}, a_t^i) & \text{if } i \in \{1, \dots, d_A - 1\} \\ R(s_t, a_t) + \gamma \max_{a_{t+1}^1} Q(s_{t-w+1:t+1}, a_{t+1}^1) & \text{if } i = d_A  \end{cases}$
				- $d_\mathcal A$: action dim
				- $a_t^{1:i}$: vector of action dims from first dim $a_t^1$ to $i$th dm
				- $s_{t-w:t}$: time window for conditioning of autoregressive Q-function
				- reward is only for last dim (2nd line in equation), because there's no reward before executing the whole action
				- discounting only happens between time steps (1 otherwise)
		3. hybrid update
			- Monte Carlo
			- n-step returns, where n is such that the final Q-value of the last dim of the next time step is used as the Q-target

🗓️ 2023

✍️
- [[Yevgen Chebotar]]
- [[Quan Vuong]]
- [[Alex Irpan]]
- [[Karol Hausman]]
- [[Fei Xia]]
- [[Yao Lu]]
- [[Aviral Kumar]]
- [[Tianhe Yu]]
- [[Alexander Herzog]]
- [[Karl Pertsch]]
- [[Keerthana Gopalakrishnan]]
- [[Julian Ibarz]]
- [[Ofir Nachum]]
- [[Sumedh Sontakke]]
- [[Grecia Salazar]]
- [[Huong T Tran]]
- [[Jodilyn Peralta]]
- [[Clayton Tan]]
- [[Deeksha Manjunath]]
- [[Jaspiar Singht]]
- [[Brianna Zitkovich]]
- [[Tomas Jackson]]
- [[Kanishka Rao]]
- [[Chelsea Finn]]
- [[Sergey Levine]]
