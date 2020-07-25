---
title: "Solving a Polynomial Equation Raised to the Power of a Polynomial Equation?"
tag: formula
show_edit_on_github: false
---

In this article, we will discuss about how to solve a polynomial equation. This equation is a quadratic equation raised to the power of another quadratic equation.

<!--more-->

## A Quadratic Equation Raised to the Power of A Quadratic Equation

Imagine this, there is a quadratic equation raised to the power of another quadratic equation. You might think, what on earth is this? It must be very insane! How can we solve this kind of equation?

Well, believe it or not? The trick is indeed very easy.

Without further ado, here is the equation:

$$
\left( x^2 - 7x + 11 \right)^{(x^2 - 13x + 42)} = 1 \label{eq:quad_power_quad}
$$

The goal is to find the value of $x$ which satisfies the equation above.

*Okay, fine. Now, where should I start from?*

## Case 1: $a^0 = 1$

This is a very fundamental concept in high school maths. It should look familiar: any number, $a$ raised to the power of $0$ equals to $1$. Looking back at our equation, we can quickly recognize that the value on the right hand side is $1$.

Therefore, we make the following substitution with the information provided:

$$
\begin{align}
a &= x^2 - 7x + 11 \notag
\\
0 &= x^2 - 13x + 42 \label{eq:power0}
\end{align}
$$

And guess what? We can solve $\eqref{eq:power0}$ right away! 😀

Let's move on...

$$
\begin{align}
x^2 - 13x + 42 &= 0 \notag
\\
(x - 6)(x - 7) &= 0 \notag
\\
x &= 6, 7
\end{align}
$$

Good start! We have earned our credit by obtaining our first two values of $x$.

**But, wait! These are only the first two values of $x$. Then, what's next?**

Be patient, let's keep calm and proceed to the second case! ☕

## Case 2: $1^b = 1$

Again, this should be another fundamental concept taught in high school maths class: $1$ raised to the power of any number, $b$ remains as $1$. Similarly, we can make the following substitution with the information provided:

$$
\begin{align}
1 &= x^2 - 7x + 11 \label{eq:equal_to_1}
\\
b &= x^2 - 13x + 42 \notag
\end{align}
$$

At this point, the next step should look easy.

$$
\begin{align}
x^2 - 7x + 11 &= 1 \notag
\\
x^2 - 7x + 10 &= 0 \notag
\\
(x - 2)(x - 5) &= 0 \notag
\\
x &= 2, 5
\end{align}
$$

Voila! We have earned another credit by obtaining another two values of $x$ that satisfies $\eqref{quad_power_quad}$.

To summarize, these are the solutions for now: $x = {2, 5, 6, 7}$

You might think...

*So far, we already have all possible cases covered, don't we?*

<details>
  <summary>Well, think again. 🙂</summary>
  
  ## Heading
  1. A numbered
  2. list
    * With some
    * Sub bullets
</details>


## References


