# Sutton & Barto

## Ch 1
__1.1__
__1.2__
__1.3__
- "the central role of value estimation is arguably the most important thing that has been learned about RL over the last six decades"
- in ch 8 we explore RL systems that simultaneously learn by trial and error, learn a model of the environment, and use the model for planning (*cool*)
__1.4__
- most of the RL systems in the book focus on estimating value functions
- RL systems that don't estimate value functions: genetic algos, genetic programming, simulated annealing, other optimization methods (these are all *evolutionary* methods)
    - don't learn by interacting with env
    - useful when policy space is small, or good policies are easy to find
    - useful in inaccessible envs
__1.6__
- Bellman extended work by Hamilton and Jacobi to form Bellman equation
- class of methods to solve optimal control problems by solving this equation called *dynamic programming*
- discrete stochastic version of optimal control problem called __MDP__
- Ronald Howard devised policy iteration method for MPDs. 
__1.7__
- Edward Thorndike's *Law of Effect*: describes effect of reinforcing events on the tendancy to select actions
    - controversial across disciplines
- see [cyberneticzoo.com](http://cyberneticzoo.com/) for early trial-and-error learning machines
- must read Minsky's paper "Steps Toward Artificial Intelligence" (1961)
    - *basic credit-assignment problem for complex reinforcement learning systems*: How do you distribute credit for success among the many decisions that may have been involved in producing it? 
    - all methods in this book essential attempt to solve that problem
- more readings
    - John Andreae, STeLLA system: internal model of world and "internal monologue" to deal with hidden state, goal of generating novel events
    - Donal Michie, MENACE: tic-tac-toe
    - Widrow, Gupta, Maitra modified Least-Mean-Square (LMS) algo to produce rule to learn from success and failure signals instead of training samples, our term *critic* originates here
    - __*learning automata*: methods for solving nonassociative, purely selectional learning problems like multi-arm bandit__
    - statistical learning theories applied to econ -> incorporation of game theory
    - John Holland (1975) - general theory of adaptive systems based on selectional principles (*classifier systems*)
    - Harry Klopf - most important person for reviving trial-and-error of RL
- temproal-difference learning (TD)
    - *secondary reinforcer*: a stimulus that has been parired with a primary reinforcer such as food or pain and , as a result, has come to take on similar reinforcing properties
    - influenced by animal learning theories
    - Sutton (1988) introduced $TD(\lambda)$ algo and proved some of its convergence properties
- Q-learning (Chris Watkins 1989)
    - TD and optimal control threads brought together


## Ch 3 
- in bandits we estimate value of $q_*(a)$ of each action $a$, in MDPs we estimate the avlue of $q_*(s,a) of each action in each state or $v_*(s)$ of each state given optimal action
- the added state requirement in MDPs allows credit-assingment for long-term consequences
__3.1__
- practice problems and examples of representing problems as MDPs
__3.2__
__3.3__
__3.4__
__3.5__
- *state-value function for policy* $\pi$ : $v_{\pi}(s) \doteq \mathbb{E}_{\pi}[\sum_{k=0}^{\infty}{\gamma^k R_{t+k+1} | S_t = s]}]$
- *action-value function for policy* $\pi$ : $q_{\pi}(s,a) \doteq \mathbb{E}_{\pi}[\sum_{k=0}^{\infty}{\gamma^k R_{t+k+1} | S_t = s, A_t = a]}]$
__3.6__
- Gridworld example and optimal policy derivation
__3.7__
__3.8__


## Ch 16 
__16.1__
__16.2__
__16.3__
__16.4__
__16.5__
__16.6__
__16.7__
__16.8__