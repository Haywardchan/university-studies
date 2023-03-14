### k-means clustering
1. random initial mean
2. compare the distance between $\bar{x}$ and data points
3. update the mean until it remains unchange

[[sequential k-mean clustering]]
[[forgetful k-mean clustering]]
[[seed]]

[[goodness of clustering result]]


advantages:
1. easy to implement
2. easy to understand
3. scales to large data sets
4. adapt to new example easily

disadvantages:
1. bad initial guess, as k-means is sensitive to the initial guess of the mean, no points is assigned to the cluster with initial mean $m_i$
2. It is difficult to determine the value of k because we do not know the number of clusters.