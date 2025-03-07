#RL #MTRL #SAL #multi-domain

![[Pasted image 20250307234527.png]]
- motivation
	- how can MTRL agents learn in different domains where the state and action space dimensionality varies?
- introduced method: *SAL*  (Shared domain-Agnostic Latent space)
	- idea:
		- learn a single shared latent policy
		- to account for domains with different observation spaces, use domain-specific
		- to account for different action dimensionality, domain-specific action heads are used
	- scope
		- considers different domains and robot morphologies
		- online RL, authors use SAC
- results are unclear, code is not available on Github
	- plots show that domain-specific translation layers perform better than zero-padding the observations and/or "slicing the output" (keeping only relevant action dims in the respective domain)

🗓️ 2024

✍️
- [[Reginald McLean]]
- [[Kai Yuan]]
- [[Isaac Woungang]]
- [[Nariman Farsad]]
- [[Pablo Samuel Castro]]
