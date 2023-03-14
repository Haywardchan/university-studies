### Propositional logic
proposition is the building block of logic statements
truth value and false value is denoted by T and F
- the outcome of a proposition must be True or False explicitly
I.e 
(a) Beijing is the capital of China. 
(b) COMP 2711 is an elective course for the COMP program. 
(c) 2 + 2 = $2^2$
(d) 1 + 1 = 3
$\therefore (a)(c) T,(b)(d) F$

Logical paradoxes and dependent statement are **not** propositions
I.e
(a) No parking 
(b) Who has an iPad? 
(c) y = log(x+1) 
(d) x 2 – 3x + 1 = 0

(a) This sentence is false. (Liar paradox) 
(b) A male barber shaves all and only those men who do not shave themselves. (Barber paradox)

#### Compound proposition
lowercase *p, q, r* are represented as propositions
Logical operators can turn existing propositions into new propositions
- definition of logical operator can be given in a form of truth table by enumerating all the possible value of the propositions involved

##### Negation $\neg$
$\neg p$ or $\bar p$
meaning not in computer science !
![[Pasted image 20220902005911.png|100]]

##### conjunction $\land$
$\land$ means and in computer science &&
![[Pasted image 20220902005859.png|150]]

##### disjunction $\lor$
$\lor$ means or in computer science ||
![[Pasted image 20220902010110.png|150]]

##### Exclusive or $\bigoplus$
the proposition that is true when exactly one of p and q is true and is false otherwise.
![[Pasted image 20220902010348.png|150]]

##### Conditional Statement/ Implications $\rightarrow$
$$p(hypothsis/premise)\rightarrow q(conclusion/consequence)$$
![[Pasted image 20220902010735.png|150]]

If $p\rightarrow q$ is true:
p is a sufficient condition of q
q is a necessary condition of p

**Equivalent ways of expressing p → q:**
 if p, then q 
 q if p 
 q when p 
 p implies q 
 q follows from p 
 p is a sufficient condition for q 
 q is a necessary condition for p
 p only if q (falsity of q implies falsity of p ) 
 “The company can succeed only if it has sufficient funding.”

##### Converse/ Contrapositive
The **converse** of p→q is q→p. 
The **contrapositive** of p→q is ¬q→¬p. 
The **inverse** of p→q is ¬p → ¬q.
p→q and its contrapositive are **equivalent**
![[Pasted image 20220902011125.png|500]]

##### Biconditional Statement↔
The biconditional statement p↔q is the proposition “p if and only if q”.
The statement is true when p and q have the **same** truth value and is false otherwise.
![[Pasted image 20220902011326.png|150]]
**Equivalent ways of expressing p ↔ q:**
 p if and only if q 
e p iff q 
 p is necessary and sufficient for q 
 if p then q, and conversely

##### Theres ambiguity to avoid in natural language
“if … then …” in natural language actually means “if and only if”.
“If you finish your meal, then you can have dessert” 
 What if you don’t finish your meal? 
 In natural language: then you can’t have dessert.  In logic: unspecified

##### Precedence of logical operators
![[Pasted image 20220902011607.png|200]]

#### Proposition equivalence
A **tautology** is a compound proposition that is **always true**, no matter what the truth values of the propositional variables that occur in it. 
A **contradiction** is a compound proposition that is **always false**. 
A **contingency** is a compound proposition that is **neither** a tautology nor a contradiction.

I.e
![[Pasted image 20220902011825.png|400]]
p∨¬p is a tautology 
p^¬p is a contradiction
p→¬p is a contingency

##### Logical equivalence p ≡ q (or p ⇔ q)
**Compound propositions that always have the same truth values are called logically equivalent**
The compound propositions p and q are called logically equivalent if p ↔ q is a tautology.

I.e 
 𝑝 → 𝑞 ↔ (¬𝑝 ∨ 𝑞) ≡ 𝑇 
 𝑝 ↔ 𝑞 ≡ 𝑝 → 𝑞 ∧ 𝑞 → 𝑝 
 𝑇 ↔ 𝐹 ≡ 𝐹
 2 = 3 ∧ (5 ≠ 4) ≡ 𝐹 
 𝑝: 2 + 2 = 4 𝑝 is true

### De Morgan's laws
Show that **¬(p ∨ q) and ¬p ^ ¬q** are logically equivalent.
![[Pasted image 20220902012241.png|600]]
p → q ≡ ¬p ∨ q
p ⊕ q ≡ (p ^ ¬ q) ∨ (¬p ^ q)
¬(p →q) 
≡ ¬(¬p ∨ q)
≡ ¬(¬p) ^¬q 
≡ p ^ ¬q
![[Pasted image 20220902012539.png|400]]
![[Pasted image 20220902012605.png|500]]
![[Pasted image 20220902012627.png|600]]
Q. Show that ¬(p∨(¬p^q)) and ¬p^¬q are logically equivalent by developing a series of logical equivalences.
¬(p ∨ (¬p ^ q)) 
≡ ¬p ^ (¬(¬p^q)) 
≡ ¬p ^ (¬(¬p ) ∨ ¬q) 
≡ ¬p ^ (p ∨ ¬q) 
≡ (¬p ^ p) ∨ (¬p ^ ¬q) 
≡ F ∨ (¬p ^ ¬q) ≡ ¬p ^ ¬q

Q. Show that (p^q)→(p∨q) is a tautology by developing a series of logical equivalences
(p^q)→(p∨q) 
≡ ¬ (p^q) ∨ (p∨q) 
≡ (¬p ∨ ¬q) ∨ (p∨q) 
≡ (p ∨ ¬p) ∨ (q ∨ ¬q) 
≡ T ∨ T ≡ T

#### Revisit the Knight and Knave puzzle 
 Let 𝑝 be “A is knight” and 𝑞 be “B is knight” 
 A: “We are both knaves”: ¬𝑝 ∧ ¬𝑞 
 B says nothing
 Two possibilities 
 If A's claim is true, then ¬𝑝 ∧ ¬𝑞 is true. If A is telling the truth, then he is knight and 𝑝 is true. However, ¬𝑝 ∧ ¬𝑞 and 𝑝 cannot both be true.
 If A's claim is false, then ¬𝑝 ∧ ¬𝑞 is false, i.e., ¬ ¬𝑝 ∧ ¬𝑞 is true. Using de Morgan's law, ¬ ¬𝑝 ∧ ¬𝑞 ≡ 𝑝 ∨ 𝑞. Since A's claims is false, he is a khave, so 𝑝 is false. Therefore, 𝑞 must be true.

