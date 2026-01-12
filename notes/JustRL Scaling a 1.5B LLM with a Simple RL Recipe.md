#RLVR

- motivation
	- modern LLM architectures are quite complex
	- can we achieve similar performance when we strip away some of their components?
- method
	- GRPO in veRL with binary outcome rewards
	- simplifications:
		- single-stage training: no progressive context lengthening, no curriculum switching, no stage transitions
		- fixed hyper-parameters: no adaptive temperature scheduling, no dynamic batch size adjustments, no mid-training reference model resets
		- standard data: DAPO-Math-17k, no offline difficulty filtering or online dynamic sampling strategies
		- basic prompting: un-tuned suffix prompt
		- length control: max context length 16k
- results
	- smooth training curves
	- adding "improvements" actually worsens performance
		- although note that the authors only consider 1.5B param models and a specific dataset setting on mathematical reasoning
	- on-par performance
	- 2x less compute than comparable methods

🗓️ 2025

✍️
- [[Bingxiang He1]]
- [[Zekai Qu]]
- [[Zeyuan Liu]]
- [[Yinghao Chen]]
- [[Yuxin Zuo]]
- [[Cheng Qian]]
- [[Kaiyan Zhang]]
- [[Weize Chen]]
- [[Chaojun Xiao]]
- [[Ganqu Cui]]
- [[Ning Ding]]
- [[Zhiyuan Liu]]
