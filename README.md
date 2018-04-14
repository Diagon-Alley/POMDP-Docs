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

Now, when the POMDP operates it also makes use of a policy. The policy actually chooses an action given a point in belief space. Belief space is simply the set of all belief states. A policy defines that when in a particular belief state, what is the action that I am supposed to take.

### The sequence of events in a POMDP

The sequence of events when a POMDP operates follows a cycle. At each step(time step or when the user has given some utterance for the POMDP to process), the machine is in some unobserved state s<sub>m</sub>. Since the true state is unknown(recall that this is a fundamental assumption in POMDPs), the machine (POMDP) maintains a probability distribution over the states. This probability distribution is called the belief state **b** at the current time step. Based on this belief state **b** and a policy being followed, the machine takes an action a. The machine is thus rewarded with r(s<sub>m</sub>, a<sub>m</sub>) and the state transitions to a new unobserved state s'<sub>m</sub> with some transition probability. At this point the machine receives an observation o with a probability dependent only on the new state s'<sub>m</sub> and the machine action a<sub>m</sub>. So basically I already have the probability distribution for the observation versus the joint probability of the new state and the action taken.  Now after I get the observation, I found out what was the probability that I will get that observation by coming to the new state s'<sub>m</sub> with the action a<sub>m</sub>. Now based on all this data, I now update my belief state and this cycle repeats. 

When training the POMDP all we need to do is optimize the policy as far as possible. For this we define a `task specific objective function`. The entire goal is really to maximize the task specific objective function. This objective function is typically dependent on the reward. The idea is to find a policy that maximizes the value function at every point of the belief space(basically at every belief state). 

