---
title: "Fourier Series: How to Solve the Fourier Coefficients?"
tag: formula
show_edit_on_github: false
---

In this article, we will be going through the process of solving the coefficients of Fourier Series.

<!--more-->

## Brief Introduction

In simple language, a periodic function, $f(x)$, is defined as a function in which, a value $P$ exists such that $f(P + x) = f(x)$. This periodic function can be represented as a Fourier series, namely the series of harmonically-related sines and cosines, as follows:

$$
\begin{align}
f(x) = \frac{a_0}{2} + 
\sum_{n=1}^{\infty} \left\{a_n \cos{nx} + b_n \sin{nx}\right\} \label{fourier}
\end{align}
$$
where $a_0$, $a_n$, and $b_n$ are constant values called Fourier coefficients.

In other references, the Fourier series of $f(x)$ is also defined as follows:

$$
\begin{align*}
f(x) = \frac{a_0}{2} + 
\sum_{n=1}^{\infty} \left\{a_n \cos{\frac{2\pi nx}{P}} + b_n \sin{\frac{2\pi nx}{P}}\right\}
\end{align*}
$$

which is indeed the same representation as \eqref{fourier}, given the assumption $P = 2\pi$. However, note that we will be using the representation in \eqref{fourier} for our purpose of solving Fourier coefficients.

There are other ways of representing the Fourier series of a function. For example, when we define new variables $d_n$, $\varphi_n$ and $\theta_n$ such that 

$$
\begin{align*}
d_n = \sqrt{a_n^2 + b_n^2},
&{}&
\tan{\varphi_n} = \frac{a_n}{b_n},
&{}&
\tan{\theta_n} = \frac{b_n}{a_n}
\end{align*}
$$

the following are valid forms of Fourier series.

$$
\begin{align*}
f(x) = \frac{a_0}{2} + \sum_{n=1}^{\infty} d_n \sin{nx + \varphi_n}
&{}&
\text{or}
&{}&
f(x) = \frac{a_0}{2} + \sum_{n=1}^{\infty} d_n \cos{nx + \theta_n}
\end{align*}
$$

Note that a periodic function must satisfy certain conditions so that it can be represented as a Fourier series (there are many resources regarding this topic on the Internet).

In the upcoming sections, we would like to solve the Fourier coefficients (namely $a_0$, $a_n$ and $b_n$) in terms of $x$.

## Fourier coefficient $a_0$

First, we integrate both sides of \eqref{fourier} to the range of $[-\pi, \pi]$.

$$
\begin{align}
\int_{-\pi}^{\pi} f(x) \mathop{dx} &= 
\int_{-\pi}^{\pi} \frac{a_0}{2} \mathop{dx} + 
\int_{-\pi}^{\pi} \left\{\sum_{n=1}^{\infty} \left\{a_n \cos nx + b_n \sin nx\right\}\right\} \mathop{dx} \notag
\\ &=
\frac{a_0}{2} x\Big|_{-\pi}^{\pi} + 
\sum_{n=1}^{\infty} 
\left\{a_n \frac{\sin nx}{n} \Big|_{-\pi}^{\pi} + 
b_n \frac{-\cos nx}{n} \Big|_{-\pi}^{\pi} \right\} \label{fourier:a_0}
\end{align}
$$

From \eqref{fourier:a_0}, we can verify that $\frac{\sin nx}{n} \Big\rvert_{-\pi}^{\pi} = 0$ and $\frac{-\cos nx}{n} \Big\rvert_{-\pi}^{\pi} = 0$. Therefore, \eqref{fourier:a_0} can be rewritten as follows:

$$
\begin{align*}
\int_{-\pi}^{\pi} f(x) \mathop{dx} &= 
\frac{a_0}{2} x\Big|_{-\pi}^{\pi} 
\\ &=
\frac{a_0}{2} (2 \pi) = a_0 \pi 
\end{align*}
$$

which can be rearranged to obtain the expression of Fourier coefficients $a_0$ that we are interested in.

$$
\begin{equation}
a_0 = \frac{1}{\pi} \int_{-\pi}^{\pi} f(x) \mathop{dx} 
\end{equation}
$$

## Fourier coefficient $a_n$

