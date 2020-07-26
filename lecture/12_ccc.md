## Coordinating, Communicating, Coaching  

### DEC-POMDP
- Multi-agent POMDP with shared reward function
- Special case of Partially Observable Stochastic Game (POSG)
- Properties
    - Elements of POMDPs and game theory
    - NEXP-Complete (for finite horizon)
    - Agents can benefit from communication
    - Optimal solution balance cost of communicating and cost of not communicating
    - Algorithms, heuristics, applications known

### Inverse RL (IRL)
- Input behavior and environment and output rewards
- Function approximation of $R$
- Maximum-likelihood IRL (MLIRL)

### Policy shaping
- Agent learns policy by adjustments from expert source (human or other agent) 
- Expert needs not be perfect to produce optimal policy

### Drama Management
- Story management system can be thought of as an MDP 
    - States: partial sequences of states
    - Actions: story actions
    - Model: player model
    - Rewards: author evaluations
- The above MDPs have a lot of states and scale poorly
- Instead, we can treat trajectories as targeted trajectory distribution MPDs (TTD-MDP)
    - Trajectories: sequence so far
    - Actions: story actions
    - Model: trajectory probabilities given player action and current trajectory
    - Target distribution: probabilities of ending with a trajectory
    - Policy: probability distribution over actions
    - Builds a tree of states, which can be learned via algos like Monte-Carlo Tree Search

### Recap
- DEC-POMDP: decentralized POMDP, multiagent environment with shared reward
    - Requires communication and coordination to solve
- Inverse RL (IRL)
    - Behaviors -> rewards 
    - Learn a reward function
- Coaching
    - Deomonstrations
    - Reward shaping 
    - Policy shaping
        - Expert need only be 70% correct
- Drama management
    - TTD-MDPs (targeted trajectory distribution)
- It's better to move machine design to meet human understanding than to expect humans to move to meet machine understanding