---
title: "Fourier Series: How to Solve the Fourier Coefficients?"
tag: formula
show_edit_on_github: false
---

In this article, we will be going through the process of solving the coefficients of Fourier Series.

<!--more-->

## Fourier Series: Brief Introduction

In simple language, a periodic function, $f(x)$, is defined as a function in which, a value $P$ exists such that $f(P + x) = f(x)$. This periodic function can be represented as a Fourier series, namely the series of harmonically-related sines and cosines, as follows:

\begin{align}
f(x) = \frac{a_0}{2} + 
\sum_{n=1}^{\infty} \left\{a_n \cos{nx} + b_n \sin{nx}\right\} \label{fourier}
\end{align}
where $a_0$, $a_n$, and $b_n$ are constant values called Fourier coefficients.

In other references, the Fourier series of $f(x)$ is also defined as follows:

\begin{align*}
f(x) = \frac{a_0}{2} + 
\sum_{n=1}^{\infty} \left\{a_n \cos{\frac{2\pi nx}{P}} + b_n \sin{\frac{2\pi nx}{P}}\right\}
\end{align*}
which is indeed the same representation as~\eqref{fourier}, given the assumption $P = 2\pi$. However, note that we will be using the representation in~\eqref{fourier} for our purpose.

There are other ways of representing the Fourier series of a function. For example, when we define new variables $d_n$, $\varphi_n$ and $\theta_n$ such that 

\begin{align*}
d_n = \sqrt{a_n^2 + b_n^2},
&{}&
tan{\varphi_n} = \frac{a_n}{b_n},
&{}&
tan{\theta_n} = \frac{b_n}{a_n}
\end{align*}
the following are valid forms of Fourier series.

\begin{align*}
f(x) = \frac{a_0}{2} + \sum_{n=1}^{\infty} d_n \sin{nx + \varphi_n}
&{}&
\text{or}
&{}&
f(x) = \frac{a_0}{2} + \sum_{n=1}^{\infty} d_n \cos{nx + \theta_n}
\end{align*}

Note that a periodic function must satisfy certain conditions so that it can be represented as a Fourier series (there are many resources regarding this topic on the Internet).

In the upcoming sections, we would like to solve the Fourier coefficients (namely $a_0$, $a_n$ and $b_n$) in terms of $x$.



## References

1. R. S. Sutton and A. G. Barto, *Reinforcement learning: an introduction.* Cambridge, MA: The MIT Press, 2018.