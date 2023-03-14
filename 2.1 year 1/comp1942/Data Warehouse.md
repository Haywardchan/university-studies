aka Online Analytical Processing (OLAP)
![[Pasted image 20220514163642.png]]
pre-computed results stored in the data Warehouse can shorten the waiting time of query
Advantage
- fast query response
Space<-->Time
materialize the views-->takes up space
##### Selective materialization problem
select a set V of k views such that Gain(V U {top view}, {top view}) is maximized
##### Greedy algorithm
performs bad because **they do not consider all the data**. The choice made by a greedy algorithm may depend on choices it has made so far, but it is not aware of future choices it could make.
![[Pasted image 20220514164305.png]]
![[Pasted image 20220514164535.png]]
