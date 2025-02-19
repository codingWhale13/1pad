#DL #multi-task #multi-modal

- different DL architectures are good for different domains - can they work together?
- introduced method: *MultiModel*
	- uses sub-networks from different domains
		- depthwise-separable convolutions
		- an attention mechanism
		- sparsely-gated mixture-of-experts layers
	- joint model is concurrently trained on different domains
		- ImageNet
		- multiple translation tasks
		- image captioning (COCO dataset)
		- a speech recognition corpus
		- an English parsing task

🗓️ 2017

✍️
- [[Lukasz Kaiser]]
- [[Aidan N. Gomez]]
- [[Noam Shazeer]]
- [[Ashish Vaswani]]
- [[Niki Parmar]]
- [[Llion Jones]]
- [[Jakob Uszkoreit]]
