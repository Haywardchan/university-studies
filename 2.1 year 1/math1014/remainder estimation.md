### remainder estimation
can be used when
> 1. f is CPD for $x>=n$
> 2. $\sum a_n$ is convergent

if $R_n =S-S_n$ then 
>$\int_{n+1}^{\infty}f(x)dx<=R_n<=\int_{n}^{\infty}f(x)dx$

noted that $S=R_n+S_n$, so
>$\int_{n+1}^{\infty}f(x)dx+S_n<=R_n+S_n=S<=\int_{n}^{\infty}f(x)dx+S_n$

A further usage is incorporating the [[comparison theorem]]:
suppose $S_n$ and $t_n$ are the partial sums of an [[2.1 year 1/math1014/Infinite Series]] $a_n$ and $b_n$ where $R_n$ and $T_n$ are the remainder of the series.
>If $a_n<=b_n$, then 
$R_n<=T_n$ can be used to estimate the remainder of the sum of $a_n$ 