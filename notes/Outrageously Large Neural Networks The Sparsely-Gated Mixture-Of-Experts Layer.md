#DL #sparse-network #MoE #LSTM #LLM

- realizes "the promise of of conditional computation" - 1000x model cpacity
- introduces method: *Sparsely-Gated Mixture-Of-Experts Layer*
	- trainable gating network determines sparse combination of these experts during inference
	- the MoE layers are applied convolutionally between stacked LSTM layers
	- all experts have identical architectures, but separate parameters
		- up to 65536 experts (99.994% layer sparsity)
	- noisy top-k gating introduces two things to the softmax gating network:
		- sparsity (only top k values are considered)
		- tunable Gaussian noise
- shrinking batch problem
	- CPUs and GPUs need large batch sizes for computational efficiency
	- problem: if gating network chooses $k$ out of $n$ experts for each example and we have a batch of $b$ examples, then each expert receives only $\frac{kb}{n}\ll b$ examples
	- solution: make batch size as large as possible to account for this shrinking

🗓️ 2017

✍️
- [[Noam Shazeer]]
- [[Azalia Mirhoseini]]
- [[Krzysztof Maziarz]]
* [[Andy Davis]]
* [[Quoc Le]]
* [[Geoffrey Hinton]]
* [[Jeff Dean]]
