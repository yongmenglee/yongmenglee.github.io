---
title: "Bellman's Equation"
tag: formula
show_edit_on_github: false
---

In this article, we will perform the derivation of Bellman's equation for both state-value and action-value functions.

<!--more-->

## The State-Value Function

The state-value function for a given policy, $\pi$, denoted by $v_{\pi}(s)$ is defined as follows.

$$
v_{\pi}(s) \doteq \mathbb{E}_{\pi} \left[ G_t | S_t = s \right] \notag
$$

where

- $\pi$: a given policy applied by the agent to interact with the environment,
- $s$: current state on the environment, and
- $G_t$: the return, which is the sum over the future rewards.

Note that $G_t$ is a random variable, therefore the state-value function is defined as the expected return of the agent for a given state $s$.

The Bellman equation for the state-value function is defined as follows.

$$ 
v_{\pi}(s) \doteq \sum_{a} \pi(a|s) \sum_{s'} \sum_{r} p(s', r | s, a) \left[ r + \gamma v_{\pi} (s') \right] \notag
$$

Notice how the state-value function for the current state $v_{\pi}(s)$ is a recursive function, depending on the state-value function for the next state $v_{\pi}(s')$ on the right hand side.

**How to convert state-value function into Bellman equation?**

### The Derivation

Recall that $G_t$ is the sum of future rewards, i.e.

$$
\begin{align}
G_t &= \sum_{k=0}^{\infty} \gamma^k R_{k+t+1} \notag
\\
&= R_{t+1} + \gamma \sum_{k=1}^{\infty} \gamma^k R_{k+t+1} \notag
\\
&= R_{t+1} + \gamma G_{t+1} \notag
\end{align}
$$

where $\gamma$ is the discounted value and $R_t$ is the reward at time $t$.

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


## The Action-Value Function

An action-value function describes what happens when the agent selects the particular action $a$, and then follow the policy $\pi$. The action-value function, denoted by $q_{\pi}(s, a)$ is defined as follows.

$$
q_{\pi}(s, a) \doteq \mathbb{E}_{\pi} \left[ G_t | S_t = s , A_t = a\right] \notag
$$

where

- $\pi$: a given policy applied by the agent to interact with the environment,
- $s$: current state on the environment,
- $a$: the selection action for current state $s$, and
- $G_t$: the return, which is the sum over the future rewards.

Similarly, the action-value function is defined as the expected return of the agent for selected action $a$ and given state $s$.

The Bellman equation for the action-value function is defined as follows.

$$ 
q_{\pi}(s, a) \doteq \sum_{s'} \sum_{r} p(s', r | s, a) \left[ r + \gamma \sum_{a} \pi(a'|s') q_{\pi} (s', a') \right] \notag
$$

Notice how the action-value function for the current state and action $q_{\pi}(s, a)$ is also a recursive function, depending on the action-value function for the next state $q_{\pi}(s', a')$ on the right hand side.

## References

1. R. S. Sutton and A. G. Barto, *Reinforcement learning: an introduction.* Cambridge, MA: The MIT Press, 2018.
