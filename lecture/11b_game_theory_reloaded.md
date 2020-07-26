## Game Theory 2 

### Repeated games
- If the number of repetitions is known, nothing changes (strategies are those for a single game)
- If number of repetitions unknown, threats can matter

### Finite state strategies for unbounded repeated games
- Player choice affects payoff and future decisions of opponent
- Choosing actions can be treated as MDP (so solving a MDP corresponds to chossing a strategy against a strategy)
- Tit-for-tat  
    - First round cooperate, then copy opponent's previous move 
- Security level profile (minmax in mixed strategies)
    - Intersection of feasible region and acceptable (preferable) region
- **Folk Theorem**: in repeated games, the possibility of retaliation opens the door for cooperation
    - = any feasible payoff profile that strictly dominates the minmax/security level profile can be realized as a NE payoff profile with sufficiently large discount factor
    - Describes the set of payoffs that can result from Nash strategies in repeated games
    - The convex hull of player strategies describes feasible region
- Grim trigger
    - Captures a severe threat
    - Default to cooperation, if opponent ever defects, defect forever
    - Grim trigger is implausible in Prisoner's Dilemma, 
    - It is not subgame perfect against TfT (even though they are a NE)
- Pavlov
    - Start with cooperating
    - Cooperate if both players agree, defect if they disagree
    - Pavlov vs. Pavlov is NE **and** subgame perfect
    - Humans tend to act this way

### Computational Folk Theorem
- Can build Pavlov-like machines for any game and construct subgame perfect NE for any game in polynomial time

### Stochastic games
- Generalize MDP and repeated games
- MDP : RL :: stochastic game : multi-agent RL
- Zero-sum
    - Value iteration works
    - Minimax-Q works
    - Unique solution to Q*
    - Policies can be computed independently for each player
    - Update efficient
    - Q-functions are sufficient to specify policy
- General-sum
    - All of the above fail
    - Possible ideas: cheaptalk->correlated equilibria, cognitive hierarchy->best repsonses, side payments (coco values)

### Recap
- Iterated Prisoner's Dilemma is an example of a repeated game
    - We can encourage cooperation in repeated games 
    - New NE appear in repeated games
    - Folk Theorem (threats)
    - Equilibria can be subgame perfect 
    - If a game is not subgame perfect, threats can be implausible
    - Computational folk theorem
- Stochastic games generalize MDPs and repeated games
    - Minimax-Q works
    - Nash-Q doesn't work
    
