https://course.cse.ust.hk/comp3711_2021F/Exams/pastpapers/3711_Exam_Library.html
Lecture 1: Introduction

Overview:
with problem:
    identify/prove lowerbound/hardness
    while not satisfied:
        design algorithms
        analyze algorithms
    implement program
    
    
Lecture 1-2: Bentley

Remark: index start from 1 and end at n

Bentley's Problem (Maximum Subarray Problem):
Given sequence {a1, ... , an}, find the largest sum of contiguous block {ai, ... , aj}.
e.g.: {1, -6, 3, -1, 4, 2, -3, 2} => best = 8 ({3, -1, 4, 2})

Alg'm #0: brute force

"""
ans = -inf
for i = 1 to n do
    for j = i to n do
        sum = 0 
        for k = i to j do
            sum = sum + ak
        ans = max{ans, sum}
return ans
"""

Analysis: O(n3) cubic

Alg'm #1: use previous computed sums to compute new sums

"""
ans = -inf
for i = 1 to n do
    sum = 0
    for j = i to n do
        sum = sum + aj
        ans = max{ans, sum}
return ans
"""

Analysis: O(n2) quadratic

Alg'm #2: divide and conquer
case 1: occur in left part        xxxx | ====
case 2: occur in right part       ==== | xxxx
case 3: occur across the border   ===x | xx==

e.g. {1, -6, 3, -1, 4, 2, -3, 2} => 1 -6 3 -1 | 4 2 -3 2
ans_L = max{-1, -1 + 3, -1 + 3 + -6, -1 + 3 + -6 + 1}
ans_R = max{4, 4 + 2, 4 + 2 + -3, 4 + 2 + -3 + 2}
ans_merge = ans_L + ans_R

"""
if n = 1 then return a1
ans = max{solve(a1 ... a_[n/2], solve(a_[n/2+1] ... an)}
ans_L = -inf, sum = 0
for i = [n/2] down to 1 do
    sum = sum + ai
    ans_L = max{ans_L, sum}
ans_R = -inf, sum = 0
for i = [n/2+1] to n do
    sum = sum + ai
    ans_R = max{ans_R, sum}
return max{ans, ans_L + ans_R}
"""
where [x] means floor function.

Analysis: O(nlogn)
T(n) = {O(1)             if n = 1
        2T(n/2) + O(n)   if n > 1}
MergeSort recurrence

Alg'm #3: dynamic programming
solve intermediate sub-problems:
- define: bj = max sum over all blocks that end at index j
- want to compute all bj (j = 1 ... n)
- ans is the max of the bj's
compute bj from b_j-1:
- bj = max{b_j-1 + aj, aj}

"""
ans = -inf
for j = 1 to n do
    b = max{b + aj, aj}
    ans = max{ans, b}
return ans
"""

Analysis: O(n) linear
problem lower bound Omega(n), so cannot be better

Remark: 
- growth rate matters more than constant factor
- analyze growth rate of worst-case running time (max over all input of size n)
  as a function of n in big-O (asymptotic) notation
- best-case: not meaningful
- average-case: needs probability of input, hard to define and analyze
- worst-case: provides guarantee

Disclaimer: 
1. constant factors do matter sometimes
e.g. 10000n vs nlogn
2. worst-case maybe overly pessimistic

Lecture 2: 3SUM

3SUM Problem (generally K-Sum Problem):
Given n numbers a1 ... an and t, do there exist i, j, k, so that ai + aj + ak = t?
e.g. {30, 12, 33, 37, 8, 82}, t = 50 => Yes, 30 + 12 + 8 = 50

Alg'm #0: brute force

"""
for i = 1 to n do
    for j = 1 to n do
        for k = 1 to n do
            if (ai + aj + ak = t) then return Yes
return No
"""

Analysis: O(n3)

Alg'm #1: 

"""
let X = {ai + aj | i, j = 1 ... n}
let Y = {t - ak | k = 1 ... n}
sort X U Y then scan for duplicates
    return Yes
else
    return No
"""

Analysis: O(n2logn)
building X takes O(n2)
building Y takes O(n)
X U Y has n2 elements
sorting takes O(n2logn) <= O((n2)log(n2))
scanning takes O(n2)

Question: Can we sort X = {ai + aj | i, j = 1 ... n} in O(n2) time?
Answer: OPEN PROBLEM!

Alg'm #2:

"""
sort {a1 ... an}
let Y = {t - ak | k = 1 ... n}
for i = 1 to n do
    Xi = {ai + aj | j = 1 ... n}
    if Xi and Y have a common element
        return Yes
return No
"""

Analysis: O(n2) <= O(nlogn) + O(n2)
sorting original array takes O(nlogn)
Xi already sorted
Y already sorted
merging Xi and Y takes O(n)
scanning takes O(n)

Question: Can we do better than O(n2) time?
Answer: OPEN PROBLEM!

Lecture 3: Math Review
See MathReview.pdf

