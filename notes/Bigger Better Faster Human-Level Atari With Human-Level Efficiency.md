#RL #BBF #EfficientZero #atari-100k #SR-SPR

![[Pasted image 20250303232443.png]]
- motivation
	- improving on Atari 100k benchmark (~2h of gameplay) through scaling up
	- tackling the question: how can we scale the model when samples are scarce?
- introduced method: *BBF* (Bigger, Better, Faster)
	- based on SR-SPR with a lot of modifications to tune performance
		- replay ratio: 8
		- harder resets: 50% instead of 20%
		- bigger network: 15-layer ResNet, scaling up width 4x compared to Impala-CNN
		- increasing discount factor: schedule from 0.97 to 0.997
- results
	- super-human performance in the Atari 100K benchmark
		- 5x more sample-efficient than SR-SPR
		- as sample-efficient as EfficientZero but 4x faster (also note that BBF is model-free while EfficientZero is model-based)
		- receding update horizon: decreases exponentially from 10 to 3 over the first 10k gradient steps following each network reset
- take-aways
	- in RL, a one-size-fits-all solution is unrealistic due to variability in problem characteristics
		- but many insights transfer across problem domains
	- self-supervision is crucial: " It is worth noting that EfficientZero uses a self-supervised objective that is extremely similar to SPR, a striking commonality between BBF and EfficientZero"

🗓️ 2023

✍️
- [[Max Schwarzer]]
- [[Johan Obando-Ceron]]
- [[Aaron Courville]]
- [[Marc G. Bellemare]]
- [[Rishabh Agarwal]]
- [[Pablo Samuel Castro]]
