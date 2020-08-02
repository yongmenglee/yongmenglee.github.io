---
title: "Actor-Critic with Linear Function Approximation and Softmax Policy Parameterization: How to Prove the Eligibility Vector?"
tag: formula
show_edit_on_github: false
---

In this article, we will do an exercise to prove the eligibility vector of a policy parameterization using the softmax in action preferences with linear function approximations.

<!--more-->

## Actor-Critic with Linear Function Approximation and Softmax Policy Parameterization

The original exercise is extracted from \[1\] as follows:

*In Section 13.1 we considered policy parameterizations using the soft-max in action preferences (13.2) with linear action preferences (13.3). For this parameterization, prove that the eligibility vector is*

$$
\nabla \ln \pi \left(a \vert s, \mathbf{\theta} \right) =
\mathbf{x}_h (a, s) - \sum_{b \in \mathcal{S}} \pi (b \vert s, \mathbf{\theta}) \mathbf{x}_h (b, s)
$$

*using the definitions and elementary calculus.*

The equations (13.2) and (13.3) are, respectively

$$
\pi (a \vert s, \mathbf{\theta}) = \frac
    {e^{h(s, a, \mathbf{\theta})}}
    {\sum_{b \in \mathcal{A}} e^{h(s, b, \mathbf{\theta})}}
$$

and 

$$
h(s, a, \mathbf{\theta}) = \mathbf{\theta}^T \mathbf{x}_h (s, a)
$$

which will be further discussed in the following sections.

Before getting started with the proving, we need to get familiar with several concepts applied for the proving.

## Recap: Quotient Rule

Quotient Rule of calculus.

$$
\nabla \left[\frac{f(x)}{g(x)}\right] = \frac{g(x) \nabla f(x) - f(x) \nabla g(x)}{\left(g(x)\right)^2}
$$

The Quotient rule is a simple yet powerful technique to solve many problems in calculus. A simple example which applies the Quotient Rule of calculus is as follows:

**Find $\nabla \left[ (x^2 + x - 6)/(x - 2) \right]$.**

We denote by $f(x)$ and $g(x)$, the numerator and denominator respectively.
$$
\begin{align}
f(x) &= x^2 + x - 6
\\
g(x) &= x - 2
\end{align}
$$

Therefore,
$$
\begin{align}
\nabla f(x) &= 2x + 1
\\
\nabla g(x) &= 1
\end{align}
$$

By applying the Quotient Rule:
$$
\begin{align}
\nabla \left( \frac{x^2+x-6}{x-2} \right)
&= \frac{(x-2)(2x+1) - (x^2+x-6)(1)}{(x-2)^2}
\\
&= \frac{(2x^2-3x-2) - (x^2+x-6)}{(x-2)^2}
\\
&= \frac{x^2-4x+4}{(x-2)^2}
\\
&= \frac{(x-2)^2}{(x-2)^2}
\\
&= 1
\end{align}
$$

In fact, one can always simplify the expression $(x^2 + x - 6)/(x - 2)$ as $x-3$, therefore $\nabla (x-3) = 1$.


## Action Preference

In general, an action preference function, $h$ is defined as a function with respect to $s$, current state, $a$, selected action, and $\mathbf{\theta}$, parameter of a policy, as follows:

$$
h(s, a, \mathbf{\theta}), s \in \mathcal{S}, 
a \in \mathcal{A}, \mathbf{\theta} \in \mathbb{R}^{\left|\mathcal{S}\right| \times \left|\mathcal{A}\right|}
$$

The rationale behind the action preference is to assign different preference values to each possible action for every state, such that these values correspond to the probability of one action taken by an agent at any given state following a policy, $\pi$. Note that an action preference can be either positive or negative value, in which, a more positive action preference value indicates that an action is more strongly preferred by the agent at a given state, whereas a more negative action preference value indicates that, for the same state, the agent is more adverse to the action.

For our purpose, we define the action preference as a linear function. However, it should be noted that an action preference function can be defined as any function, including polynomial functions. Our action preference function, $h$, is defined as follows:

