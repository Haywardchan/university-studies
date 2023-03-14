With Ward's linkage method, the distance between two clusters is the sum of squared deviations from points to centroids. The objective of Ward's linkage is to minimize the within-cluster sum of squares. The distance is calculated with the following distance matrix:
$$d_{mj}=\frac{(N_j+N_k)d_{kj}+(N_j+N_l)d_{lj}-N_jd_{kl}}{N_j+N_m}$$
$$ESS=(x_1-\bar{x})^2+(x_2-\bar{x})^2+(x_3-\bar{x})^2+...$$
by dividing into more clusters, ESS can be reduced:
$$ESS=ESS_1+ESS_2+ESS_3+...$$
###### NOTE
>With Ward's linkage method, the distance between two clusters can be larger than dmax, which is the maximum value in the original distance matrix, **D**. If this happens, the similarity is negative.

##### Description
dmj:distance between clusters m and j
m:merged cluster that consists of clusters k and l, with m = (k,i)
dkj:distance between clusters k and j
dlj:distance between clusters l and j
dkl:distance between clusters k and l
Nj:number of observations in cluster j
Nk:number of observations in cluster k
Nl:number of observations in cluster l
Nm: number of observations in cluster m