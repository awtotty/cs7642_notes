## Markov Decision Process
- only present matters
- stationary model (rules of game don't change)

__Problem__:
- states : s
- model : T(s,a,s') ~ Pr(s'|s,a)
- actions
- reward

__Policy: a "solution" to a MDP problem__
- \pi(s) -> a (policy maps states to actions)
- \pi* maximized the total cummulative reward 

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
- \pi^* = argmax_pi E\[\sum_t(\gamma^t R(s_t)) | pi\] = the policy that maximizes expected value of reward
- U^{\pi}(s) = E\[\sum_t(\gamma^t R(s_t)) | pi, s_0 = s\] != R(s) 
- Reward is immediate, utility is long term