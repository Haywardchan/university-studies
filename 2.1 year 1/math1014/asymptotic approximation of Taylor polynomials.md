If $f^{(n)}(a)$ exist then $$\lim_{x\to a} \frac{f(x)-T_n(x)}{(x-a)^n}=0$$, or equivalently, by using little o notation,
$$f(x)=T_n(x)+o(|x-a|^n)=\sum_{k=0}^{n}\frac{f^{k}(a)}{k!}(x-a)^k+o(|x-a|^n),\space as \space x\to a$$
Remarks:
1. the accuracy improves as n increase
2. In general $f(x) \neq \lim_{n \to \infty}T_n(x)$