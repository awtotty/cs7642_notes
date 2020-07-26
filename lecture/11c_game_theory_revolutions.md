## Game Theory 3 

### Correlated equilibria
- Agents have shared source of randomization (oracle that recommends strategy)
- Can be found in polynomial time
- All mixed NE are CE 
- All convex combinations of mixed NE are CE

### Coco values
- = cooperative-competitive values
- Players can offer side payments to encourage cooperation from opponent
- Coco value formal defn: 
    - Let $U$ be payoffs to player 1, $\overline{U}$ be payoffs to player 2.  
    - Coco($U,\overline{U}$) = maxmax($\frac{U+\overline{U}}{2}$) + minimax($\frac{U-\overline{U}}{2}$) = cooperative max + competitive max
- Coco properties
    - Efficiently computable
    - Utility maximizing
    - Decomposes game into sum of two games (cooperative, competitive)
    - Unique value
    - Can be extended to stochastic games (Coco-Q [convergese despite non-expansion])
    - Not necessarily an equilibrium 
    - Doesn't generalize beyond 2 players

### Mechanism design
- Design games or extensions of games to produce desired behavior
- Peer teaching
    - Very cool work
    - Student tries to maximize correct answers, teacher tries to find place in spectrum of questions where student will get slightly harder problems wrong and slightly easier problems correct
- King Solomon
    - Fees for liar 

### Recap
- Solution concepts: 
    - Correlated equilibria
        - Shared source of randomization
        - Traffic light example
    - Coco values
        - Binding side payments
        - Encourages Pareto optimal actions
    - NE 
    - Subgame perfect
- Mechanism design: designing games or extensions of games to produce desired behavior
    - Peer teaching (J. Pollack's work)
    - King Solomon
- All of these cases (except NE) show extensions of games to yield desired behavior