To express \eqref{fourier} in terms of Fourier coefficient $a_n$, we will first multiply both sides of \eqref{fourier} by $\cos mx$, where $m \in \mathbf{Z^+}$. Then, we integrate both sides of \eqref{fourier} to the range of $[-\pi, \pi]$, as follows:

$$
\begin{align}
\int_{-\pi}^{\pi} f(x) \cos mx \mathop{dx} =& 
\int_{-\pi}^{\pi} \frac{a_0}{2} \cos mx \mathop{dx} \notag
\\ &+
\int_{-\pi}^{\pi} \left\{\sum_{n=1}^{\infty} \left\{a_n \cos nx \cos mx + b_n \sin nx \cos mx\right\}\right\} \mathop{dx} \label{fourier:a_n_1}
\end{align}
$$

The next part is a bit tricky. Take note that we apply trigonometric identities to convert the terms enclosed within the summation as such:

$$
\begin{align}
\cos nx \cos mx &= \frac{1}{2} \left[\cos{(n+m)x} + \cos{(n-m)x}\right] \label{cosAndCos}
\\
\sin nx \cos mx &= \frac{1}{2} \left[\sin{(n+m)x} + \sin{(n-m)x}\right] \label{sinAndCos}
\end{align}
$$

{::options parse_block_html="true" /}

<details><summary markdown="span">*Need some quick refreshers on trigonometric identities? Click me.* 😀</summary>

***

Some refreshers on the trigonometric identities which are applied here:

$$
\begin{align*}
\cos a \cos b &= \frac{1}{2} 
\left[\cos{a} \cos{b} - \sin{a} \sin{b} + \cos{a} \cos{b} + \sin{a} \sin{b}\right]
\\ &= \frac{1}{2}
\left[\cos{(a+b)} + \cos (a - b)\right]
\\
\sin a \cos b &= \frac{1}{2} 
\left[\sin{a} \cos{b} + \cos{a} \sin{b} + \sin{a} \cos{b} - \cos{a} \sin{b}\right]
\\ &= \frac{1}{2}
\left[\sin{(a+b)} + \sin{(a-b)}\right]
\end{align*}
$$

***

</details>

{::options parse_block_html="false" /}

By substituting \eqref{cosAndCos} and \eqref{sinAndCos} into the right hand side of \eqref{fourier:a_n_1}, we have

$$
\begin{align}
\int_{-\pi}^{\pi} f(x) \cos mx \mathop{dx} =& 
\int_{-\pi}^{\pi} \frac{a_0}{2} \cos mx \mathop{dx} \notag 
\\ &+
\int_{-\pi}^{\pi} \frac{1}{2} \Biggl\{ \sum_{n=1}^{\infty} \Bigl\{ 
a_n \left(\cos{(m+n)x} + \cos{(m-n)x} \right) \notag 
\\ & \hspace{16mm}+
b_n \left(\sin{(m+n)x - \sin{(m-n)x}}\right)\Bigr\} \Biggr\} \mathop{dx} \label{fourier:a_n_2}
\end{align}
$$

First, we consider the case where $m \neq n$ for \eqref{fourier:a_n_1}. We can verify that

$$
\begin{align*}
\int_{-\pi}^{\pi} \cos{(m+n)x} \mathop{dx} &= 
\left.\frac{\sin{(m+n)}x}{m+n}\right|_{-\pi}^{\pi} 
\\ &= 
\left[\frac{\sin{(m+n)\pi}}{m+n}\right] - \left[\frac{\sin{(m+n)(-\pi)}}{m+n}\right]
\\ &= 
\left[\frac{\sin{(m+n)\pi}}{m+n}\right] - \left[-\frac{\sin{(m+n)\pi}}{m+n}\right]
\\ &= 0 + 0
\\ &= 0
\end{align*}
$$

and

$$
\begin{align*}
\int_{-\pi}^{\pi} \sin{(m+n)x} \mathop{dx} &= 
\left.\frac{-\cos{(m+n)}x}{m+n}\right|_{-\pi}^{\pi} 
\\ &= 
\left[\frac{-\cos{(m+n)\pi}}{m+n}\right] - \left[\frac{-\cos{(m+n)(-\pi)}}{m+n}\right]
\\ &= 
\left[\frac{-\cos{(m+n)\pi}}{m+n}\right] - \left[\frac{-\cos{(m+n)\pi}}{m+n}\right]
\\ &= 0
\end{align*}
$$

