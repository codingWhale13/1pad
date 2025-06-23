#LLM #reasoning-evaluation
- motivation
	- it's hard to say how good LLMs are at reasoning
		- they might perform really well in some benchmarks, where language understanding is sufficient
		- but in other benchmarks, where actual step-by-step reasoning from axioms is required, they fall short
	- in short: static QA is only an indirect test of reasoning
	- goal: create a benchmark testing true reasoning capabilities by providing problems that a model has not seen before
		- make sure, there's no information leakage
- proposed framework: *MATH()*
	- idea overview
		1. given static QA tests,
		2. convert it into a functional variant taking a set of random generators as input,
		3. to let the LLM solve snapshot (called QA* in the paper) of each test
	- this idea can be applied to many NLP benchmarks, but focus of this paper is MATH benchmark
		- e.g. "Compute $\left(-\sqrt{5321}\right)^2$" -> 5321
- finding: there's a "reasoning gap" (difference of performance w/ vs. w/o testing functional variants) in all LLMs as of now

🗓️ 2024

✍️
- [[Saurabh Srivastava]]
- [[Annarose M B]]
- [[Anto P V]]
- [[Shashank Menon]]
- [[Ajay Sukumar]]
- [[Adwaith Samod T]]
- [[Alan Philipose]]
- [[Stevin Prince]]
- [[Sooraj Thomas]]
