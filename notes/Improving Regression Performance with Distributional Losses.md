#supervised-learning #RL #regression #HL #KL-divergence

![[Pasted image 20250311235624.png]]
- motivation
	- growing evidence, both in supervised learning and RL: learning distribution ("soft targets") rather than hard targets is beneficial
	- in analyzing why distributional losses benefit the RL setting, the authors initially set out to explore reduced overfitting and improved representations
		- original hypothesis: converting problem essentially to a multi-task setting (1 output -> multiple values) promotes generalization in the learner and reduces overfitting
		- new hypothesis: optimization properties of the HL seem to be the key factor in the resulting improved accuracy
- note: throughout the paper, we're still doing regression
	- the authors don't "provide another method to learn distributions" but rather show that forming a distribution over the target $Y$ is beneficial even if it is only used for mean prediction
- introduced loss: *HL* (histogram loss)
	- goal: predict continuous target $Y$, given inputs $\mathbf x$
	- instead of doing old-school regression on $Y$, we do this
		- target distribution $p=Y\mid\mathbf x$
			- manually chosen up-front!
			- support $[a, b]$
			- pdf $p$
			- cdf $F$
		- prediction distribution $q_\mathbf x:\mathcal Y\to[0,1]$
			- learned
			- histogram density
		- some math leads to the Histogram Loss $HL(p,q_\mathbf x)=-\Sigma_{i=1}^k p_i\log f_i(\mathbf x)$
	- the paper continues presenting multiple ways of selecting $p$, with the HL-Gaussian performing best ($\mu$ is actual data, $\sigma^2$ is fixed)
- properties of Histogram Loss
	- histogram density is trade-off between
		- flexible prediction distribution and
		- efficient computation of KL-divergence
	- stable gradients due to small Lipschitz constant
	- low variability, compared to l2 loss

🗓️ 2018

✍️
- [[Ehsan Imani]]
- [[Martha White]]
