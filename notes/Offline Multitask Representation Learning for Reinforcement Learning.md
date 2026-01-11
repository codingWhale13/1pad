#RL #offline-RL #MTRL #representation-learning #MLE

- motivation
	- given an offline dataset from different tasks that share a common representation,  learn a shared representation
- introduced method: *MORL* (Multitask Offline Representation Learning)
	- estimates low-rank components via MLE
- theoretical results
	-  offline multitask representation learning is provably more sample efficient than learning each task individually
	- it's beneficial to use the learned representation from the upstream to learn a near-optimal policy of a new downstream task
		- in reward-free, offline and online setting
		- (as long as they share the same representation
- future work,
	- studying general function class representation learning in offline multitask setting

🗓️ 2024

✍️
- [[Haque Ishfaq]]
- [[Thanh Nguyen-Tang]]
- [[Songtao Feng]]
- [[Raman Arora]]
- [[Mengdi Wang]]
- [[Ming Yin]]
- [[Doina Precup]]
