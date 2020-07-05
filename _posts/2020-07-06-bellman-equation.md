The state-value function is defined as follows.

$$ v_{\pi}(s) \doteq \mathbb{E}_{\pi} \left[ G_t | S_t = s \right] $$

The Bellman equation for the state-value function is defined as follows.

$$ 
v_{\pi}(s) \doteq \sum_{a} \pi(a|s) \sum_{s'} \sum_{r} p(s', r | s, a) \left[ R_{t+1} + \gamma v_{\pi} (s') \right] 
$$

**How to convert state-value function into Bellman equation?**

### The derivation

Recall that $G_t$ is the sum of future rewards, i.e.
$$
G_t = \sum_{k=0}^{\infty} \gamma^k R{k+t+1}
$$

where $\gamma$ is the discounted value and $R_n$ is the reward at state $n$.

Therefore, 

$$
begin{align}
v_{\pi}(s) &\doteq \mathbb{E}_{\pi} \left[ G_t | S_t = s \right]
\\
&= \mathbb{E}_{\pi} \left[ R_{t+1} + \gamma G_{t+1} | S_t = s \right]
\\
&= \mathbb{E}_{\pi} \left[ R_{t+1} \right] + \mathbb{E}_{\pi} \left[ \gamma G_{t+1} | S_t = s \right]
end{align}
$$