#LLM #RL #code-generation

- motivation
	- given some problem specification in natural language and unit tests, can we solve coding tasks?
	- in particular, when code fails, can we use RL to debug it automatically?
- proposed method: CodeRL
	- framework for program synthesis
	- uses RL to improve pretrained language models
		- concretely: using CodeT5-large (770M params)
- framing program synthesis as an RL problem
	- actor-critic approach, based on REINFORCE
		- actor: CodeT5-large, stochastic LM policy
		- critic: CodeT5-small
- benchmarks
	- APPS: training and test sets with 5000 samples each of programming tasks with three difficulties
	- MBPP: simpler than APPS, good for zero-shot evaluation
- results
	- success is evaluated using pass@k metric: percentage of problems solved by using $k$ generated programs per problem
	- CodeRL beats much larger GPT models on MBPP

🗓️ 2022

✍️
- [[Hung Le]]
- [[Yue Wang]]
- [[Akhilesh Deepak Gotmare]]
- [[Silvio Savarese]]
- [[Steven C. H. Hoi]]
