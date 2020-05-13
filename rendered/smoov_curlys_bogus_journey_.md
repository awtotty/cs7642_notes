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
- in SL the input is <img src="https://latex.codecogs.com/gif.latex?&#x5C;langle%20s,%20a%20&#x5C;rangle"/> tuples (a is correct action in s)
- in RL the input is <img src="https://latex.codecogs.com/gif.latex?&#x5C;langle%20s,%20a,%20r%20&#x5C;rangle"/> tuples (r is reward for a in s)
- MDPs have delayed rewards
  
__Rewards__
- temporal credit assingment problem: how to rate past choices in problems with delayed rewards
- small negative reward in each state other than game ending states (goal/lava) trains the ideal policy <img src="https://latex.codecogs.com/gif.latex?&#x5C;pi^*"/> 
    - large positive reward makes a policy that avoids goal (since endless traversal is better)
    - large negative reward makes a policy that can choose the lava (positive of goal not enough to outweigh negative of long journey)
- in MDPs minor changes matter
  
__Sequences of Rewards__
- infinite vs finite horizons (this course is infinite only) 
- utility of sequences: if <img src="https://latex.codecogs.com/gif.latex?U(s0,%20s1,%20..)%20&gt;%20U(s0,%20s1&#x27;,%20..)"/>, then <img src="https://latex.codecogs.com/gif.latex?U(s1,%20s2,%20..)%20&gt;%20(s1&#x27;,%20s2&#x27;,%20..)"/>
    - note this is equivalent to the stationary model requirement of MDP
    - what is a good utility function? 
        - then <img src="https://latex.codecogs.com/gif.latex?U(s0,%20s1,%20..)%20=%20&#x5C;sum_t(R(s_t))"/>, but in this case any countably infinite sum is equivalent for unending games (if you live forever, it doesn't matter what you do)
        - "discounted rewards" - instead use <img src="https://latex.codecogs.com/gif.latex?U(s0,%20s1,%20..)%20=%20&#x5C;sum_t(&#x5C;gamma^t%20R(s_t))"/> where <img src="https://latex.codecogs.com/gif.latex?|&#x5C;gamma|%20&lt;%201"/> -- this is a geo series that converges 
        - so <img src="https://latex.codecogs.com/gif.latex?U(s0,%20s1,%20..)%20&#x5C;leq%20&#x5C;sum_t(&#x5C;gamma^t%20R_{max})%20=%20R_{max}&#x2F;(1-&#x5C;gamma)"/>
  
__Policies__
- <img src="https://latex.codecogs.com/gif.latex?&#x5C;pi^*%20=%20&#x5C;text{argmax}_{&#x5C;pi}%20E[&#x5C;sum_t{&#x5C;gamma^t%20R(s_t)}%20|%20&#x5C;pi]%20="/> the policy that maximizes expected value of reward
- <img src="https://latex.codecogs.com/gif.latex?U^{&#x5C;pi}(s)%20=%20E[&#x5C;sum_t{&#x5C;gamma^t%20R(s_t)}%20|%20&#x5C;pi,%20s_0%20=%20s]%20&#x5C;neq%20R(s)"/>
- Reward is immediate, utility is long term value of policy
- Usually we use <img src="https://latex.codecogs.com/gif.latex?U(s)%20=%20U^{&#x5C;pi^*}(s)"/> -- "true utility of a state"
- <img src="https://latex.codecogs.com/gif.latex?&#x5C;pi^*(s)%20=%20&#x5C;text{argmax}_a%20&#x5C;sum_{s&#x27;}{T(s,%20a,%20s&#x27;)%20U(s&#x27;)}"/>
    - knowing true utility means you can find optimal policy
- __Bellman Equation:__ <img src="https://latex.codecogs.com/gif.latex?U(s)%20=%20R(s)%20+%20&#x5C;gamma%20&#x5C;max_a%20&#x5C;sum_{s&#x27;}{T(s,%20a,%20s&#x27;)%20U(s&#x27;)}"/>
    - how to solve? n equations (one for each utilities) and n unknowns (utilities), but not linear equations (due to max)
    - algo to solve (__value iteration__):  (proof of convergence on slide 25 [here](https://s3.amazonaws.com/ml-class/notes/MDPIntro.pdf ))
        - start with arbitrary utilities
        - update utilities based on neighbors
        - repeat update step until convergence
    - Ex. ![https://classroom.udacity.com/courses/ud600/lessons/4100878601/concepts/6512308860923](../images/find_policy.png ) 
        notes: Don't forget the transition probabilities: 0.8 of going in the desired direction, and 0.1 of going in each of the directions at 90-degrees, <img src="https://latex.codecogs.com/gif.latex?U_0(green)%20=%201"/>, ~ <img src="https://latex.codecogs.com/gif.latex?U_0(red)%20=%20-1"/>
        - <img src="https://latex.codecogs.com/gif.latex?U_1(x)%20=%20-0.04%20+%200.5[0%20+%200%20+%200.8*1]%20=%200.36"/>
        - <img src="https://latex.codecogs.com/gif.latex?U_2(x)%20=%20-0.04%20+%200.5((0.1)(-0.4)%20+%20(0.1)(0.36)%20+%200.8*1)%20=%200.376"/>
    - the optimal policy can be found even if the true utility is not found (order of actions is all that is needed)
    - find policy (__policy iteration__): 
        - start with <img src="https://latex.codecogs.com/gif.latex?&#x5C;pi_0"/>
        - evaluate: given <img src="https://latex.codecogs.com/gif.latex?&#x5C;pi_t"/> calculate <img src="https://latex.codecogs.com/gif.latex?U_t%20=%20U^{&#x5C;pi_t}"/>, where <img src="https://latex.codecogs.com/gif.latex?U_t%20=%20R(s)%20+%20&#x5C;gamma%20&#x5C;sum_{s&#x27;}{T(s,%20&#x5C;pi_t(s),%20s&#x27;)%20U_t(s&#x27;)}%20="/> reward + gamma*expected utility 
        - improve: <img src="https://latex.codecogs.com/gif.latex?&#x5C;pi_{t+1}%20=%20&#x5C;text{argmax}_a%20&#x5C;sum{T(s,%20a,%20s&#x27;)%20U_t(s&#x27;)}"/>
    - the algo above is now linear (no max to find <img src="https://latex.codecogs.com/gif.latex?U_t"/>)
  
__More on Bellman__
- other ways to express Bellman: 
    - value of state <img src="https://latex.codecogs.com/gif.latex?=%20V(s)%20=%20&#x5C;max_a%20(R(s,a)%20+%20&#x5C;gamma%20&#x5C;sum_{s&#x27;}{T(s,a,s&#x27;)V(s&#x27;)})"/>
    - quality of a state,action <img src="https://latex.codecogs.com/gif.latex?=%20Q(s,a)%20=%20R(s,a)%20+%20&#x5C;gamma%20&#x5C;sum_{s&#x27;}{T(s,a,s&#x27;)%20~%20&#x5C;max_{a&#x27;}Q(s&#x27;,a&#x27;)}"/>  --  useful when you don't know R and T
    - continuation of state,action <img src="https://latex.codecogs.com/gif.latex?=%20C(s,a)%20=%20&#x5C;gamma%20&#x5C;sum_{s&#x27;}{T(s,a,s&#x27;)%20~%20&#x5C;max_{a&#x27;}(R(s&#x27;,a&#x27;)+C(s&#x27;,a&#x27;))}"/>
- Ex. ![https://classroom.udacity.com/courses/ud600/lessons/4100878601/concepts/41234786540923](../images/relating_bellmans.png )
    Soln: ![https://classroom.udacity.com/courses/ud600/lessons/4100878601/concepts/41234786540923](../images/relating_bellmans_soln.png ) 
  
  