$$
h(s, a, \mathbf{\theta}) = \mathbf{\theta}^T \mathbf{x}_h (s, a)
$$

where $\mathbf{x}_h (s, a)$ is the feature vector for current state, $s$ and selected action, $a$.

## Softmax Policy

Again for our purpose, the chosen policy parameterization method is **softmax policy**. A softmax policy is very commonly picked in policy parameterization. It is not only simple and intuitive, but also ensures that our policy with finite set of discrete actions always obeys the two fundamental rules of a stochastic policy.

**Rule 1: The probability of an action at any given state following policy $\pi$ must be greater than 0.**

During a policy parameterization, the policy must ensure that every action at a given state must be greater than 0 to encourage exploration of the agent. The policy, $\pi$, is defined as a function with respect to $a$, the action for $s$ and $\mathbf{\theta}$, the given state and the parameter, respectively.

$$
\pi \left(a \vert s, \mathbf{\theta} \right) > 0
$$

One way to ensure that the policy is always positive is to define the policy as a natural exponential function of the action preference. This means, we specify $x = h(s, a, \mathbf{\theta})$ in the natural exponential function $f(x) = e^x$.

$$
e^{h(s, a, \mathbf{\theta})} > 0
$$

With this definition, the policy function $\pi$ is guaranteed to be positive. However, we cannot simply define our policy function as follows:

$$
\pi \left(a \vert s, \mathbf{\theta} \right) \neq e^{h(s, a, \mathbf{\theta})}
$$

This might violate the second rule of a stochastic policy.

**Rule 2: The sum of probability of all actions at any given state following policy $\pi$ must be equal to 1.**

The second rule of a stochastic policy is defined as follows: 

$$
\sum_{a \in \mathcal{A}} \pi \left(a \vert s, \mathbf{\theta} \right) = 1
$$

The range of a natural exponential function is $(0, \infty)$. Therefore, if the policy is simply defined as the natural exponential function of the action preference, the chance that the sum of probability of all actions exceeds 1 is high.

Nonetheless, we can perform a simple trick to satisfy this rule. We normalize the value of the natural exponential function of the action preference by the total preference values over all actions at a given state.

To define a policy function which satisfies the second rule, let us start with the following expression.

$$
\frac
    {\sum_{a \in \mathcal{A}} e^{h(s, a, \mathbf{\theta})}}
    {\sum_{b \in \mathcal{A}} e^{h(s, b, \mathbf{\theta})}}
= 1
$$

We can then rearrange the expression from above.

$$
\sum_{a \in \mathcal{A}}
\left(
\frac
    {e^{h(s, a, \mathbf{\theta})}}
    {\sum_{b \in \mathcal{A}} e^{h(s, b, \mathbf{\theta})}}
\right)
= 1
$$

The term in bracket is the desired policy function, which also satisfies the first rule of stochastic policy. Note that the denominator becomes the *normalizer* to the original natural exponential function of the action preferences.

$$
\pi (a \vert s, \mathbf{\theta}) = \frac
    {e^{h(s, a, \mathbf{\theta})}}
    {\sum_{b \in \mathcal{A}} e^{h(s, b, \mathbf{\theta})}}
$$

## The Prove

To organize the presentation of our content, in this section, we denote by $H(a)$ and $H(b)$, respectively

$$
\begin{align}
H(a) &= e^{h(s, a, \mathbf{\theta})}
\\ 
H(b) &= e^{h(s, b, \mathbf{\theta})}
\end{align}
$$

for $a, b \in \mathcal{A}$.

With all the prerequisite knowledge and definitions above, we can start off with the proving part. Recall that the equation is given as follows:

$$
\nabla \ln \pi \left(a \vert s, \mathbf{\theta} \right) =
\mathbf{x}_h (a, s) - \sum_{b \in \mathcal{S}} \pi (b \vert s, \mathbf{\theta}) \mathbf{x}_h (b, s)
$$

