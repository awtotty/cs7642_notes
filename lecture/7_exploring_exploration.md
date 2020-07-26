## Exploration

### Bandits
- Policy paradigms
    - Maximum maximum likelihood
    - Maximum confidence
    - Minimum confidence 
- Exploration-exploitation dilemma
- Bandit metrics
    - Identifies optimal arm in the limit 
    - Maximize (discounted) expected reward 
        - Gittins index: describes how high of a payoff would be required to ignore possible rewards of low-confidence alternatives
        - Gittins seems to be of limited value beyond bandits 
    - Maximize expected reward over finite horizon
    - Identify near optimal arm with high probability in time some time that is a function in $k$, $1/\delta, 1/\epsilon$
    - **Nearly** maximize reward with high probability in some time as above
    - Pull non-near optimal arm no more than some number of times (Mistake Bound)
    - ITO Find Best -> Few Mistakes -> Do Well
### Hoeffding bound
- Captures how confident the maximum likelihood estimate is in terms of number of experiences

### Deterministic MDPs
- Mistake Bound : The number of $\epsilon$-suboptimal action choices is bounded in poly($1/\epsilon, 1/\delta, n, k$), where $n$ is the number of states, $k$ is number actions in each state
- Rmax: 
    - "Optimism in the face of uncertainty"
    - Algorithm: 
        - Keep track of MDP
        - Any unknown state-action pair is Rmax (update as observed)
        - Solve the MDP
        - Take action from $\pi^*$
    - Once all edges are known, no more mistakes
    - Stop exploring unknowns when total reward from exploration cannot be greater than known path
    - Finds near optimal policy (optimal policy not guaranteed)
    - Can make more mistakes than Mistake Bound 

### Stochastic MDP 
- General Rmax: Keep track of unknown values using Rmax and Hoeffding bound
- Simulation lemma: If a simulation of an MDP is a good approximation of the MDP, policies that do well in the simulation will do well in the MDP
- Explore-or-Exploit lemma: If all transitions are either accurately estimated or unknown, optimal policy is either near optimal **or** an unknown state is reached "quickly"

### Recap
- Bandits
    - Can apply Hoeffding and Union bounds to measure confidence in current konwledge about each arm (action)
- Rmax
    - "Optimism in the face of uncertainty"
    - Assumes unexplored actions produce some maximum possible reward, which encourages exploration via greedy action selection
    - "Grass is always greener..."
- Bandits + Rmax = stochastic + sequential 
- KWIK