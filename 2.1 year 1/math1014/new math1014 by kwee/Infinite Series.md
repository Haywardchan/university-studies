### Infinite Series


$$S_\infty=\sum_{i=1}^{n\to\infty}a_n$$
- If the limit above exists as a number $L$, we say the infinite series **converges** to $L$; 
- If the limit above doesn’t exist, we say the infinite series **diverges**.

## Tests
- [[Geometric Sequences]]
- [[2.1 year 1/math1014/new math1014 by kwee/Telescoping Sum]]

**Absolute Convergence**: $\sum|a_n|$ converge -> $\sum a_n$ converge
**Conditional Convergence**: convergence other than abolute convergence (e.g. $\sum\dfrac{1}{n}$ diverge but $\sum(-1)^n\dfrac{1}{n}$ converge)
> terms in the infinite series can be rearranged for **absolute convergence** but not for **conditional convergence**

1. (Limit Test) $\displaystyle\lim_{n\to\infty}a_n\neq0$ -> diverge
2. (Integral Test) $\sum a_n\sim\int_{1}^{\infty}f(x)dx$
	- $f(x)$ is **continuous, positive and decreasing**
3. (Comparison Tests)
	- (Direct Comparison) $a_n > b_n$ or $a_n < b_n$ -> $\sum a_n\sim\sum b_n$
		- similar to **sandwich theorem**
	- (Limit Comparison) $\displaystyle\lim_{n\to\infty}\dfrac{a_n}{b_n}=\left\{0, \mathbb{R}, \infty\right\}$
		-  <span style="color:orange;font-weight:bold">⚠️</span> $\mathbb{R}$: **both converge or diverge**
		- $0$: $b_n$ converge -> $a_n$ converge
		- $\infty$: $b_n$ diverge -> $a_n$ diverge
		- useful for **p-series** comparison
4. (Geomtric Growth Test) $G(n)=a\rho^n$
	- (Ratio Test) $\displaystyle\lim_{n \to \infty}\left|\frac{a_{n+1}}{a_n}\right|=\left\{0, 1, \infty\right\}\leftrightarrow\rho$
		- useful for $a^n$, $n!$ etc.
	- (Root Test) $\displaystyle\lim_{n \to \infty} \sqrt[n]{|a_n|}=\left\{0, 1, \infty\right\}\leftrightarrow\sqrt[n]{a}\rho$
		- useful for $x^n, n^n$ etc.
5. (Three-Condition Test / Alternating Series)
	- $u_n>0$, $u_{n+1}>u_n$ eventually and $\displaystyle\lim_{n\to\infty}u_n=0$

**Approximations and Error Bounds**
1. (Integral Test) Letting $R_n=S_\infty-S_n$, we have
$$\begin{align*}&\text{(Error Bound)}&\hspace{30px}\int^\infty_{n+1}f(x)\:dx&\leq R_n\leq\int^\infty_{n}f(x)\:dx\\
&\text{(Series Bound)}&\hspace{30px}S_n+\int^\infty_{n+1}f(x)\:dx&\leq S_\infty\leq S_n+\int^\infty_{n}f(x)\:dx
\end{align*}$$
![[Pasted image 20220501051023.png]]
2. (Alternating Series)
$$|S_n-S_\infty|<|S_{n+1}|$$ and the error has the same sign as $S_{n+1}$.


## Taylor and Maculin Series
**Power Series**: $$\sum_{n=0}^\infty a_nx^n$$
can be summed, multiplied, compositied, term-by-term differentiated and integrated.

**Convergence Theorem**
The convergence pattern of the power series follows the following pattern: ($R=\left\{0, \mathbb{R}^+, \infty\right\}$. In general, $R$ is found by **ratio test**.)

![[Pasted image 20220501033757.png]]

**Taylor Series**:
$$\sum_{n=0}^{\infty}\dfrac{f^{(n)}(\pmb{a})}{n!}(x-a)^n$$
is the Taylor series **generated** by the function $f(x)$ at $x=a$. Its deriatives matches all deriatives of $f(x)$. The Taylor polynomial $P_n(x)$ is generated by truncating the series.

Define $R_n(x)+P_n(x)=f(x)$. Technically $R_n(x)$ are the remaining terms of the series. See **Taylor's Theorem** later.

**Convergence** (follows from definition):
>If $\displaystyle\lim_{n\to\infty}R_n(x)=0$, then the Taylor series converges to $f$.

**Taylor's Theorem** (higher-order mean value theorem)
If $f, f', f'', ..., f^{(n)}$ are continuous on $[a,b]$, and $f^{(n)}$ is differentiable on $[a,b]$, then $\exists c\in(a,b)$ s.t.
$$\begin{align*}
f(b)\:=\:&f(a)+f'(a)(b-a)+\dfrac{f''(a)}{2!}(b-a)^2
\\&+\:...\:+\dfrac{f^{(n)}(a)}{n!}(b-a)+\boxed{\dfrac{f^{(n+1)}(c)}{(n+1)!}(b-a)^{n+1}}\end{align*}$$
Replacing $b$ by $x$, we define $R_n(x)$ as the last term.

*This is special because we replaced the rest of the series with one single term, $\dfrac{f^{(n+1)}(c)}{(n+1)!}(x-a)^{n+1}$, where $c\in(a,x)$.*

**Error Bound**:
$$|f(x)-P_n(x)|<\dfrac{\max{\left|f^{(n+1)}(t)\right|_{[(a,x)}}}{(n+1)!}(x-a)^{n+1}$$















Further example of this topic:
*the ratio of integers can be written down*
>$2.3\bar{17}=2.3+\frac{17}{10^3}+\frac{17}{10^5}+\frac{17}{10^7}+...$ 
>		$=2.3+\frac{\frac{17}{10^3}}{1-\frac{1}{10^2}}$ 
>		$=2.3+\frac{\frac{17}{1000}}{\frac{99}{100}}$
>		$=\frac{1147}{495}$

