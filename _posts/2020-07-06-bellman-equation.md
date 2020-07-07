---
title: "Bellman Equation"
tag: formula
show_edit_on_github: false
---

The state-value function is defined as follows.

$$ v_{\pi}(s) \doteq \mathbb{E}_{\pi} \left[ G_t | S_t = s \right] \notag $$

The Bellman equation for the state-value function is defined as follows.

$$ 
v_{\pi}(s) \doteq \sum_{a} \pi(a|s) \sum_{s'} \sum_{r} p(s', r | s, a) \left[ r + \gamma v_{\pi} (s') \right] \notag
$$

**How to convert state-value function into Bellman equation?**

## The derivation

Recall that $G_t$ is the sum of future rewards, i.e.

$$
G_t = \sum_{k=0}^{\infty} \gamma^k R_{k+t+1} \notag
$$

where $\gamma$ is the discounted value and $R_n$ is the reward at state $n$.

Therefore, 

$$
\begin{align}
v_{\pi}(s) &\doteq \mathbb{E}_{\pi} \left[ G_t | S_t = s \right]
\\
&= \mathbb{E}_{\pi} \left[ R_{t+1} + \gamma G_{t+1} | S_t = s \right]
\\
&= \mathbb{E}_{\pi} \left[ R_{t+1} | S_t = s \right] + \gamma \mathbb{E}_{\pi} \left[ G_{t+1} | S_t = s \right]
\end{align}
$$

Here, we separate the right hand side of the equation into two parts:

$$
\begin{align}
\mathbb{E}_{\pi} \left[ R_{t+1} | S_t = s \right] 
&= \sum_r p(R_{t+1} = r | S_t = s) \cdot r
\\
&= \sum_r p(r|s) \cdot r
\\
&= \sum_a \sum_r p(a,r|s) \cdot r
\\
&= \sum_a \sum_r \pi(a|s) \cdot p(r|s,a) \cdot r
\\
&= \sum_a \pi(a|s) \sum_{s'} \sum_r p(s',r|s,a) \cdot r
\end{align}
$$

and

$$
\begin{align}
\mathbb{E}_{\pi} \left[ G_{t+1} | S_t = s \right] 
&= \mathbb{E}_{\pi} \left[ \mathbb{E}_{\pi} \left[ G_{t+1} | S_t = s , S_{t+1} = s' \right] \right]
\\
&= \mathbb{E}_{\pi} \left[ v_{\pi}(s') | S_t = s \right]
\\
&= \sum_{s'} p(S_{t+1} = s' | S_t = s) \cdot v_{\pi}(s')
\\
&= \sum_{s'} p(s'|s) \cdot v_{\pi}(s')
\\
&= \sum_a \sum_{s'} p(s',a|s) \cdot v_{\pi}(s')
\\
&= \sum_a \pi(a|s) \sum_{s'} p(s'|s,a) \cdot v_{\pi}(s')
\\
&= \sum_a \pi(a|s) \sum_{s'} \sum_r p(s',r|s,a) \cdot v_{\pi}(s')
\end{align}
$$

Now, we merge the two parts on the right hand side back to the state-value function.

$$
\begin{align}

v_{\pi}(s) &\doteq \mathbb{E}_{\pi} \left[ G_t | S_t = s \right]
\\
&= \sum_a \pi(a|s) \sum_{s'} \sum_r p(s',r|a,s) \cdot r
+ \gamma \sum_a \pi(a|s) \sum_{s'} \sum_r p(s',r|s,a) \cdot v_{\pi}(s')
\\
&= \sum_a \pi(a|s) \sum_{s'} \sum_r p(s',r|a,s) \left[ r + \gamma v_{\pi}(s') \right]
\end{align}
$$

## References

1. R. S. Sutton and A. G. Barto, Reinforcement learning: an introduction. Cambridge, MA: The MIT Press, 2018.
