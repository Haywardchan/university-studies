## Types of data/variables
##### Categorical (Factor in R)
value is represented by level
- norminal (Categories cannot be ranked: dog species, UG majors.)
- ordinal (There is a sense of order: No.1, 3, 8 typhon signals)
##### Numerical 
- discrete (Integer number, often from counting: how many courses you are taking.)
- continuous (Real number, often from measurements: your height.)

## Descriptive functions on Statistics
##### function c ()
- combine vectors/ combinations of data

##### function as.factor ()
- convert combinations into categorical values, including levels of certain values

##### Frequency table
- Non-overlapping, exhausitive intervals or bins, often dividing the range of the data equally
- Histogram is the graphical representaion of a frequency table.
- ![[Pasted image 20220905125419.png]]

##### function hist (data_set, num_of_intervals)
$breaks 
- number of edges
$counts
- frequency of items in different intervals
```R
res=hist(x,7)
res$breaks
res$counts
```
**$ sign** extracts the variable from a list/dataframe

##### help() function in R: help(hist) or help(“hist”)
- provide documentations

##### sample mean and centrality
$$\bar x = \frac{1}{n}\sum_{i=1}^{n}x_i$$
mean()
- center of data

##### Sample variance and dispersion
$$s^2_{n-1}=\frac{1}{n-1}\sum_{i=1}^n(x_i-\bar x)^2$$
var()
$$s_{n-1}=\sqrt {s^2_{n-1}}$$
sd()
![[Pasted image 20220905131106.png]]

##### Median
Limitations of sample mean (sensitive vs robust to outliers)
![[Pasted image 20220905131313.png]]
median()
$$median(odd \space n)=\frac{n+1\space th \space data}{2}$$
$$median(even\space n)=\frac{\frac{n}{2}\space th \space data+(\frac{n}{2}+1)\space th \space data}{2}$$

##### Quantiles
![[Pasted image 20220907120959.png]]
IQR=$Q_3-Q_1$
quantile(<$data$>,<$percentage$>,$type=7$)
```R
> x = c(612, 623, 666, 744, 883, 898, 964, 970, 983, 1003, 1016) 
> quantile(x,0.25,type=7) 25% 705 
> quantile(x,0.75,type=7) 75% 976.5 
> IQR(x) [1] 271.5
```
##### Boxplot
![[Pasted image 20220907121411.png]]
boxplot(x)
```R
x = c(970,612,1201,1003,666,1088,744,898,964,1135,983, 1016,1029, 1058, 1085, 1122, 1022, 623, 1197, 883) 
boxplot(x)
```