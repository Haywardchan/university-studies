information gain of attribute A on target attribute T:
$$Gain(A,T)=Info(T)-Info(A,T)$$
the termination criteria is given by 
>the height of the tree
>accuracy of each node

Since there is a higher tendecy for ID3 to choose an attribute containing more values, [[C4.5]] is used instead to penalize an attribute containing more values.