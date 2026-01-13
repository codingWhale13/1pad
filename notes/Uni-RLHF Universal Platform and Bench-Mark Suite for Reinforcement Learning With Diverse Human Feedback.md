- motivation
	- there's a lack of standardized annotation platforms and good benchmarks for assessing RL algos that use human feedback for as reward
- introduced platform: Uni-RLHF
	- NOTE: RLHF here is not quite the same as RLHF in LLMs; the goal is to develop RL agents, not LLMs
	- standardized feedback encoding format
		- comparative feedback: given a pair of sequences, choose the better
		- attributive feedback: learn certain attributes such as speed, stride length, ...
		- evaluative feedback: assign a score to a segment
		- visual feedback: to learn saliency maps
		- keypoint feedback: identify time steps of special moments, e.g. "open the door"
	- implemented in Flask
	- contains three packages
		- universal multi-feedback annotation platform
		- large-scale crowd-sourced feedback dataset
		- modular offline RLHF baseline implementations

🗓️ 2024

✍️
- [[Yifu Yuan]]
- [[Jianye Hao]]
- [[Yi Ma]]
- [[Zibin Dong]]
- [[Hebin Liang]]
- [[Jinyi Liu]]
- [[Zhixin Feng]]
- [[Kai Zhao]]
- [[Yan Zheng]]
