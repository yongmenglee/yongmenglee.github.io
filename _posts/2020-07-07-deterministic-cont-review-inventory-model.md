---
title: "Deterministic Continuous Review Inventory Model: The Formula"
tag: formula
show_edit_on_github: false
---

In this article, we will define the formula for EOQ (Economic Order uantity) Model with and without planned shorted, and perform the derivation to the formula.

<!--more-->

## EOQ Model: No Planned Shortages

Given that

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