With elementary knowledge in calculus, we can rewrite the left hand side expression from the equation as follows:

$$
\nabla \ln \pi \left(a \vert s, \mathbf{\theta} \right) =
\frac
    {\nabla \pi \left(a \vert s, \mathbf{\theta} \right)}
    {\pi \left(a \vert s, \mathbf{\theta} \right)}
$$

We start with the numerator: $\nabla \pi \left(a \vert s, \mathbf{\theta} \right)$. First, we denote the numerator and denominator of our Softmax policy as follows:

$$
\begin{align}
f(x) &= H(a)
\\
g(x) &= \sum_{b \in \mathcal{A}} H(b)
\end{align}
$$

Since $H(a) = \mathbf{\theta}^T \mathbf{x}_h (s, a)$, we can deduce that $\nabla H(a) = \mathbf{x}_h (s, a)$.

We can now define $\nabla f(x)$ and $\nabla g(x)$ respectively, as follows
$$
\begin{align}
\nabla f(x) &= H(a) \mathbf{x}_h (s, a)
\\
\nabla g(x) &= \sum_{b \in \mathcal{A}} H(b) \mathbf{x}_h (s, b)
\end{align}
$$

Remember the quotient rule that we have defined earlier?

$$
\begin{align}
\nabla \pi (a \vert s, \mathbf{\theta}) 
&= \frac{g(x) \nabla f(x) - f(x) \nabla g(x)}{\left(g(x)\right)^2}
\\
&= \frac
    {\sum_{b \in \mathcal{A}} H(b) H(a) \mathbf{x}_h (s, a)
        - H(a) \sum_{b \in \mathcal{A}} H(b) \mathbf{x}_h (s, b)}
    {\left[ \sum_{b \in \mathcal{A}} H(b) \right]^2}
\end{align}
$$

Substitute the equation into $\nabla \ln \pi \left(a \vert s, \mathbf{\theta} \right)$:
$$
\begin{align}
\nabla \ln \pi \left(a \vert s, \mathbf{\theta} \right)
&= \frac
    {\sum_{b \in \mathcal{A}} H(b) H(a) \mathbf{x}_h (s, a)
        - H(a) \sum_{b \in \mathcal{A}} H(b) \mathbf{x}_h (s, b)}
    {\left[ \sum_{b \in \mathcal{A}} H(b) \right]^2}
    \times
    \frac{\sum_{b \in \mathcal{A}} H(b)}{H(a)}
\\
&= \frac
    {\sum_{b \in \mathcal{A}} H(b) \mathbf{x}_h (s, a)
        - \sum_{b \in \mathcal{A}} H(b) \mathbf{x}_h (s, b)}
    {\sum_{b \in \mathcal{A}} e^{ h(s, b, \mathbf{\theta})}}
    \times \frac{H(a)}{\sum_{b \in \mathcal{A}} H(b)}
    \times \frac{\sum_{b \in \mathcal{A}} H(b)}{H(a)}
\\
&= \frac
    {\sum_{b \in \mathcal{A}} H(b) \mathbf{x}_h (s, a)
        - \sum_{b \in \mathcal{A}} H(b) \mathbf{x}_h (s, b)}
    {\sum_{b \in \mathcal{A}} H(b)}
\\
&= \frac
    {\sum_{b \in \mathcal{A}} H(b)}
    {\sum_{b \in \mathcal{A}} H(b)}
    \mathbf{x}_h (s, a)
    -
    \sum_{b \in \mathcal{A}} 
    \frac{H(b)}{\sum_{b \in \mathcal{A}} H(b)}
    \mathbf{x}_h (s, b)
\\
&= \mathbf{x}_h (s, a) - \sum_{b \in \mathcal{A}} \pi (b \vert s, \mathbf{\theta}) \mathbf{x}_h (s, b)
\end{align}
$$

## References

1. R. S. Sutton and A. G. Barto, *Reinforcement learning: an introduction.* Cambridge, MA: The MIT Press, 2018.