#MTRL #Q-learning #offline-RL #CQL #C51 #atari-2600 #scaled-Q-learning #ResNet

![[Pasted image 20250423200805.png]]
- motivation
	- examine potential of scaling up offline RL to generalize over a broad set of tasks
	- become less reliant on supervised learning, but also try to learn from non-expert offline data
- introduced method: *Scaled Q-Learning*
	- base method is Conservative Q-Learning (CQL), an offline RL algo
		- uses a sum of two loss functions to combat Q overestimation on unseen actions
		- loss function: $\min_\theta \alpha(\mathbb E_{s\sim D}[\log (\sum_{a'}\exp (Q_\theta (s,a')))]-\mathbb E_{s,a\sim\mathcal D}[Q_\theta(s,a)]+\text{TDError}(\theta;\mathcal D)$
		- it's not clear what TDError performs best
			- C51 uses distribuational TDError
			- others use simply mean squared TD-error
			- -> this study tries both; turns out that MS TD-error doesn't scale well
			- -> categorical distributional representation of return values wins
		- in this work, CQL is extended as multi-headed architecture
	- three crucial points to make this work
		- modified ResNet architecture > typical deep Rl architectures
		- discretized representation of return distribution > MSE
			- trained with distributional cross-entropy loss
		- feature normalization
			- stabilizes training
			- prevents feature co-adaptation
	- transfer learning
		- online adaptation on new variants of training games
- results
	- single policy learns 40 games with near-human performance, using 80M params
	- while other methods like IMPALA scale poorly (even drop in performance), Scaled Q-Learning improves scales favorably with increased parameter size
- future directions
	- offline Q-learning with a transformer architecture
	- data augmentation
	- look into making offline finetuning to never-before-seen games work

🗓️ 2023

✍️
- [[Aviral Kumar]]
- [[Rishabh Agarwal]]
- [[Xinyang Geng]]
- [[George Tucker]]
- [[Sergey Levine]]
