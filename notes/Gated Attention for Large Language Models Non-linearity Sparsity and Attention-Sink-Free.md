#LLM #gating #MoE #SDPA

- motivation
	- gating mechanisms are heavily used, but there is a lack of understanding why they work
- background: what's gating?
	- $Y$: input to be modulated
	- $X$: another input used to compute the gating scores
	- $W_\theta$: learnable gate params
	- $\sigma$: activation function (e.g. sigmoid)
	- then we get the gated output by: $Y'=g(Y,X,W_\theta,\sigma)=Y\odot\sigma (XW_\theta)$
- method
	- let's compare 30 variants of MoE models and see if they improve if we apply a head-specific sigmoid gate after the scaled dot-product attention (SDPA)
		- spoiler: it does
	- they also try different positions for the gating mechanism, but after SDPA gives best performance improvement
- results
	- applying gating
	- why does it work so well?
		- we introduce a non-linearity between the two consecutive linear layers (value projection $W_v$ and dense $W_O$ projection)
		- sparsity mitigates the following common issues in LLMs:
			- massive activation: initial tokens have large activation values in the corresponding hidden state
			- attention sink: initial tokens disproportionately dominate attention score
- other take-aways
	- SDPA output gating is already used in Qwen3-Next models
	- gating itself provides significant intrinsic value, even when separated from the routing mechanism
	- when applying element-wise SDPA gating (i.e., gating after the attention-weighted value projection), train with a moderately increased learning rate


🗓️ 2025

✍️
- [[Zihan Qiu]]
- [[Zekun Wang]]
- [[Bo Zheng]]
- [[Zeyu Huang]]
- [[Kaiyue Wen]]
- [[Songlin Yang]]
- [[Rui Men]]
- [[Le Yu]]
- [[Fei Huang]]
- [[Suozhi Huang]]
- [[Dayiheng Liu]]
- [[Jingren Zhou]]
- [[Junyang Lin]]
