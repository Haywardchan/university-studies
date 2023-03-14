![[Pasted image 20230314233018.png|600]]
Given an array A of n distinct elements and an integer i, return the i-th smallest element of A.
![[Pasted image 20230314233933.png|600]]
#### Analysis
The probability of a random pivot being good is 1/2.
The probability of a random pivot being good is 1/2.
After i good pivots, total # of items left to process is $\leq (\frac{3}{4})^in$
![[Pasted image 20230314234358.png|500]]
![[Pasted image 20230314234431.png|600]]
linear-time selection algorithm

Next: [[Heap Sort]]