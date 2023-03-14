### proof of $S_0=S_2$
to prove $S_0=S_2$, we have to prove
a) $S_2\subseteq S_0$
b) $S_0 \subseteq S_2$

For a) $S_2\subseteq S_0$:
1. since $B \to C \in$ $S_2$, conf($B \to C$)$\geq$threshold
2. the remaining question is whether supp($B\to C$)$\geq$threshold
3. $\because B\to C \in S_2$, $\frac{supp(B,C)}{supp(B)}$have been calculated
4. $\therefore B,C \in S_1$,which means supp(B) and supp(C)$\geq$threshold
5. supp($B\to C$)=supp(B,C)
6. supp($B\to C$)$\geq$threshold

For b) $S_0 \subseteq S_2$:
1. since $B\to C\in S_0$,conf($B\to C$)$\geq$threshold; supp($B\to C$)$\geq$threshold
2. $\because$ supp($B\to C$)$\geq$threshold $\therefore$ supp($B,C$)$\geq$threshold, B,C $\in S_1$
3. $\because$ supp($B,C$)$\geq$threshold $\therefore$ supp(B)$\geq$threshold, B $\in S_1$ 
4. $\because$(B),(B,C) $\in S_1$
5. step 2 must consider $\frac{supp(B,C)}{supp(B)}$ and generate $B \to C$ as its conf($B\to C$)$\geq$threshold
6. $\therefore B\to C \in S_2$ 