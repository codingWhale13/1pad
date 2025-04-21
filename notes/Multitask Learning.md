#MTL #backpropagation #inductive-bias #KNN

- motivation
	- instead of learning tasks one at a time by breaking them down into small separately learned problems, let's use training signals of related tasks to speed up learning
	- this work is not concerned with computational efficiency, just accuracy
	- goal: improve generalization by using domain information contained in training signals of related tasks as an inductive bias
		- inductive bias = anything that causes an inductive learner to prefer some hypotheses over other hypotheses
		- from the perspective of one task, all the other tasks, that are learned jointly, serve as an inductive bias
- introduced method: *Backprop MTL
	- consider neural net trained with backprop
	- add extra outputs for different but related tasks
	- this is the simplest method to do multitask inductive transfer
- MTL works; here are some domains in which many related tasks need to be learned
	- 1D-ALVINN (simulated domain)
		- one or two lanes
		- location of road center
		- intensity of region bordering road, road surface, centerline
		- location ofcenterline, left/right edge of road
	- 1D-DOORS (real domain)
		- horizontal location of doorknob, doorway center, left door jab, left edge of door, right door job, right edge of door
		- width of of left doorway, door jab, right door jab
		- single or double door
	- pneumonia prediction (real domain)
		- main task: basic measurements prior to hospital admission
		- auxiliary tasks: extra lab tests once patients are admitted to the hospital (usually of higher quality, but cannot be used for pre-admission prediciton, of course)
	- => MTL > STL in terms of accuracy
- how does MTL work?
	- the experiments above were made using backprop MTL
		- but are improvements really due to related tasks or are the extra output just adding uncorrelated noise, yielding better generalization?
		- the authors rule this out by doing a "shuffle test": for each case in the training set, keep the correspondence to the main task, but shuffle the extra task training signals randomly -> this eliminates the relationship of extra tasks being meaningfully related to the main task -> MTL performance drops to STL level
	- learning tasks in parallel while using a shared representation is useful because
		- statistical data amplification: effective increase in sample size due to extra info
		- attribute selection (a consequence of data amplification): when tasks T and T' use common hidden layer features F, learning both tasks gives better training signals for F and reduces allows it to distinguish better than just using T
		- eavesdropping: a hidden layer feature F might be useful for tasks T and T' but much simpler to learn using task T' -> beneficial for T as well
		- representation bias: MTL tasks prefer NOT to use hidden layer representations that other tasks prefer NOT to use (according to their constructed experiment)
		- backprop MTL discovers how tasks are related: using a shared hidden layer is able to discover how tasks are related on hidden layer features without being told about the relatedness explicitly
- is MTL applicable? yes, in many classes of problems such as
	- using the future to predict the present (e.g. in pneumonia prediction)
	- having multiple metrics / representations of the same problem can aid learning
	- time series data: predicting events of multiple tasks at the same time step, i.e. short-term vs. long-term time scale
	- having few expensive features can still be useful as extra features
	- using extra features to focus attention, e.g. road domain
	- sequential transfer: use outdated data to deal with new data
	- learn multiple tasks, arising naturally together (e.g. location, time of day, day of week, duration of scheduled meetings)
	- quantization smoothing: quantized tasks are usually harder to learn (e.g. pneumonia patient lives or dies) but learning to predict more features (e.g. length of stay in hospital) benefits learning
	- some inputs work better as outputs
- using MTL outside of backprop nets
	- k-nearest neighbor
	- kernel regression
	- decision tree
- limitations
	- worst-case bounds are too guarantee that extra tasks will help (they can actually hurt)
	- no well-defined notion of task relatedness
	- tricky to combine with search procedures such as early-stopping

🗓️ 1998

✍️
- [[Rich Caruana]]