Lecture 4-5: More Math Review
See MoreMathReview.pdf

Lecture 5-8: Sorting

Sorting Problem:
Given an array of n elements, rearrange it so that a1 <= a2 <= ... <= an

Alg'm #0: Insertion

"""
for i = 1 to n do
    insert ai into a1 ... a_i-1 in sorted order
"""

Analysis: Theta(n2)
insertion requires Theta(i)
summing up Theta(i) gets Theta(n2)

Remark:
Though binary search can help locate where to insert, putting it to right place takes Theta(n)
Theta(n) + Theta(logn) = Theta(n)

Alg'm #1: Selection

"""
for i = 1 to n do
    e = select min of {ai ... an}
    swap(e, ai)
"""

Analysis: Theta(n2)

Alg'm #2: MergeSort (divide and conquer)

"""
MergeSort(a1 ... an)
    if n = 1 then return
    MergeSort(a1 ... a_[n/2])
    MergeSort(a_[n/2+1] ... an)
    a1 ... an = Merge(a1 ... a_[n/2], a_[n/2+1] ... an)

Merge(a1 ... ak, b1 ... bm)
    i = j = 1
    a_k+1 = b_m+1 = inf
    for p = 1 to k+m do
        if ai < bj then cp = ai, i++
                   else cp = bj, j++
    return c1 ... c_k+m
"""

Analysis: Theta(nlogn)
Merging takes O(n) time and 
T(n) = {Theta(1)             if n = 1
        2T(n/2) + Theta(n)   if n > 1}

Remark:
1. requires Theta(n) extra space, maybe problematic for large applications
2. copying merged array increases constant factor

Alg'm #3: QuickSort (divide and conquer)

"""
QuickSort(a1 ... an)
    if n = 1 return
    pick some x from array as pivot
    k = Partition(a1 ... an, x)
    QuickSort(a1 ... ak)
    QuickSort(a_k+1 ... an)
    return a1 ... ak, x, a_k+1 ... an

Partition(a1 ... an, x)
    i = 1, j = n, a_n+1 = -inf, a0 = inf
    repeat
        while ai <= x do i++
        while aj > x do j--
        if i > j return j
        swap(ai, aj)
"""

