### Infinite Series
summation of a sequence denoted by $\sum a_n$
partial sum $S_n$ denoted by $\sum\limits_{i=1}^na_n$
If $\lim_{n \to +\infty}S_n = S$ exist as a real number, then we call $\sum a_n$ is convergent
elif $\lim_{n \to +\infty}S_n=DNE/\infty$, then we call $\sum a_n$ is divergent

the convergence of [[geometric series]] can be dicussed:
>$\sum_{n=0}^\infty ar^n$ =$\frac{a}{1-r}$ for $|r|<1$ 
>$\sum_{n=0}^\infty ar^n$ =$\frac{a(r^n-1)}{r-1}$ for $|r|>=1$

[[2.1 year 1/math1014/telescoping sum]] can be used to evaluate convergence.
>1. $set \lim_{n \to \infty} S_n$ after the cancellation of the common terms 
>2. if $\lim_{n \to \infty} S_n=L$ then it converges
>3. elif $\lim_{n \to \infty} S_n=DNE/\infty$ then it diverges

[[harmonic series]] is divergent.
>1. $S_{2n} > 1+\frac{n}{2}$
>2. $\lim_{n \to \infty}1+\frac{n}{2}=\infty$, by the [[comparison test]], 
>3. $\lim_{n \to \infty}S_{2n}=\infty$, therefore it is divergent as well

[[Test for divergence]] is the first test that could be used to prove a series is divergent.
>$\lim_{n \to \infty}\neq0/DNE$ then $\sum_{n=1}^{\infty}a_n$is divergent
>$\lim_{n \to \infty}=0$ is inconclusive, further test is needed

the [[p-series test]] can be used as a convergence test for the p series
>$\int_{1}^{\infty}\frac{1}{x^p}dx$ is convergent when $p>1$
>$\int_{1}^{\infty}\frac{1}{x^p}dx$ is divergent when $p<=1$

the [[integral test]] can be used when simple formula for $S_n$ cannot be found.
>for a function f is CPD(continuous, positive, decreasing) on the interval $[1,\infty)$ and let $a_n$be $f(n)$ then
>1. If $\int_{1}^{\infty}f(x)dx$ converges then $\sum_{1}^{\infty}a_n$ converges
>2. If $\int_{1}^{\infty}f(x)dx$ diverges then $\sum_{1}^{\infty}a_n$ diverges

*n can be started at any integer k*
[[comparison test]] and [[comparison theorem]]

[[altternating series test]]

If the alternating series $\sum_{n=1}^{\infty}(-1)^{n-1}b_n$ satisfies
>1. $b_{n+1}\leq b_n$
>2. $\lim_{n \to \infty} b_n = 0$

we can test the first derivative for checking whether the function is decreasing.


[[absolute convergence]] and [[conditional convergence]]
the following two useful test to determine a give series is absolutely convergent

[[ratio test]]
If $\lim_{n \to \infty}|\frac{a_{n+1}}{a_n}|=L < 1$, then the series is absolutely convergent and therefore convergent
If $\lim_{n \to \infty}|\frac{a_{n+1}}{a_n}|=L > 1$, then the series is divergent
if $\lim_{n \to \infty}|\frac{a_{n+1}}{a_n}|=L = 1$, the ratio test is inconclusive
usually used when factorials or other product exist

[[root test]]
if $\lim_{n \to \infty} \sqrt[3]{|a_n|}=L<1$, then $\sum a_n$ is absolutely convergent
if $\lim_{n \to \infty} \sqrt[3]{|a_n|}=L>1$, then $\sum a_n$ is divergent
if $\lim_{n \to \infty} \sqrt[3]{|a_n|}=L=1$, then $\sum a_n$ is inconclusive

**estimating the sum of a series**
-[[remainder estimation]] can be used when
> 1. f is CPD for $x>=n$
> 2. $\sum a_n$ is convergent


Further example of this topic:
*the ratio of integers can be written down*
>$2.3\bar{17}=2.3+\frac{17}{10^3}+\frac{17}{10^5}+\frac{17}{10^7}+...$ 
>		$=2.3+\frac{\frac{17}{10^3}}{1-\frac{1}{10^2}}$ 
>		$=2.3+\frac{\frac{17}{1000}}{\frac{99}{100}}$
>		$=\frac{1147}{495}$

approximating functions with polynomials
[[linear approximation]]
[[quadratic approximation]]
[[Taylor polynomials]]
[[Taylor series]]
[[Maclaurin series]]
[[power series]]


[[example questions]]
