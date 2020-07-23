## Partially Observable Markov Decision Processes

### POMDP Basics
- True MPD hidden from agent (agent must infer current state from observable features)
- $O(s,z) = $ probabiltity of seeing feature $z$ if in state $s$ 
- **POMDP generalizes MPD**: Any POMDP can be thought of as an MDP where observable feature space is the state space and $O(s,z) = 1$ if $s = z$ else $0$. 

### Belief MDP 
- We can reframe POMDP as a belief MDP
- $b$ is a vector representing a probability distribution over states, and $b(s)$ is the probability agent is in state $s$. 
- $b, a, z \rightarrow b'$ (note: reward is not directly observed, the observation can include the reward)
- $b'(s') = Pr(s'| b,a,z) = \frac{\sum_s b(s) O(s',z) T(s,a,s')}{\sum_s\sum_{s'} b(s)O(s',z)T(s,a,s')}$ by Baye's Rule

#### Solving Belief MDP (Planning): 
- The belief MDP is infinite (there are an infinite number of possible states), so requires care to solve
- The value of a given belief state $b$ is piece-wise linear and convex
- Convert infinite value vectors to finite sets of upper bounds on the values (Littman describes these as "bags of vectors")
- We can define a function `purge` to eliminate vectors that do not contribute to the max piece-wise linear convex function
    - `purge` can speed up computation, but it can be challenging to know if a vector is dominated by the union of other vectors
    - `purge` is polynomial in complexity of linear programming

### RL for POMDP
- Model-based RL (learn a model and use it) - learn POMDP 
    - Expectation Maximization (EM): make a hypothesis to get expectation, use expectations to maximize model? (See HMM for examples?)
- Model-free RL (don't learn model) - map observations to actions 
    - Memoryless policies

### Bayesian RL 
- RL can be thought of an MDP with planning
- Baye's Rule allows for normalization of belief state probabilities as we learn to rule out certain beliefs
- An optimal policy in this problem maximizes reward
    - Exploiting in the belief state results in maximizing reward **and** identifying the MDP the agent is actually in
    - Exploration is not explicitly required
- RL is actually planning in a kind of continuous POMDP (hidden state is the set of parameters of the MDP we are trying to learn)
- Bayesian RL is currently too expensive to be widely practical

### Predictive State Representation (PSR)
- POMDP: belief state is distribution over states
    - If states are never observed, do they even exist? 
- PSR: predictive state is probability of future predictions
    - Create test by taking actions and making observations
    - Predictive states are distribution of **outcomes of tests**
- Relatively easy to convert from belief state to predictive state (find probability of test outcome for each possible current state from belief state)
    - Reverse process is not always possible (there is more than one belief state that corresponds to a predictive state) -- see thm below
- **PSR Theorem: Any $n$-state POMDP can be represented by a PSR with no more than $n$ tests, each of which is no longer than $n$ steps long**
- In some cases where state space is continuous, PSR can be more efficient than POMDP
- In general, hard POMDPs correspond to hard PSRs