---
title: "Deterministic Continuous Review Inventory Model: The Formula"
tag: formula
show_edit_on_github: false
---

In this article, we will define the formula for EOQ (Economic Order uantity) Model with and without planned shorted, and perform the derivation to the formula.

<!--more-->

## EOQ Model: No Planned Shortages

Before formulating the model, we define some variables that is required. Given that

- $Q$ = order quantity, in unit
- $K$ = setup cost per batch, in \$
- $c$ = unit cost, in \$ per unit
- $h$ = holding cost, in \$ per unit per unit time
- $d$ = ordering rate, in unit per unit time

The cycle length is $\frac{Q}{d}$ unit time.

Therefore, the production or ordering cost per cycle is $K + cQ$ in \$.

Assume that the average inventory level during a cycle is $\frac{Q+0}{2} = \frac{Q}{2}$ units, and its corresponding holding cost is $\frac{hQ}{2}$ in \$ per unit time.

Therefore, the holding cost per cycle is, in \$,

$$
\frac{hQ}{2} \times \frac{Q}{d} = \frac{hQ^2}{2d}
$$

Then, the total cost per cycle is, $K + cQ + \frac{hQ^2}{2d}$, in \$.

We denote by $T$, the total cost (in \$) per unit time, as follows:

$$
T = \left( K + cQ + \frac{hQ^2}{2d} \right) \times \frac{1}{Q/d}
= \frac{dK}{Q} + cd + \frac{hQ}{2}
$$

We denote by $Q^{\ast}$, the value of $Q$ that minimizes $T$ as follows:

$$
Q^{\ast} = \sqrt{\frac{2dK}{h}}
$$


### $Q^{\ast}$: The Derivation

Given that

$$
T = \frac{dK}{Q} + cd + \frac{hQ}{2} \notag
$$

we differentiate $T$ with respect to $Q$ as follows:

$$
\frac{dT}{dQ} = -\frac{dK}{Q^2} + \frac{h}{2}
$$

To find $Q$ that minimizes $T$, we want to find the value of $Q^{\ast}$ such that $\frac{dT}{dQ} = 0$. Hence,

$$
\begin{align}
-\frac{dK}{(Q^{\ast})^2} + \frac{h}{2} &= 0
\\
(Q^{\ast})^2 &= \frac{2dK}{h} \notag
\\
Q^{\ast} &= \sqrt{\frac{2dK}{h} \notag}
\end{align}
$$

The value of $Q^{\ast}$ answers the following question:

> How many products to produce in each batch of order?

Next, we will look at the derivation of $t^{\ast}$, the optimal cycle length.

### $t^{\ast}$: The Derivation

From earlier section, we know that the cycle length is $t = \frac{Q}{d}$, therefore

$$
t^{\ast} = \frac{Q^{\ast}}{d} = \sqrt{\frac{2K}{dh}}
$$

The value of $t^{\ast}$ answers the following question:

> When to make the order?

The formula for $Q^{\ast}$ and $t^{\ast}$ above enables us to calculate the optimal unit of product to order at an optimal time. However, this is only the special case where **planned shortage is not allowed**.

So, what will happen if we change the assumption: to allow planned shortage?

## EOQ Model: With Planned Shortages

Similar to previous section, we define some variables that is required. Given that

- $Q$ = order quantity, in unit
- $K$ = setup cost per batch, in \$
- $c$ = unit cost, in \$ per unit
- $h$ = holding cost, in \$ per unit per unit time
- $d$ = ordering rate, in unit per unit time
- $p$ = *(new)* shortage cost, in \$ per unit per unit time
- $S$ = *(new)* inventory level (in unit) just after a batch of $Q$ units are added to inventory
- $Q - S$ = *(new)* shortage in inventory (in unit) just before a batch of $Q$ units are added to inventory.

Again, the cycle length is $\frac{Q}{d}$ unit of time.

Therefore, the production or ordering cost per cycle is $K + cQ$, in \$.

Assume that the average inventory level during a cycle is $\frac{S+0}{2} = \frac{S}{2}$ units (we use $S$ instead of $Q$ because $S$ is the quantity of product in the inventory), and its corresponding holding cost is $\frac{hS}{2}$ in \$ per unit time.

Therefore, the holding cost per cycle is, in \$,

$$
\frac{hS}{2} \times \frac{S}{d} = \frac{hS^2}{2d}
$$

Similarly, assume that the average shortage during a cycle is $\frac{Q-S}{2} $ units, and its corresponding shortage cost is $\frac{p(Q-S)}{2}$ in \$ per unit time.

Therefore, the holding cost per cycle is, in \$,

$$
\frac{p(Q-S)}{2} \times \frac{Q-S}{d} = \frac{p(Q-S)^2}{2d}
$$

Here, the total cost per cycle is, $K + cQ + \frac{hS^2}{2d} + \frac{p(Q-S)^2}{2d}$, in \$.

We denote by $T$, the total cost (in \$) per unit time, as follows:

$$
\begin{align}
T &= \left( K + cQ + \frac{hS^2}{2d} + \frac{p(Q-S)^2}{2d} \right) \times \frac{1}{Q/d} \notag
\\
T &= \frac{dK}{Q} + cd + \frac{hS^2}{2Q} + \frac{p(Q-S)^2}{2Q} \notag
\\
&= \frac{dK}{Q} + cd + \frac{hS^2}{2Q} + \frac{pQ^2 - 2pQS + p^2}{2Q} \notag
\\
&= \frac{dK}{Q} + cd + \frac{(h+p)S^2}{2Q} + \frac{pQ}{2} - pS
\end{align}
$$