because $m+n \in \mathbf{Z}$.

Therefore, we can also verify that 

$$
\begin{align*}
\int_{-\pi}^{\pi} \cos{(m-n)x} \mathop{dx} = 0 
&{}&
\text{and}
&{}&
\int_{-\pi}^{\pi} \sin{(m-n)x} \mathop{dx} = 0  
\end{align*}
$$

given $m-n \in \mathbf{Z}$.

This reduces the summation in \eqref{fourier:a_n_1} to only terms where $m=n$, as follows:

$$	
\begin{align}
\int_{-\pi}^{\pi} f(x) \cos mx \mathop{dx} =& 
\int_{-\pi}^{\pi} \frac{a_0}{2} \cos mx \mathop{dx} \notag 
\\ &+
\int_{-\pi}^{\pi} \frac{1}{2} \bigl\{ 
a_m \left(\cos{2mx} + \cos{0} \right) + b_m \left(\sin{2mx} + \sin{0}\right)\bigr\} \mathop{dx} \label{fourier:a_n_3}
\end{align}
$$

From \eqref{fourier:a_n_3}, we can verify that

$$
\begin{align*}
\int_{-\pi}^{\pi} \cos{(2m)x} \mathop{dx} = 0 
&{}&
\int_{-\pi}^{\pi} \cos{0} \mathop{dx} &= \int_{-\pi}^{\pi} \mathop{dx} = 2\pi
\\
\int_{-\pi}^{\pi} \sin{(2m)x} \mathop{dx} = 0
&{}&
\int_{-\pi}^{\pi} \sin{0} \mathop{dx} &= \int_{-\pi}^{\pi} 0 \mathop{dx} = 0
\end{align*}
$$

Therefore, we can further reduce \eqref{fourier:a_n_3} to the following:

$$
\begin{align}
\int_{-\pi}^{\pi} f(x) \cos mx \mathop{dx} = 
\frac{a_m}{2} \int_{-\pi}^{\pi} \cos{0} \mathop{dx} =
a_m \pi \label{fourier:a_n_4}
\end{align}
$$

There is still a last step before completing the expression of Fourier equation in terms of Fourier coefficient $a_n$. By rearranging the term in \eqref{fourier:a_n_4}, and then replacing $m$ with $n$, we obtain

$$
\begin{align}
a_n = \frac{1}{\pi} \int_{-\pi}^{\pi} f(x) \cos nx \mathop{dx}
\end{align}
$$	

## Fourier coefficient $b_n$
We use the similar approach as previous section to express \eqref{fourier} in terms of Fourier coefficient $b_n$. The difference here is that, we will first multiply both sides of \eqref{fourier} by $\sin mx$ instead, where $m \in \mathbf{Z^+}$. Then, we integrate both sides of \eqref{fourier} to the range of $[-\pi, \pi]$, as follows:

$$
\begin{align}
\int_{-\pi}^{\pi} f(x) \sin{mx} \mathop{dx} =& 
\int_{-\pi}^{\pi} \frac{a_0}{2} \sin{mx} \mathop{dx} \notag
\\ &+
\int_{-\pi}^{\pi} \left\{\sum_{n=1}^{\infty} \left\{a_n \sin{mx} \cos{nx} + b_n \sin{mx} \sin{nx}\right\}\right\} \mathop{dx} \label{fourier:b_n_1}
\end{align}
$$

The trigonometric identities used here are slightly different from \eqref{fourier:a_n_1}, as follows:

$$
\begin{align}
\sin{mx} \cos{nx} &= \frac{1}{2} \left[\sin{(m-n)x} + \sin{(m+n)x}\right] \label{cosAndSin}
\\
\sin{mx} \sin{nx} &= \frac{1}{2} \left[\cos{(m-n)x} - \cos{(m+n)x}\right] \label{sinAndSin}
\end{align}
$$

Now, substitute \eqref{cosAndSin} and \eqref{sinAndSin} into \eqref{fourier:b_n_1}.

