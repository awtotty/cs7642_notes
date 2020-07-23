
## Options 

### What make RL hard? 
- Delayed reward
- Bootstrapping -> need good exploration
- Learning algorithm complexity is heavily impacted by number of states and number actions
    - function approximation for $V(s)$ or $Q(s,a)$ attempts to avoid this problem
- Goal: generalize on actions to improve scaling

### Temporal abstraction
- Creates new actions that combine existing actions
- A sequence of many actions can be generalized to a sequence of a few actions
    - Allows value backup to jump temporally (recall grid world with rooms)

### Options
- Semi-MDP (SMDP) : MDP in which agent may make jumps in time
    - These are not truly Markov because you need to know how much has time has passed under execution of time jump
- Option : a tuple $(I,\pi,\beta)$ that represents a sequence of actions
    - $I$ is initiation set of states
    - $\pi$ is a policy that maps $(s,a) \rightarrow [0,1]$
    - $\beta$ is a termination set of states, $s \rightarrow [0,1]$ 
    - Note: $\beta$ encapsulates the idea of interruption of an option
- Options are generalizations of actions
- At the level of options, SMDPs are MDPs
- Unlike the atomic actions of an MDP (each action takes the same amount of time), options require variable amount of time 
    - Each "immediate reward" of an option is actually an expected discounted reward over the number of time steps required to execute the option
    - Similarly, the options transition function hides discounts for future rewards for each time stop required to execute the option

### State abstraction as a consequence of temporal abstraction
- Using options to abstract actions results in state abstractions as well
    - Pac-man example in which the option "avoid ghosts" provides an abstraction for all states in which ghosts can hurt player
    - Thus, under certain options we can reduce the size of the state space in which we are operating
- Thus, during learning, we can avoid "boring" parts of the state space -- this avoids unhelpful exploration
- If options are not carefully defined, optimal policy may not be found

### Goal abstraction
- Options can be executed in parallel 
    - Agent can learn goal of move to door of room 1 and move from door of room 2 to goal simultaneously
- Parellel goals (e.g. as in preditor-prey problems)
    - Then options descrie competing goals and learning is reduced to identifying most important goal in any given moment
- **Modular RL**: learn goal arbitration
    - Greatest mass Q-learning (each goal "votes" for the action to take, highest count wins)
    - Top Q-learning (take action from goal with highest value)
    - Negotiated W-learning (the agent with the most to lose chooses the action)
    - Problem with all of these: each agent may be using different value units, so each of these approaches must resolve this with an Arbitrator (dictator) or assuming each agent uses the same units

### Monte Carlo tree search
- Select, Expand, Simulate, Back up
- Rollout policy: policy to follow when expanding tree leaves to subtrees
- Goals that define options usually have one of two forms: 
    - Goals with measurable success and finite horizon
    - Goals with measurable failure and infinite horizon (constraints)
- We can replace the action edges in MCTS with option edges
- Properties
    - Useful for large state spaces, due to sampling
    - Planning time is independent of number of states
    - Running time is exponential in the horizon, $O((|A|*x)^H)$, where $x$ is the number of steps to take and $H$ is the horizon