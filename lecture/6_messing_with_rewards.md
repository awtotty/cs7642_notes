## Messing with Rewards 

- reward functions are kind of like formal languages
    - semantics 
    - efficiency (speed, space)
    - solvability
- lots of work to be done here (cool research area)

### Changing the Reward Function
- results are invariant if $R$ is...
    - multiplied by a (positive) scalar
        - if $R'(s,a) = cR(s,a)$, then $Q'(s,a) = cQ(s,a)$ 
    - shifted by a constant
        - if $R'(s,a) = R(s,a)+c$, then $Q'(s,a) = Q(s,a) + \frac{c}{1-\gamma}$ 
    - shifted by non-linear potential function
        - reward shaping (inspired by B.F. Skinner)
        - modify reward to incentivize progressively more complex tasks
        - think of training an animal to do a complex task
    
### Reward Shaping
- **while shaping rewards avoid creating a suboptimal positive feedback loop**
- potential functions
    - change-in-state-based bonuses (get rewards for reaching certain states)
    - if entering a state gains a positive reward, leaving that state loses the same reward
    - Ex. move from 10 pixels from ball to 5 pixels from ball, get $\frac{1}{5} - \frac{1}{10} = 0.1$ 
    move from 5 pixels from ball to 10 pixels from ball, get $\frac{1}{10} - \frac{1}{5} = -0.1$ 
- potential-based shaping: 
    - if $Q(s,a) = \sum_{s'} T(s,a,s')(R(s,a,s') + \gamma\max_{a'}Q(s',a')$ and $R'(s,a,s') = R(s,a)-\psi(s) + \gamma\psi(s')$, then $Q'(s,a) = Q(s,a)-\frac{\gamma\psi-\psi}{1-\gamma} = Q(s,a)-\psi(s) $
    - $\psi(s)$ represents what potential you are going to lose by leaving the state
- Wiewiora showed potential-based shaping of Q update produces same updates as Q update with Q initialized to reflect potential (see [paper](https://arxiv.org/abs/1106.5267))