### $Q^{\ast}$ and $S^{\ast}$: The Derivation

Given that

$$
T = \frac{dK}{Q} + cd + \frac{(h+p)S^2}{2Q} + \frac{pQ}{2} - pS \notag
$$

First, we differentiate $T$ with respect to $Q$:

$$
\begin{align}
\frac{\partial{T}}{\partial{Q}} 
&= -\frac{dK}{Q^2} - \frac{(h+p)S^2}{2Q^2} + \frac{p}{2} \notag
\\
&= -\frac{2dK + (h+p)S^2}{2Q^2} + \frac{p}{2}
\end{align}
$$

Next, we differentiate $T$ with respect to $S$:

$$
\frac{\partial{T}}{\partial{S}} 
= -p + \frac{(h+p)S}{Q}
$$

To find $Q$ and $S$ that minimize $T$, we want to find the value of $Q^{\ast}$ and $S^{\ast}$ such that $\frac{\partial{T}}{\partial{Q}} = 0$ and $\frac{\partial{T}}{\partial{S}} = 0$ respectively. Hence,

$$
\begin{align}
-\frac{2dK + (h+p)(S^{\ast})^2}{2(Q^{\ast})^2} + \frac{p}{2} &= 0
\\
\frac{2dK + (h+p)(S^{\ast})^2}{(Q^{\ast})^2} &= p
\\
\frac{2dK + (h+p)(S^{\ast})^2}{p} &= (Q^{\ast})^2 \label{eq:eqone}
\end{align}
$$

and

$$
\begin{align}
-p + \frac{(h+p)S^{\ast}}{Q^{\ast}} &= 0
\\
\frac{(h+p)S^{\ast}}{Q^{\ast}} &= p
\\
Q^{\ast} &= \frac{(h+p)}{p}S^{\ast} \label{eq:eqtwo}
\end{align}
$$

Next, we substitute $\eqref{eq:eqtwo}$ into $\eqref{eq:eqone}$:

$$
\begin{align}
\frac{2dK + (h+p)(S^{\ast})^2}{p}
&= \left( \frac{(h+p)}{p}S^{\ast} \right)^2
\\
\frac{2dK}{p} + \frac{hp+p}{p}(S^{\ast})^2
&= \left( \frac{(h+p)}{p} \right)^2 (S^{\ast})^2
\\
\left[ \left( \frac{(h+p)}{p} \right)^2 (S^{\ast})^2 - (h+p) \right] (S^{\ast})^2
&= 2dK
\\
\frac{h}{p}(h+p)(S^{\ast})^2 &= 2dK
\\
(S^{\ast})^2 &= \frac{2dK}{h} \cdot \frac{p}{p+h}
\\
S^{\ast} &= \sqrt{\frac{2dK}{h}} \cdot \sqrt{\frac{p}{p+h}} \label{eq:eqthree}
\end{align}
$$

Finally, we substitute $\eqref{eq:eqthree}$ into $\eqref{eq:eqtwo}$:

$$
\begin{align}
Q^{\ast} &= \frac{(h+p)}{p} \sqrt{\frac{2dK}{h}} \cdot \sqrt{\frac{p}{p+h}}
\\
&= \sqrt{\frac{2dK}{h}} \cdot \sqrt{\frac{p+h}{p}}
\end{align}
$$

In summary, the values of $Q^{\ast}$ and $S^{\ast}$ can be calculated using the formula as follows:

$$
\begin{align}
Q^{\ast} &= \sqrt{\frac{2dK}{h}} \cdot \sqrt{\frac{p+h}{p}} \notag
\\
S^{\ast} &= \sqrt{\frac{2dK}{h}} \cdot \sqrt{\frac{p}{p+h}} \notag
\end{align}
$$

We can also deduce $Q^{\ast} - S^{\ast}$ as follows:

$$
\begin{align}
Q^{\ast} - S^{\ast}
&= \sqrt{\frac{2dK}{h}} \cdot \sqrt{\frac{p+h}{p}}
- \sqrt{\frac{2dK}{h}} \cdot \sqrt{\frac{p}{p+h}} \notag
\\
&= \sqrt{\frac{2dK}{h}} \cdot 
\left( \sqrt{\frac{p+h}{p}} - \sqrt{\frac{p}{p+h}} \right} \notag
\\
&= \sqrt{\frac{2dK}{h}} \cdot 
\left( \sqrt{\frac{(p+h)^2}{p(p+h)}} - \sqrt{\frac{p^2}{p(p+h)}} \right} \notag
\\
&= \sqrt{\frac{2dK}{h}} \cdot 
\left( \frac{p+h}{\sqrt{p(p+h)}} - \frac{p}{\sqrt{p(p+h)}} \right} \notag
\\
&= \sqrt{\frac{2dK}{h}} \cdot \frac{h}{\sqrt{p(p+h)}} \notag
\\
&= \sqrt{\frac{2dK}{p}} \cdot \sqrt{\frac{h}{p(p+h)}}
\end{align}
$$

### $t^{\ast}$: The Derivation

We would also like to know when to make the order, therefore, the time $t^{\ast}$ is given by
$$
t^{\ast} = \frac{Q^{\ast}}{d} = \sqrt{\frac{2K}{dh}} \cdot \sqrt{\frac{p+h}{p}}
$$