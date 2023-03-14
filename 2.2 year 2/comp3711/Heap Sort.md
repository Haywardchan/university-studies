##### Priority queue (abstract data structure)
calculating the time complexity by the FIFO principal
Ie A:100 B:10 C:1
A,B,C need 100+110+111/3=107 time units while
C,B,A only need 1+11+111=41 time units

Processing the shortest job first corresponds to extracting the smallest element from the queue
Insert new printing jobs as they arrive
thus 2 operations are needed: Insert and extract min

2 Possible implementation
1. unsorted list + a pointer to the smallest element
2. sorted doubly linked list + a pointer to first element
requires O(1) and O(n) for
1. Insert and extract min
2. extract min and Insert

Heaps are 'almost' complete binary trees
1. All levels are **full** except possibly the lowest level
2. If the lowest level is not full, then nodes must be packed to the **left**
Heap order prop:
3. The value of a node is at least the value of its parent — Min-heap

thus support both operations at O(logn) time complexity

![[Pasted image 20230315000842.png|200]]
A heap with height (deepest level) ℎ has $2^i$ nodes on every level i < ℎ
A heap with height ℎ has $2^h − 1$ nodes above level ℎ.
A heap with height ℎ has between $2^h$ and $2^{h+1} − 1$ nodes
an n-element heap has height Θ(logn)

Array representation
![[Pasted image 20230315000945.png|400]]

### Insertion
we use the general strategy bubble up:
1. Add the new element to the next available position at the lowest level
2. if the parent of the element is larger than the element, then interchange the parent with child. 
![[Pasted image 20230315001157.png|300]]