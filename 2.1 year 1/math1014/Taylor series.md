#### Taylor series
$$\sum_{n=0}^\infty \frac{f^{(n)}(a)}{n!}(x-a)^n=f(a)+f'(a)(x-a)+\frac{f''(a)}{2!}(x-a)^2+...+\frac{f^{(n)}(a)}{n!}(x-a)^n$$
the [[Maclaurin series]] is the taylor series with a=0

the remainder of the taylor series 
$$R_n(x)=f(x)-T_n(x)$$
Remarks:$\sum_{n=0}^\infty \frac{f^{(n)}(a)}{n!}(x-a)^n$ may not converge at x where f(x) is well-defined

Convergence thm of Taylor series
If $\lim_{n \to \infty}R_n(x)=0$ in an open interval I that contains a then
$$\lim_{n \to \infty}T_n(x)=\sum_{k=0}^\infty \frac{f^{(k)}(a)}{k!}(x-a)^k, x \in I$$
integral form of the remainder
If $f^{n+1}$ is continuous in an open interval I that contains a, then
$$R_n(x)=\frac{1}{n!}\int_a^x(x-t)^nf^{n+1}(t)dt, x \in I$$
lagrange remainder
If $f^{(n+1)}(x)$ is continuos in an open interval $I$ that contains a, then there is a, then there is c between a and x such that $$R_n(x)=\frac{f^{(n+1)}(c)}{(n+1)!}(x-a)^{n+1}$$
remainder estimate
If $|f^{(n+1)}(x)\leq M$ in an open interval I that contains a, then 
$$|R_n(x)|\leq \frac{M}{(n+1)!}|x-a|^{n+1},x \in I$$
Hence, if $|f^{(n+1)}(x)|\leq M$ for every n in $I$, then $$f(x)=\sum_{k=0}^\infty \frac{f^{(k)}(a)}{k!}(x-a)^k, x \in I$$
![[Taylor series representation]]