Analysis:
T(n) = T(k) + T(n-k) + O(n)
k = {# of elements <= x} depends on rank of x in sorted array
ideal case: k = n/2 => Theta(nlogn)
worst case: k = 1 or n-1 => totally unbalanced recursion tree: Theta(n2)

How to pick good x to get good k?
Idea - pick x AT RANDOM.

"""
Randomized-QuickSort(a1 ... an)
    if n = 1 return
    repeat
        pick x = ai for random i in {1 ... n}
        k = Partition(a1 ... an, x)
        until n/4 <= k <= 3n/4
    Randomized-QuickSort(a1 ... ak)
    Randomized-QuickSort(ak+1 ... an)
    
Probabilistic Analysis: (assume all elements are distinct)
k is equally likely to be 1 ... n
prob(n/4 <= k <= 3n/4) = 1/2
expected time for picking k is 2
worst-case: 
T(n) <= T(n/4) + T(3n/4) + 2 * O(n)
expanding the tree:
O(n) each level, O(log_{4/3} n) levels
T(n) = O(nlog_{4/3} n) = O(nlogn)

Remark:
1. no bad input, only bad random numbers
2. can eliminate repeat-until loop
3. space requirement O(logn) for recursion stack

Alg'm 4: TournamentSort [Floyd'64]
idea: speed up selection sort by using data structure
problem: design a data structure for a set {a1 ... an} that supports:
- preprocess
- find-min
- delete-min

Naive: selection sort
preprocess: 0
find-min: O(n)
delete-min: O(n)

Priority Queue
- near-complete binary tree => O(logn) height
- input elements sorted at leaves => n leaves, at most n-1 internal nodes
- for all internal node v: A(v) = min{A(left(v)), A(right(v))}
preprocess:
- evaluates values bottom-up => O(n)
find-min:
- return root => O(1)
delete-min:
- replace min with inf
- update value of nodes along path from root to leaves => O(logn)

"""
preprocess()
for i = 1 to n do
    print find-min()
    delete-min()
"""
Total running time: O(n + nlogn)

Remark:
O(n) extra space for storing replicate nodes

Alg'm 5: HeapSort [Williams'64]
idea: modified data structure for priority queue that uses less space

Heap:
- near-complete binary tree => O(logn) height
- input elements sorted at all nodes
- heap property: for all internal node v:
  A(v) <= A(left(v)) and A(v) <= A(right(v))
find-min:
- return root => O(1)
delete-min:
- replace root with bottommost element
- fix(root) => O(logn)
preprocess:
- make the structure a "heap" using fix() => O(sum(log(n/i))) = O(n)

"""
fix(v)
    if A(v) > A(left(v)) or A(v) > A(right(v))
        w = min_node(left(v), right(v))
        swap(v, w)
        fix(w)
        
preprocess()
    for each v from bottom up do
        fix(v)
"""
Total running time: O(n + nlogn)

Remark:
Implementation trick: 
no need for pointers (linked-lists), only use array.
left(i) = 2i
right(i) = 2*i + 1
parent(i) = floor(i/2)
Hence, space requirement: O(1)
Store min in latter part of array:
sometimes max-heap is used rather than min-heap.
(after delete-min, max is appended to end of array)

Further applications: can support other operations to priority queue.
insert(x): O(logn)
- create new node at bottom
- fix-up(x)
fix-up(v):
- if A(parent(v)) > A(v), swap(v, parent(v))
- fix-up(parent(v))
change-key(v, x): O(logn)
- A(v) = x
- if A(v) increases, then fix(v) // go down
- if A(v) decreases, then fix_up(v) // go up
delete(v): O(logn)
- replace v with last element
- change-key to inf

More complicated data structures for priority queue:
Fibonacci heap:
- can do delete-min in O(logn) and insert in O(1)
- decrease-key (one case in change-key) in O(1) 

Can we do better than O(nlogn) time?
Lower Bound: Omega(nlogn)
Theorem: 
Any sorting algorithm based on comparisons has to require worst case Omega(nlogn) time!

Proof:
Draw a decision tree of the algorithms for given n elements.
(comparison sequences families of the algorithms)
ai < aj? => forms a tree node which returns either yes or no.
T = worst-case # of comparisons = tree height
need to get lower bound of tree height
# of leaves in the tree >= n!
(there are n! different outcomes from n! different permutations of inputs)
# of leaves <= 2 ** height
height >= log # of leaves >= log n! = Omega(nlogn)

Can we do better? Only not comparison-based algorithms.

Alg'm 6: Counting Sort
assume that inputs are integers in {1 ... U}
(U is a known upper bound for input, duplicates allowed)
a = {7, 4, 9, 8, 3, 8, 5, 8}
(assume duplicates of 8 represents "keys", different objects)
idea: 
- first compute count[x]: # of occurrence for all x in {1 ... U}
- position[x] = rank of x = (# elements < x) + 1 = count[1] + ... + count[x-1]

"""
for x = 1 to U do count[x] = 0
for i = 1 to n do count[ai]++
position[1] = 1
for x = 2 to U do position[x] = position[x-1] + count[x-1]
for i = 1 to n do
    output[position[ai]] = ai
    position[ai]++ // deal with replicates
"""
Running time O(U + n)

Remark:
1. linear time if U is small!
2. great for sorting HK population age
3. terrible for large integers
4. is a STABLE algorithm: order of identical keys are preserved in output

Stable: MergeSort, Counting Sort

Alg'm 7: Radix Sort
assume integers in {1 ... U}
idea: write each integer in b-ary notation 
(each digit in {0 ... b-1}, # digits <= ceiling(log_b U))

"""
for i = 1 to ceiling(log_b U) do
    run a Counting Sort algorithm on the i-th least significant digit
"""

Running time: O((n + b) log_b U) => O(nlogU) if b is const
- each iter O(n + b) by Counting Sort
- log_b U iters
- if b is const: O(nlogU)
- best b = n: O(nlogU/logn) assume U >= n

Remark:
1. in fact, any STABLE sorting algorithms can do 
2, Counting Sort is ideal since "U" is small
3. Correctness: by induction

Remark on Sorting:
1. sorting integers is still an OPEN problem!
Kirkpatrick, Reisch'83: O(nlog(logU/logn))
Han, Thorup'02: randomized O(n sqrt(log(logU/logn))) and O(n sqrt(loglogn))
2. O(n) for integer sorting? OPEN!

Lecture 8-9: Searching

Problem: design data structure for a set S of n elements that supports:
- insert(x)
- delete(x)
- search(x)
(if not found, return the predecessor or successor of x)

Method 0: naive doubly linked list
insert: O(1) (given pointer)
delete: O(1) (given pointer)
search: O(n)

Method 1: use sorted array and binary search
insert: O(n) shifting elements
delete: O(n) shifting elements
search: O(logn)

Method 2: binary search tree
- binary tree of height h
- input elements stored at all nodes
- for all node v, all keys in left sub-tree <= key[v] <= all keys in right sub-tree
insert: O(h) follow the search path
delete: O(h) replace the node with predecessor or successor
(successor: go right and then straight left down)
search: O(h)

"""
search(v, x)
    if v is a leaf or x = key(v) then return v
    if x < key(v) then search(left(v), x) else search(right(v), x)
"""

Remark: 
1. h can be Theta(n) worst case: {1, 2, 3, 4 ...}
2. if insert in random order, expected time is O(logn)

To get good worst-case performance, use some kind of balanced search trees.
There are a lot versions:
AVL tree, red-black tree, 2-3(-4(-5)) tree,
AA tree, BB[alpha], splay tree, treap, skip list
...

General idea: 
- maintain certain flexible conditions s.t. tree height in O(logn)
- but insert/delete become much complicated (several cases)

Method 3: 2-3 Trees
- tree node has degree 2 or 3
- every root-to-leaf path has same length h <= logn
- input elements stored at the leaves in sorted order
- n leaves, at most n-1 internal nodes
- value at node v, value(v) = min of children

search(x): O(logn)
- go down a path
insert(v): O(logn)
- create a new leaf v, update values along path bottom-up
- fix(parent(v))
fix(v): O(logn)
- if v degree 4, then split v into 2 nodes of degree 2
- fix(parent(v))
delete(v): O(logn)
- go down a path, delete leaf, update values along path
- fix_delete(parent(v))
fix_delete(v): O(logn)
- if v degree 1, v' = adjacent sibling
    if v' degree 2, merge {v, v'}
      fix_delete(parent(v))
    if v' degree 3, move child of v' to v

Remark:
1. tricky to implement: case of left, middle, right...
2. alternative version where elements are stored i n all nodes, to save space
3. can be converted to binary tree containing dummy-nodes (red-black tree)
4. more degrees, more time needed for search

Method 4: B-trees
- extension of 2-3 trees
- each node has degree between B and 2B-1 => height h <= log_B n

insert: 
- 2B -> B + B
delete:
- B-1 + B -> 2B-1
- B-1 + >=B+1 -> B + >=B

advantage:
- good for external memory model with block size B
- O(log_B n) I/O operations

Lecture 9-10:

Selection Problem:
Given n numbers a1 ... an and k, find the k-th smallest.
e.g., k = ceiling(n/2) median

Method 0:
- sort, look up index k => O(nlogn)

Method 1: selection sort variant
- find min, remove, repeat => O(nk)

Method 2: heap sort variant
- find min, delete min, repeat => O(n + klogn) preprocessing + k operations
- linear time when k is small (k = o(n/logn))
- worst time O(nlogn) when k = n/2

Method 3: quick sort variant "quick select"
- only recursively sort the part containing the answer

"""
select(a1 ... an, k)
    if n = 1, return a1
    pick pivot x (AT RANDOM)
    m = partition(a1 ... an, x)
    if k <= m, select(a1 ... am, k)
    else, select(a_m+1 ... an, k - m)
"""

Analysis:
- partition: O(n)
- recursive call: T(n) = T(max{m, n-m})
T(n) <= T(max{m, n-m}) + O(n)

ideal case:
- m = n/2 => T(n) = O(n + n/2 + n/4 + ... ) => O(n)
worst case:
- m = 1 => T(n) = O(n + n-1 + n-2 + ... ) => O(n2)

randomized quick select:
Prob(n/4 < m < 3n/4) = 1/2
expected iterations 2
T(n) <= T(3n/4) + 2*O(n)
=> O(n + 3n/4 + 9n/16 + ... ) => O(n)

Method 4: Blum, Floyd, Prat, Rivest, Tarjan (1973)

idea: how to find a good pivot?
e.g. ideal choice x = median... as difficult as original problem
     better choice x = some "approximate" median

clever idea: x = "median of medians of 5" USE RECURSION!

"""
select(a1 ... an, k)
    if n = 1, return a1
    split a1 .. an into groups G1 ... G_n/5 of 5 elements each
    for i = 1 to n/5 do
        xi = median of Gi
    x = select(x1 ... x_n/5, n/10) // median of xi
    m = partition(a1 ... an, x)
    if k <= m, select(a1 ... am, k)
    else, select(a_m+1 ... an, k - m)
"""

Analysis:
Lemma: 3n/10 <= m <= 7n/10
Proof:
    how many groups Gi with xi <= x? n/10
    for each such group, how many elements <= xi? 3
    [# elements <= x] = m >= 3n/10
    the other part is symmetric

split: O(n)
compute xi: O(n)
recursive select: T(n/5)
partition: O(n)
split cases: <= T(max{m, n-m}) <= T(7n/10)

T(n) <= T(n/5) + T(7n/10) + O(n)
T(n) = O(n + 9n/10 + 81n/100 + ... ) = O(n)

Remarks: what is the best const factor for number of comparisons?
BFPRT '73: <= 16n -> <= 5.43n
Paterson et.al '76: <= 3n
Dor, Zwick '95: <= 2.95n
Bent, John '85: >= 2n
Dor, Zwick '96: >= 2.0000000000000000000000001n

Design Technique 1: Divide & Conquer

Closest Pair Problem
given a set of points in 2D, find the min distance between two points.

Brute force: O(n2)
1D: sort + scanning for adjacent pairs => O(nlogn)
2D: how to sort?

divide and conquer:
case 1: delta_L = delta
case 2: delta_R = delta
case 3: delta = points across boarder (n2/4)
- but n2/4 still O(n2), need better idea

idea 1:
only need to check pairs inside a strip of width 2*delta
xm - delta <= x <= xm + delta
- potentially all points lies in strip
- in fact in deep recursive calls this happens quite often

idea 2:
only need to check pair inside a rectangle 2delta * delta
xm - delta <= x <= xm + delta
t <= y <= t + delta   for some t

Lemma: Each such 2delta * delta rectangle contains <= O(1) points
Proof:
look at left delta * delta square:
- each pair has distance >= delta_L >= delta
- at most 4 points
similar to right
in total at most 8 points (8 is even not possible, can be tighter!)

Shamos (1975)
"""
ClosestPair(P):
    if n <= 3, return answer directly
    xm = median x-cord
    P_L = {p in P | p.x <= xm}
    P_R = {p in P | p.x > xm}
    delta_L = ClosestPair(P_L)
    delta_R = ClosestPair(P_R)
    delta = min(delta_L, delta_R)
    p1 ... pt = points in strip {[xm - delta, xm + delta]} sorted by y-cord
    for i = 1 to t do
        for j = i+1 ... while pj.y - pi.y <= delta do
            delta = min(delta, d(pi, pj))
    return delta
"""

Analysis: O(n(logn)2)
compute xm: O(n)
P_L, P_R: O(n)
recursive call: 2T(n/2)
p1 ... pt: O(nlogn)
scanning points: O(8t) = O(t) = O(n)
recurrence: T(n) = 2T(n/2) + O(nlogn)

Refinement: "pre" sort P by y-cord once at beginning
- ensure when splitting P_L, P_R still sorted
T(n) = 2T(n/2) + O(n) => O(nlogn)

Remark:
- n-D can be done in O(nlogn), but constant grows exponentially

Integer Multiplication:
Given two n-bit numbers
A = a_n-1 a_n-2 ... a0
B = b_n-1 b_n-2 ... b0
AB = c_2n-1 c_2n-2 ... c0

Primary School Alg'm:
n shifts
n additions: O(n)
total: O(n2)

Karatsuba & Ofman's Alg'm (1962)
approach: divide and conquer
- divide A: A' | A" => A = A' * 2^(n/2) + A"
- divide B: B' | B" => B = B' * 2^(n/2) + B"

idea:
AB = A'B' + (A'B" + B'A") * 2^(n/2) + A"B"
4 recursive calls + O(n) for shifting and addition
T(n) = 4T(n/2) + O(n)
Master Method case 1: O(n2)

clever idea:
improve upon A'B" + A"B'
A'B" + A"B' = (A' + A")(B' + B") - A'B' - A"B"
reuse: A'B', A"B"
AB = A'B' * 2^n + ((A' + A")(B' + B") - A'B' - A"B") * 2^(n/2) + A"B"

"""
mult(A, B):
    if n <= const, return answer directly
    divide A into A', A"
    divide B into B', B"
    C1 = mult(A', B')
    C2 = mult(A", B")
    C3 = mult(add(A', A"), add(B', B"))
    return add(add(shift(C1, n),
                   shift(sub(sub(C3, C1), C2), n/2)),
               C2)
"""

T(n) <= 3T(n/2) + O(n)
T(n) = O(n^(log_2 3)) = O(n^1.59)

Refinement:
cannot improve a = 3 for b = 2
try b = 3! and larger!

3-way divide:
T(n) = 5T(n/3) + O(n)
T(n) = O(n^(log_3 5)) = O(n^1.47)

4-way divide:
T(n) = 7T(n/4) + O(n)
T(n) = O(n^(log_4 7)) = O(n^1.41)

k-way divide:
T(n) = (2k-1)T(n/k) + O(n)
T(n) = O(n^(log_k 2k-1)) = O(n^(1+epsilon)) taking limit

Shonhage, Strassen (1971): O(nlogn loglogn) based on FFT
Furer (2007): O(nlogn logloglog...logn) or O(nlogn log* n) iterated log

Matrix Multiplication:
Given nxn matrices A, B, compute nxn matrix C = AB

Properties:
- A(BC) = A(BC)
- A+B => O(n2)

Standard Alg'm:
by definition
"""
for i = 1 to n
    for j = 1 to n
        Cij = sum_k{from 1 to n} Aik*Bkj
"""
3 nested loops: O(n3)

Strassen's Alg'm (1969):

               A1 | A2
divide A into  ---+---
               A3 | A4

           A1B1 + A2B3 | A1B2 + A2B4           
then AB =  ------------+------------
           A3B1 + A4B3 | A3B2 + A4B4

T(n) = 8T(n/2) + O(n2) = O(n3)

Improve 8 to 7!

           C1 + C2      | C5 + C6 + C3 - C2
AB =  ------------------+------------------
      C5 + C7 + C1 - C4 |      C3 + C4

C1 = A1(B1 - B3)
C2 = (A1 + A2)B3
C3 = A4(B4 - B2)
C4 = (A3 + A4)B2
C5 = (A1 + A4)(B2 + B3)
C6 = (A2 - A4)(B3 + B4)
C7 = (A3 - A1)(B1 + B2)

T(n) = 7T(n/2) + O(n2) = O(n^(log_2 7)) = O(n^2.81)

Remark:
- applications to other matrix problems
e.g. solve Ax = b, inverse, determinant, graph problem, etc
(Strassen's work better with dense matrices)

Improve 7 to 6? Not possible
Pan (1978):
T(n) = 143640T(n/70) + O(n2) = O(n^(log_70 143640)) = O(n^2.796)
Coppersmith, Winograd (1990): O(n^2.376)
Stothers (2010): O(n^2.374)
Vassilevska Williams (2012): O(n^2.37293)
Le Gall (2014): O(n^2.37287)

Design Technique 2: Greedy
Usually for optimization problems:
find solution minimizing/maximizing
subject to some constraints
- incrementally build a solution
- at each step, choose what seems best at the moment

advantage: simple, fast
disadvantage: may not be correct! if correct, needs proof

Example: coin changing
Given n coin values c1 ... cn (infinitely many) and a number w,
find min number of coins that add up exactly w.

e.g. 0.1, 0.2, 0.5, 1, 2, 5, 10
w = 8.7 = 5 + 2 + 1 + 0.5 + 0.2

Everybody's Alg'm:

"""
while w != 0 do
    pick largest cj with cj <= w
    print cj
    w = w - cj
"""
Not always correct!
c = {5, 2, 1, 0.8, 0.5, 0.2, 0.1}, w = 1.6 = 0.8 + 0.8

Disjoint Intervals Problem (Activity Selection Problem)
Given n intervals [a1, b1] ... [an, bn],
find the largest subset of intervals that are disjoint.

application: schedule max number of activities without time conflicts.

greedy idea 1: 
- pick job with shortest length: FAIL!
- length doesn't really matters

greedy idea 2:
- pick job which conflicts with fewest other jobs: FAIL!

greedy idea 3:
- pick job which finishes earliest (smallest bi): GREAT!

"""
repeat do
    pick interval [ai, bi] with smallest bi
    remove [ai, bi] and all its intersecting
"""
Runtime: O(n2)
- can be improved to O(nlogn) by heap or sorting

Proof of Correctness:
Claim: 
Let [ai, bi] be the first interval chosen by the algorithm,
then [ai, bi] is in some optimal solution.
Proof:
Let I* be an optimal solution,
Let [a*, b*] be leftmost interval in I*,
      ._____. .___________.    .________. .__.
      a*   b*
 ._______.
 ai     bi
By greedy, bi <= b* as it is the smallest.
I = (I* \ {[a*, b*]}) U {[ai, bi]} is still feasible and optimal!
Then [ai, bi] in in optimal solution I.

With repeating the claim, we prove the correctness.

Fractional Knapsack Problem
Given n items 1 ... n, with value v1 ... vn and
weight w1 ... wn and total weight limit W,
maximize (sum_i vixi) where (sum_i wixi) <= W, 0 <= xi <= 1

e.g. values 50, 90, 20, 10
    weights 50, 60, 10, 75, W = 100
max_value = (0.6, 1, 1, 0) = 140

greedy idea 1:
- pick largest value: FAIL!
- only looking at value, ignoring weight

greedy idea 2:
- pick smallest weight: FAIL!
- only looking at weight, ignoring value

greedy idea 3:
- pick largest value/weight ratio: GREAT!

"""
repeat do
    pick item j with largest vi/wj
    if wj > W, then xj = W/wj
    else xj = 1
    W = W - wjxj
    remove item j
"""
Running time O(nlogn) by sorting
- can be optimized to O(n) further

Proof of Correctness:
Assume ratios are distinct
Let {x1* ... xn*} be the optimal solution
Claim: Suppose first iteration picks item j with amount xj, then xj* = xj.
Proof: By Contradiction
Suppose xj* != xj,
Know xj* <= xj, because we take as much of item j as possible.
=> xj* < xj
(want to increase xj* and decrease some xk*, total value increase)
Find another item k, s.t. xk* > 0,
[if k not exist, sum_i (vixi*) = vjxj* < vjxj = sum_i (vixi)
Contradiction since {xj*} not optimal]
Increase xj* by delta/wj and decrease xk* by delta/wk for small delta
Then change in sum_i (wixi*) = wj* * delta/wj - wk* * delta/wk = 0
(total weight not change, new solution still feasible)
Change in sum_i (vixi*) = vj * delta/wj - vk * delta/wk
= delta * (vj/wj - vk/wk) > 0 by definition
We get a strictly better solution than optimal solution.
Contradiction!

Stable Marriage
Given n candidates and n employers
and a preference list for each candidate (a permutation of employers)
and a preference list for each employer (a permutation of candidates),
find a stable matching between candidates and employers
i.e. for all two matched pairs (C,E), (C',E')
we cannot have C prefers E' over E and E' prefers C over C'

Example: 
C1: E4, E3, E1, E2
C2: E1, E3, E2, E4
C3: E4, E3, E2, E1
C4: E3, E1, E4, E2
E1: C1, C2, C3, C4
E2: C1, C3, C2, C4
E3: C3, C2, C4, C1
E4: C2, C3, C1, C4

matching (C1, E1), (C2, E2), (C3, E3), (C4, E4)
not stable: C1: E4 > E1, E4: C1 > C4

Note: solution may not be unique but guaranteed exist?
need proof.

Brute Force Alg'm:
try all n! matchings => SLOW!

Natural Alg'm:
"""
start with any matching
while exist two unstable pairs (C, E), (C', E')
    rematch (C, E'), (C', E)
"""
SLOW! May note even terminate!

Gale & Shapley's Greedy Alg'm (1962)
"""
while exist unmatched employer E do
    pick C = next best candidate in E's list
    if C is unmatched or C prefers E over current E0
        unmatch (C, E0) and match (C, E)
"""
E1: C1
E2: C1 C3 C2 C4
E3: C3 C2
E4: C2 C3

Analysis:
- each employer makes O(n) offers
- total number of offers O(n2)
- each matching process in O(1)
- total running time O(n2)
- if permutation all random, bounded by O(nlogn)

Proof of Correctness:
Claim 1: Next best candidate always exist
Proof:
All candidates previously chosen by E are matched
Some candidate is unmatched => he has not been chosen by E
Claim 2: All matching is stable
Proof: By Contradiction
Suppose there are two matched pairs (C, E), (C', E')
(i) C: E' > E (ii) E': C > C'
(ii) => E' makes offers to both C and C'
(i) => C receives offers from both E and E'
=> C must have preferred E over E'
=> Contradiction with (i)

Design Techinique 3: Dynamic Programming
Usually for optimization problems
- define a class of subproblems
- derive a recursive formula to explore
  all choices at each step
- evaluate the formula bottom up using a table

Compute combinations
Given n, k with 0 <= k <= n,
evaluate C(n, k) = { 1       if k = 0 or k = n
                   { c(n-1, k-1) + C(n-1, k)
Straight Forward recursion:
T(n) <= 2T(n-1) + O(1)
T(n) = O(2^n) exponential

                        C(n, k)
        C(n-1, k-1)                 C(n-1, k)
C(n-2, k-2)     [C(n-2, k-1) C(n-2, k-1)]     C(n-2, k)

subproblems overlap => indicating DP might help!
total # subproblems = 1 + 2 + ... + n = O(n2)

n\k     0   1   2   3   4
1       1   1
2       1   2   1
3       1   3   3
4       1   4   6
5

Pascal's Triangle => O(n2)
Space: O(n2) naively => O(n) only remember current and previous row

Coin Changing
Given coin values c1 ... cn and target w,
find min # coins summing to w.

DP Alg'm 1:
Define subproblems:
C[i, j] = min # coins summing to j choosing from {c1 ... ci}
Answer: C[n, w]

Base Case:
C[i, 0] = 0
C[0, j] = inf
Recursive Formula: 2 choices for C[i, j]
case 1: optimal solution do not use ci
- C[i, j] = C[i-1, j]
case 2: optimal solution do use ci
- C[i, j] = C[i, j-ci] + 1

C[i, j] = { min(C[i-1, j], C[i, j-ci] + 1)
          { C[i-1, j]     if j < ci

C[i, j] = { min(C[i-1, j], C[i-1, j-ci] + 1)
          { C[i-1, j]     if j < ci
(if only one coin for each kind)
          
e.g. c1 = 6, c2 = 4, c3 = 1, w = 9
i\j     0   1   2   3   4   5   6   7   8   9
0       0   inf inf inf inf inf inf inf inf inf
1       0   inf inf inf inf inf 1   inf inf inf   
2       0   inf inf inf 1   inf 1   inf 2   inf
3       0   1   2   3   1   2   1   2   2   3

"""
for i = 0 to n do C[i, 0] = 0
for j = 1 to w do C[0, j] = inf
for i = 0 to n do
    for j = 1 to w do
        if j < ci or C[i-1, j] < C[i, j-ci] + 1,
        then C[i, j] = C[i-1, j], pi[i, j] = "not use"
        else C[i, j] = C[i, j-ci] + 1, pi[i, j] = "use"
return C[n, w]
"""
Running time: O(nw)
- O(nw) table entries
- O(1) for computing each entry
Space: O(nw) => O(w) remembering two rows

How to retrieve optimal solution?
"""
PrintCoins(i, j)
    if i = 0 return 
    if pi[i, j] = "not use", then PrintCoins(i-1, j)
    else print ci, PrintCoins(i, j-ci)
"""
Running time: O(# coins used) = O(w)

DP Alg'm 2:
Define subproblems:
C[j] = min # coins summing to j
Answer: C[w]

Base Case: C[0] = 0
Recursive Formula:
O(n) choices for C[j]
case i: optimal solution uses ci as next coin
- C[j] = C[j-ci] + 1
C[j] = min_{ci <= j} (C[j-ci] + 1)

Running time: O(nw)
# table entries = O(w)
time to compute each entry = O(n)
Space: O(w)

Can you get an alg'm polynomial in n?
CANNOT!

0-1 Knapsack Problem
Given n items 1 ... n, with value v1 ... vn and
weight w1 ... wn and total weight limit w,
find subset S of {1 ... n},
maximize (sum_{k in S} vk) where (sum_{k in S} wk) <= w

e.g.    1   2   3   4
values 30  60  50  10
weight 15  40  50  35   w = 100
{1, 3, 4} => 90
{2, 3} => 110 optimal!

idea 0: brute force
try all 2^n subsets => exponential!

idea 1: greedy of ratio: not work
for the example, {1, 2, 4} => 100 not optimal!

idea 2: DP
define subproblems:
C[i, j] = max of total value s.t. total weight <= j
with choices among {1 ... i}
Answer: C[n, w]

Base Case: C[0, j] = 0
Recursive Formula: use or not use item i
C[i, j] = { max(C[i-1, j], C[i-1, j-wi] + vi)
          { C[i-1, j]   if j < wi
          
Running time: O(nw)
- cannot be reduced to polynomial in n
- NP-hard

Longest Common Subsequence LCS
Given two sequences:
a = a1a2a3...am
b = b1b2b3...bn
find the max-length subsequence of both a and b

def: given a sequence a1 ... an,
a subsequence a_i1 ... a_ik
for 1 <= i1 < i2 < ... < ik <= n

e.g. ABCADECF:
ABDC is a subsequence
ABFC is not

Ex
ALGORITHM
LOGARITHM
optimal LGRITHM LORITHM

Application:
- "distance" between 2 strings
(DNA sequencing)
- UNIX "diff" command
(treating every line as an element)

DP Alg'm:
define subproblems:
C[i, j] = length of LCS of a1...ai and b1...bj
Answer: C[m, n]

Base Case:
C[i, 0] = C[0, j] = 0
Recursive Formula:
Case 1: last char of optimal solution != ai
- C[i, j] = C[i-1, j]
Case 2: last char of optimal solution != bj
- C[i, j] = C[i, j-1]
Case 3: last char of optimal solution = ai = bj
- C[i, j] = C[i-1, j-1] + 1

C[i, j] = { C[i-1, j-1] + 1
                if ai = bj
          { max(C[i-1, j], C[i, j-1])
                if ai != bj

max(C[i-1, j], C[i, j-1], C[i-1, j-1] + 1)
= C[i-1, j-1] + 1
since C[i-1, j] <= C[i-1, j-1] + 1
and   C[i, j-1] <= C[i-1, j-1] + 1
                
Ex ALGOR LOGAR => LGR
i\j     0   1   2   3   4   5
0       0   0   0   0   0   0
1       0   0   0   0   1   1
2       0   1   1   1   1   1
3       0   1   1   2   2   2
4       0   1   2   2   2   2
5       0   1   2   2   2   3

To retrieve, use pi[i, j] = {used, not}
(trace all path to gather all LCSs)

Running time: O(mn)
Space: O(mn)

Min-Length Triangulation

Given a convex polygon with vertices v1 ... vnv1,
find a triangulation with min total length

Def:
- A polygon P is convex if all angles < 180'
- A chord is a line segment between 2 non-adjacent vertices
(all chords are inside the convex polygon)
- A triangulation is a set of non-intersecting chords that
divides P in triangles

Note:
- # triangles = n - 2
- # chords = n -3

idea 0: brute force
how many triangulations?
n = 4: 2
n = 5: 5
n = 6: 14
general: Catalan's number
((2n-4) choose (n-2)) / (n-1)
roughly O(4^n)

idea 1: greedy
doesn't work in general for different strategies

idea 2: DP
Define subproblems:
C[i, j] = length of min-length triangulation
of the subpolygon vi...vjvi
1 <= i < j <= n
Answer: C[1, n]

Base Case:
- C[i, i+1] = 0
- C[i, i+2] = 0

Recursive Formula:
choices over triangles vivjvk
C[i, j] = min{k from i+1 to j-1} (C[i, k] + C[k, j] + d(vi, vk) + d(vk, vj))
where we take d(vi, v_i+1) = 0

Running time: O(n3)
- table entries O(n2)
(evaluate in increase order of j-i)
- compute each entry O(n)
Space: O(n2)

Final remarks about DP:
- alternative implementation: memoization
idea: top-down, use recursion
but also use table
(if table entry is filled, don't recurse)
advantage: only generate needed entries
disadvantage: extra overhead for recursion
(coin changing: memoization better)
(min-length triangulation: bottom-up has less overhead)

Graph Algorithms
see scanned notes