$$
\begin{align}
\int_{-\pi}^{\pi} f(x) \sin{mx} \mathop{dx} =& 
\int_{-\pi}^{\pi} \frac{a_0}{2} \sin{mx} \mathop{dx} \notag 
\\ &+
\int_{-\pi}^{\pi} \frac{1}{2} \Biggl\{ \sum_{n=1}^{\infty} \bigl\{ 
a_n \left(\sin{(m-n)x} + \sin{(m+n)x} \right) \notag 
\\ & \hspace{16mm}+
b_n \left(\cos{(m-n)x - \cos{(m+n)x}}\right)\Bigr\} \Biggr\} \mathop{dx} \label{fourier:b_n_2}
\end{align}
$$

Considering case where $m \neq n$, we have already verified the following from previous sections.

$$
\begin{align*}
\int_{-\pi}^{\pi} \sin{(m-n)x} \mathop{dx} = 0 
&{}&
\int_{-\pi}^{\pi} \sin{(m+n)x} \mathop{dx} = 0
\\
\int_{-\pi}^{\pi} \cos{(m-n)x} \mathop{dx} = 0 
&{}&
\int_{-\pi}^{\pi} \cos{(m+n)x} \mathop{dx} = 0
\end{align*}
$$

Therefore, the summation in \eqref{fourier:b_n_2} can be reduced to only terms where $m = n$ as follows:

$$
\begin{align}
\int_{-\pi}^{\pi} f(x) \sin{mx} \mathop{dx} =& 
\int_{-\pi}^{\pi} \frac{a_0}{2} \sin{mx} \mathop{dx} \notag 
\\ &+
\int_{-\pi}^{\pi} \frac{1}{2} \Bigl\{ 
a_m \left(\sin{0} + \sin{2mx} \right) + b_m \left(\cos{0} - \cos{2mx}\right)\bigr\} \mathop{dx} \label{fourier:b_n_3}
\end{align}
$$

Again from previous section, recall that

$$
\begin{align*}
\int_{-\pi}^{\pi} \sin{0} \mathop{dx} &= \int_{-\pi}^{\pi} 0 \mathop{dx} = 0
&{}&
\int_{-\pi}^{\pi} \sin{(2m)x} \mathop{dx} = 0
\\
\int_{-\pi}^{\pi} \cos{0} \mathop{dx} &= \int_{-\pi}^{\pi} \mathop{dx} = 2\pi
&{}&
\int_{-\pi}^{\pi} \cos{(2m)x} \mathop{dx} = 0 
\end{align*}
$$

Therefore, \eqref{fourier:b_n_3} can be further reduced to

$$
\begin{align}
\int_{-\pi}^{\pi} f(x) \sin{mx} \mathop{dx} = 
\frac{b_m}{2} \int_{-\pi}^{\pi} \cos{0} \mathop{dx} =
b_m \pi \label{fourier:b_n_4}
\end{align}
$$

Finally, we rearrange the terms in \eqref{fourier:b_n_4}, then replace $m$ with $n$ to obtain the expression of Fourier coefficient, $b_n$ in terms of $x$.

$$
\begin{align}
b_n = \frac{1}{\pi} \int_{-\pi}^{\pi} f(x) \sin{nx} \mathop{dx}
\end{align}
$$

## Bonus: Fourier Series for Odd and Even Functions

A function $f$ of variable $x$, denoted by $f(x)$, is defined as an even function if the following condition is satisfied.

$$
\begin{equation*}
f(-x) = f(x)
\end{equation*}
$$

In other words, when we plot the graph of $f(x)$ against $x$ on the Cartesian plane (or $xy$-plane), the value of $f(x)$ is symmetric about the $y$-axis. Some examples of even function are $f(x) = \lvert x \rvert$ and $f(x) = x^2$.

A function $f$ of variable $x$, denoted by $f(x)$, is defined as an odd function if the following condition is satisfied.

$$
\begin{equation*}
f(-x) = -f(x)
\end{equation*}
$$

Unlike an even function, when we plot the graph of $f(x)$ against $x$ on the same plane, the value of $f(x)$ is symmetric about the line $y = -x$. Some examples are $f(x) = x^n$ where $n$ is odd.

Recall that some periodic functions can be represented in a Fourier series \eqref{fourier} as follows:

