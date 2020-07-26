## Generalization 

**Think of your work on DQN in LunarLander**

### Function Approximation
- State can be thought of as a collection of features
- We can create generalizations of mappings for value functions, policies, reward functinos, etc. 
- Linear
    - Baird's counterexample shows linear function approximation does not always lead to convergence of value function approximation (certain initializations of the weights leads to divergence)
- Averagers
    - The function approximator can be thought of as an MDP over the basis states
    - Use convex combination of anchor points
    - Analogous to K-Nearest Neighbors (KNN)


### Recap
- Large state space requires generalization
- Use supervised learning to generalize
    - Linear function approximation
    - ANNs
- Successes 
    - TD-Gammon
    - DQN
- Averagers
    - Converges to optimal value function with function approximation
    - Function approximator can be viewed as a MDP 
    - Analogous to KNN