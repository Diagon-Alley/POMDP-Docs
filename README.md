## A Brief introfuction to Partially observable markov decision processes

In a markov decision process(MDPs) there is no uncertainty involved in control being at particular state. Such a model however cannot be used in a scenario where an observation may be noisy and can lead to a variety of states where the control is. A partially observable markov decision process is a model that allows for such an uncertainty and defines a probability distribution of states where the control may be given an observation. Thus this model is a significant improvement over MDPs when it comes to matural language understanding(NLU). 

The parameters that define a POMDP are as follows:

* S which is the set of states
* A is the set of actions that the machine may take
* O is the set of possible observations
* T defines the transition probability
* R defines the immediate reward obtained from taking an action when in a particular state
* Z defines the probability of a particular observation given the state and action
* `lamda` is a geometric discount factor
* b<sub>0</sub> is an initial belief state

A belief state is simply a proability distribution over the dialogue states. That is, when at time t what is the probability that the control is in state s.

For instance at time 0 the belief state is b<sub>0</sub>.