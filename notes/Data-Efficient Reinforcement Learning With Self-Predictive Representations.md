#RL #representation-learning #self-supervised-learning #atari-100k #SPR #cosine-similarity

- goal: improve the data efficiency of deep RL methods
- introduced method: *SPR* (Self-Predictive Representations)
	- idea: use temporal consistency loss combined with data augmentations to increase performance, even with relatively few interactions with the environment
	- SPR extends a strong model-free agent by adding a dynamics model which predicts future latent representations provided by a parameter-wise exponential moving average of the agent itself
	- projection heads are used to project online (1 head) and target (another head) representations to a smaller latent space
- related work: Rainbow
	- SPR augments a sample-efficient variant of Rainbow with a model-based latent dynamics prediction objective
- crucial components of the method
	- target encoder is important (much better than using online encoder for target calculation)
	- dynamics modeling: increasing prediction depth K leads to better performance
	- temporal consistency loss outperforms both temporal and non-temporal variants of contrastive losses
	- cosine similarity works much better than MSE
	- projection and prediction networks improve performance (vs. removing them)
- result: new SOTA for Atari100k
	- evaluation is done with human-normalized score $\frac{\text{agent score}-\text{random score}}{\text{human score}-\text{random score}}$
		- Why not just $\frac{\text{agent score}}{\text{human score}}$? This baseline adjustment is useful to get better gauge the effort of the agent. It judges the agent more harshly, only taking into account its benefits beyond the baseline and not randomly achieved points
	- beside human-normalization, they also use DQN@50M-normalization

🗓️ 2021

✍️
- [[Max Schwarzer]]
- [[Ankesh Anand]]
- [[Rishab Goel]]
- [[R Devon Hjelm]]
- [[Aaron Courville]]
- [[Philip Bachman]]
