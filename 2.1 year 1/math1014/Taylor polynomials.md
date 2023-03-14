let f be a function with f', f'', f''',..., and $f^{(n)}$ defined at a.
the n-th order Taylor polynomial for f with its center at a is 
$$T_n(x)=f(a)+f'(a)(x-a)+\frac{f''(a)}{2!}(x-a)^2+...+\frac{f^{(n)}(a)}{n!}(x-a)^n$$
[[Taylor series]]
[[Maclaurin series]]

Uniqueness of Taylor polynomials
suppose f is a funciton with f',f'',f''',...,$f^{(n)}$ defined at a. If $P_n$ is a polynomial of degree n satisfying $$P_n(a)=f(a), P_n'(a)=f'(a), P_n''(a)=f'(a)$$
then $$P_n(x) \equiv T_n(x)$$

[[asymptotic approximation of Taylor polynomials]]
If $f^{(n)}(a)$ exist then $$\lim_{x\to a} \frac{f(x)-T_n(x)}{(x-a)^n}=0$$, or equivalently, by using little o notation,
$$f(x)=T_n(x)+o(|x-a|^n)=\sum_{k=0}^{n}\frac{f^{k}(a)}{k!}(x-a)^k+o(|x-a|^n),\space as \space x\to a$$
Remarks:
1. the accuracy improves as n increase
2. In general $f(x) \neq \lim_{n \to \infty}T_n(x)$