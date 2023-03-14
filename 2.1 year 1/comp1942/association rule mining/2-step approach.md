### 2-step approach
Step 1:
dividing all frequent items into
$S_1:$ a set of all frequent item of [[support]]>=threshold
$S_2:$ a set of rules with [[confidence]]>=threshold
$step1 \to S_1 \to step2 \to S_2$
step 2:
for any 2 items(x,y)$\in S_1$ where
$X \subset Y$ then if $\frac{supp(X)}{supp(Y)}>=threshold$ then
 association rule $X \to Y-X$ is generated
 
let the result of this approach is $S_0$ and the result of the [[2-step approach]] is $S_2$

[[proof of S_0=S_2]]