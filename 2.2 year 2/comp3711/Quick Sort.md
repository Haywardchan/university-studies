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
