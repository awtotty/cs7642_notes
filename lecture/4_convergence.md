## Convergence

### RL for control

### Bellman operator
- $[BQ](s,a) = R(s,a) + \gamma \sum_{s'} {T(s,a,s') \max_{a'} Q(s',a')}$
- Then the Bellman equation can be expressed as $Q^* = BQ^*$
- Value iteration can be expressed as $Q_t = BQ_{t-1}$
- Contaction mapping
    - With $B$ as an operator, if $\forall F,G$ and some $0 \leq \gamma < 1$, $||BF - BG||_{\infty} \leq \gamma ||F - G||_{\infty}$, then $B$ is a contraction mapping
    - $||Q||_{\infty} = \max_{s,a} |Q(s,a)|$
    - Kind of like $B$ shrinks the difference between to value functions (applying the operator brings $F$ and $G$ values closer together)
    - **Why is $\gamma$ needed here?** Why is this not the same as $||BF - BG||_{\infty} < ||F - G||_{\infty}$
    - Contraction mappings are useful because: 
        1. $Q^* = BQ^*$ has a unique solution
        2. $Q_t = BQ_{t-1}$ converges to $Q^*$
- The Bellman operator is a contraction mapping
- max is a non-expansion, $|\max_a f(a) - \max_a g(a)| \leq \max_a |f(a)-g(a)|$ (note, these are 3 diff $a$ values)
    - the proof of this is cool


