The dual of [[Merge Sort]]

![[Pasted image 20230314223344.png|300]]
## steps
1. choose item as pivot (all item less than pivot is sort on the left and all items greater than the pivot is on the right)
2. recursively quicksort left and right sides

partition $\theta(n)$
sort 2T(n/2)
combine 0

##### Partition
![[Pasted image 20230314224139.png|300]]
Time $\theta(n)$
Space O(1)

> Pivot selection is crucial

Best case: select the median element as the pivot running at O(nlogn)
Worst case: select the smallest/ largest element as the pivot running at O(n**2)

>Running time independent of input

randomized pivot selection

##### Randomized Algorithms
- Worst case almost never happens: 
	 Every pivot would have to be minimum or maximum; occurs with very low probability
- Expected running time of any input of size n
![[Pasted image 20230314224738.png|400]]

Elements zi and zj are compared at most once in Qsort iff in the binary tree:
they are in child-ancester relationship

#### Running time analysis
$X_{ij}=1$ if $z_i$ is compared with $z_j$
Number of comparison: X= $\sum_{i<j}X_{ij}$
By linearity of expectation: $E[Number\space of\space Comparison]= \sum_{i<j}E[X_{ij}]$
thus $P[compared]=\frac{2}{j-i+1}$
$E[Number\space of\space Comparison]=\sum_{i<j}\frac{2}{j-i+1}=O(nlogn)$

method 2:
$P[compared]=P[Either\space z_i\space or\space z_j\space are\space first\space pivot\space chosen\space in\space Z]$
$=\frac{1+1}{j-i+1}$

method 3:
upper triangular matrix
![[Pasted image 20230314230857.png|400]]

##### Why does quicksort work very well in practice?
- Θ(nlogn) time in expectation on any input – Actually, it’s Θ(nlogn) time with very high probability 
- Small hidden constants and Cache-efficient 
- Even though it has a Θ($n^2$) worst-case running time it beats the Θ(nlogn) worst case Mergesort “on average’
