##  Markov Decision Process
  
- only present matters
- stationary model (rules of game don't change)
  
__Problem__:
- states : <img src="https://latex.codecogs.com/gif.latex?s"/>
- model : <img src="https://latex.codecogs.com/gif.latex?T(s,a,s&#x27;)%20&#x5C;sim%20Pr(s&#x27;|s,a)"/>
- actions : <img src="https://latex.codecogs.com/gif.latex?a"/>
- reward : <img src="https://latex.codecogs.com/gif.latex?R,%20R(s)"/>
  
__Policy: a "solution" to a MDP problem__
- <img src="https://latex.codecogs.com/gif.latex?&#x5C;pi(s)%20&#x5C;rightarrow%20a"/> (policy maps states to actions)
- <img src="https://latex.codecogs.com/gif.latex?&#x5C;pi^*"/> maximized the total cummulative reward 
  
__RL vs Supervised Learning__
- in SL the input is <s, a> tuples (a is correct action in s)
- in RL the input is <s, a, r> tuples (r is reward for a in s)
- MDPs have delayed rewards
  
__Rewards__
- temporal credit assingment problem: how to rate past choices in problems with delayed rewards
- small negative reward in each state other than game ending states (goal/lava) trains the ideal policy (\pi*) 
    - large positive reward makes a policy that avoids goal (since endless traversal is better)
    - large negative reward makes a policy that can choose the lava (positive of goal not enough to outweigh negative of long journey)
- in MDPs minor changes matter
  
__Sequences of Rewards__
- infinite vs finite horizons (this course is infinite only) 
- utility of sequences: if U(s0, s1, ..) > U(s0, s1', ..), then U(s1, s2, ..) > (s1', s2', ..) 
    - note this is equivalent to the stationary model requirement of MDP
    - what is a good utility function? 
        - then U(s0, s1, ..) = \sum_t(R(s_t)), but in this case any countably infinite sum is equivalent for unending games (if you live forever, it doesn't matter what you do)
        - "discounted rewards" - instead use U(s0, s1, ..) = \sum_t(\gamma^t R(s_t)) where |\gamma| < 1 -- this is a geo series that converges 
        - so U(s0, s1, ..) <= \sum_t(\gamma^t R_max) = R_max/(1-\gamma)
  
__Policies__
- <img src="https://latex.codecogs.com/gif.latex?&#x5C;pi^*%20=%20argmax_{&#x5C;pi}%20E[&#x5C;sum_t(&#x5C;gamma^t%20R(s_t))%20|%20&#x5C;pi]%20="/> the policy that maximizes expected value of reward
- <img src="https://latex.codecogs.com/gif.latex?U^{&#x5C;pi}(s)%20=%20E[&#x5C;sum_t(&#x5C;gamma^t%20R(s_t))%20|%20&#x5C;pi,%20s_0%20=%20s]%20&#x5C;neq%20R(s)"/>
- Reward is immediate, utility is long term
  