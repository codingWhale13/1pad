#VQA #cross-entropy-loss #soft-cross-entropy #classification

- motivation
	- in VQA (visual question answering), humans or AIs give an answer to a question of what's happening in an image
	- in the VQA literature, there's a mismatch
		- the cross-entropy loss penalizes the all wrong categories that got non-zero probability except the most popular one (which should be the right one)
		- evaluation of VQA however considers *all* ground-truth answers
	- this means the cross-entropy loss doesn't reflect what we optimize for in this case
- background
	- cross entropy loss: $\mathcal L(x,c^*)=-x_{c^*}+\log (\sum_{j=1}^{\lvert x\rvert}\exp (x_j))$
		- x: vector of network activations for each class
		- $c^*$: index of the correct class
	- contrary to conventional classification problems, the VQA evaluation metric considers an answer correct if it was given by at least 3/10 human annotators; this accuracy is averaged over all subsets of ground-truth answers
		- $Acc(a)=\frac{1}{10}\sum_{k=1}^{10}\min (\frac{\sum_{j=1,j\neq k}^{10}\mathcal 1(a=a_j)}{3},1)$
- proposed loss function: *soft cross-entropy*
	- $\mathcal L(x,c,w)=\sum_{i=1}^{\lvert c\rvert} w_i(-x_{c_i}+\log (\sum_{j=1}^{\lvert x\rvert}\exp (x_j)))$
		- $c$: vector of unique ground-truth answers
		- $w$: vector of answer weights computed as the number of times the unique answer appears in the ground-truth set divided by the total number of answers
- result
	- on average, 1.5% higher accuracy, when swapping out CE loss with soft-CE loss

🗓️ 2017

✍️
- [[Ilija Ilievski]]
- [[Jiashi Feng]]
