Bellman equation is defined as follows.

$$
v_{\pi}(s) \doteq \mathbb{E}_{\pi} \left[ G_t | S_t = s \right]
$$

$$
v_{\pi}(s) \doteq \sum_{a} \pi(a|s) \sum_{s'} \sum_{r} p(s', r | s, a) \left[ R_{t+1} + \gamma v_{\pi} (s') \right]
$$
