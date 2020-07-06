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

We denote by $Q^*$, the value of $Q$ that minimizes $T$ as follows:

$$
Q* = \sqrt{\frac{2dK}{h}}
$$


### $Q^*$: The Derivation

Given that

$$
T = \frac{dK}{Q} + cd + \frac{hQ}{2} \notag
$$

we differentiate $T$ with respect to $Q$ as follows:

$$
\frac{dT}{dQ} = -\frac{dK}{Q^2} + \frac{h}{2}
$$

To find $Q$ that minimizes $T$, we want to find the value of $Q^*$ so that $\frac{dT}{dQ} = 0$. Hence,

$$
\begin{align}
-\frac{dK}{(Q^*)^2} + \frac{h}{2} &= 0
\\
(Q^*)^2 &= \frac{2dK}{h} \notag
\\
Q^* &= \sqrt{\frac{2dK}{h} \notag}
\end{align}
$$

The value of $Q^*$ answers the following question:

> How many products to produce in each batch of order?

Next, we will look at the derivation of $t^*$, the optimal cycle length.

### $t^*$: The Derivation

From earlier section, we know that the cycle length is $t = \frac{Q}{d}$, therefore

$$
t^* = \frac{Q^*}{d} = \sqrt{\frac{2K}{dh}}
$$

The value of $t^*$ answers the following question:

> When to make the order?

The formula above enables us to calculate the optimal unit of product to order at an optimal time. However, this is only the special case where **planned shortage is not allowed**.

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
The cycle length is $\frac{Q}{d}$ unit time.