$$
\begin{equation*}
f(x) = \frac{a_0}{2} + 
\sum_{n=1}^{\infty} \left\{a_n \cos{nx} + b_n \sin{nx} \right\}
\end{equation*}
$$

In fact, we have implicitly applied the concept of odd and even functions when solving the coefficients of the Fourier series of a periodic function, $f(x)$ in previous sections. To be more concise, the sine function, $\sin{x}$ is an odd function and the cosine function $\cos{x}$ is an even function, as such:

$$
\begin{align*}
\sin{(-x)} = -\sin{x}
&{}&
\cos{(-x)} = \cos{x}
\end{align*}
$$

In this section, the same concept is applied to find the Fourier series representation of an odd or even periodic functions. The first step is to identify the Fourier series representation of $f(-x)$.

$$
\begin{align}
f(-x) &= \frac{a_0}{2} + 
\sum_{n=1}^{\infty} \left\{a_n \cos{(-nx)} + b_n \sin{(-nx)} \right\} \notag
\\ &= \frac{a_0}{2} + 
\sum_{n=1}^{\infty} \left\{a_n \cos{nx} - b_n \sin{nx} \right\} \label{fourier:neg}
\end{align}
$$

If $f(x)$ is odd, then we can find the Fourier series representation of $f(x)$ by manipulating \eqref{fourier} and \eqref{fourier:neg} as follows:

$$
\begin{align}
f(x) &= \frac{1}{2} \left\{f(x) - f(-x)\right\} \notag
\\
&= \frac{1}{2} \Biggl\{ \Bigl\{
\frac{a_0}{2} + 
\sum_{n=1}^{\infty} \left\{a_n \cos{nx} + b_n \sin{nx} \right\} \Bigr\} \notag
\\ 
& \hspace{11mm} - \Bigl\{
\frac{a_0}{2} + 
\sum_{n=1}^{\infty} \left\{a_n \cos{nx} - b_n \sin{nx} \right\} \Bigr\} \Biggr\} \notag
\\
&= \sum_{n=1}^{\infty} \left\{b_n \sin{nx}\right\}
\end{align}
$$

Similarly, we can also find the Fourier series representation of an even function, $f(x)$ by manipulating \eqref{fourier} and \eqref{fourier:neg} as follows:

$$
\begin{align}
f(x) &= \frac{1}{2} \left\{f(x) + f(-x)\right\} \notag
\\
&= \frac{1}{2} \Biggl\{ \Bigl\{
\frac{a_0}{2} + 
\sum_{n=1}^{\infty} \left\{a_n \cos{nx} + b_n \sin{nx} \right\} \Bigr\} \notag
\\ 
& \hspace{11mm} + \Bigl\{
\frac{a_0}{2} + 
\sum_{n=1}^{\infty} \left\{a_n \cos{nx} - b_n \sin{nx} \right\} \Bigr\} \Biggr\} \notag
\\
&= \frac{a_0}{2} + \sum_{n=1}^{\infty} \left\{a_n \cos{nx}\right\}
\end{align}
$$

## References

1. “Definition of Fourier Series and Typical Examples,” *Math24*, 26-Apr-2020. \[Online\]. Available: [https://www.math24.net/fourier-series-definition-typical-examples/](https://www.math24.net/fourier-series-definition-typical-examples/). \[Accessed: 28-Aug-2020\].

2. “Fourier Series,” *Brilliant Math & Science Wiki*. \[Online\]. Available: [https://brilliant.org/wiki/fourier-series/](https://brilliant.org/wiki/fourier-series/). \[Accessed: 28-Aug-2020\].

3. Libretexts, “4.6: Fourier series for even and odd functions,” *Mathematics LibreTexts*, 14-May-2020. \[Online\]. Available: [https://math.libretexts.org/Bookshelves/Differential_Equations/Book%3A_Partial_Differential_Equations_(Walet)/04%3A_Fourier_Series/4.06%3A_Fourier_series_for_even_and_odd_functions](https://math.libretexts.org/Bookshelves/Differential_Equations/Book%3A_Partial_Differential_Equations_(Walet)/04%3A_Fourier_Series/4.06%3A_Fourier_series_for_even_and_odd_functions). \[Accessed: 28-Aug-2020\].
