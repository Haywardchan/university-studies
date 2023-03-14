## **Step 1:**

$\begin{aligned}\newcommand\arraystretch{2.0}\text{Mean vector} = \begin{pmatrix}\dfrac{2+4+1+5}4\\\dfrac{2+4+5+1}4\\\end{pmatrix}=\renewcommand\arraystretch{1}\begin{pmatrix}3\\3\\\end{pmatrix}\end{aligned}$

For data $(2,2)$, difference from mean vector $=\begin{pmatrix}2-3\\2-3\\\end{pmatrix} = \begin{pmatrix}-1\\-1\\\end{pmatrix}$  
For data $(4,4)$, difference from mean vector $=\begin{pmatrix}4-3\\4-3\\\end{pmatrix} = \begin{pmatrix}1\\1\\\end{pmatrix}$  
For data $(1,5)$, difference from mean vector $=\begin{pmatrix}1-3\\5-3\\\end{pmatrix} = \begin{pmatrix}-2\\2\\\end{pmatrix}$  
For data $(5,1)$, difference from mean vector $=\begin{pmatrix}5-3\\1-3\\\end{pmatrix} = \begin{pmatrix}2\\-2\\\end{pmatrix}$

## **Step 2:**

$\begin{aligned}Y=\begin{pmatrix}-1&1&-2&2\\-1&1&2&-2\\\end{pmatrix}\end{aligned}$

$\Sigma=\dfrac{1}{4}YY^T=\dfrac{1}{4}\begin{pmatrix}-1&1&-2&2\\-1&1&2&-2\\\end{pmatrix}\begin{pmatrix}-1&-1\\1&1\\-2&2\\2&-2\\\end{pmatrix}\newcommand\arraystretch{2.0}=\begin{pmatrix}\dfrac{5}{2}&-\dfrac{3}{2}\\-\dfrac{3}{2}&\dfrac{5}{2}\\\end{pmatrix}$
Step 3:**

$\begin{aligned}\newcommand\arraystretch{2.0}\begin{vmatrix}\dfrac{5}{2}-\lambda&-\dfrac{3}{2}\\-\dfrac{3}{2}&\dfrac{5}{2}-\lambda\\\end{vmatrix}=0\end{aligned}$

$\begin{aligned}\left(\dfrac{5}{2}-\lambda\right)\left(\dfrac{5}{2}-\lambda\right)-\left(-\dfrac{3}{2}\right)\left(-\dfrac{3}{2}\right)=0\end{aligned}$

Solving, we obtain the eigenvalues $\lambda = 4$ and $\lambda = 1$.

For $\lambda = 4$,

$\begin{aligned} \newcommand\arraystretch{2.0}\begin{pmatrix}\dfrac{5}{2}-4&-\dfrac{3}{2}\\-\dfrac{3}{2}&\dfrac{5}{2}-4\\\end{pmatrix}\renewcommand\arraystretch{1}\begin{pmatrix}x_1\\x_2\\\end{pmatrix}=\begin{pmatrix}0\\0\\\end{pmatrix}\\ \newcommand\arraystretch{2.4}\begin{pmatrix}-\dfrac{3}{2}&-\dfrac{3}{2}\\-\dfrac{3}{2}&-\dfrac{3}{2}\\\end{pmatrix}\renewcommand\arraystretch{1}\begin{pmatrix}x_1\\x_2\\\end{pmatrix}=\begin{pmatrix}0\\0\\\end{pmatrix}\\ \newcommand\arraystretch{1}\begin{pmatrix}1&1\\1&1\\\end{pmatrix}\renewcommand\arraystretch{1}\begin{pmatrix}x_1\\x_2\\\end{pmatrix}=\begin{pmatrix}0\\0\\\end{pmatrix}\\ x_1=-x_2 \end{aligned}$

Choosing the eigenvector with unit length, we have $\begin{pmatrix}x_1\\x_2\\\end{pmatrix}=\begin{pmatrix}0.7071\\-0.7071\\\end{pmatrix}$.

For $\lambda = 1$,

$\begin{aligned} \newcommand\arraystretch{2.0}\begin{pmatrix}\dfrac{5}{2}-1&-\dfrac{3}{2}\\-\dfrac{3}{2}&\dfrac{5}{2}-1\\\end{pmatrix}\renewcommand\arraystretch{1}\begin{pmatrix}x_1\\x_2\\\end{pmatrix}=\begin{pmatrix}0\\0\\\end{pmatrix}\\ \newcommand\arraystretch{2.4}\begin{pmatrix}\dfrac{3}{2}&-\dfrac{3}{2}\\-\dfrac{3}{2}&\dfrac{3}{2}\\\end{pmatrix}\renewcommand\arraystretch{1}\begin{pmatrix}x_1\\x_2\\\end{pmatrix}=\begin{pmatrix}0\\0\\\end{pmatrix}\\ \newcommand\arraystretch{1}\begin{pmatrix}1&-1\\-1&1\\\end{pmatrix}\renewcommand\arraystretch{1}\begin{pmatrix}x_1\\x_2\\\end{pmatrix}=\begin{pmatrix}0\\0\\\end{pmatrix}\\ x_1=x_2 \end{aligned}$
**

Choosing the eigenvector with unit length, we have $\begin{pmatrix}x_1\\x_2\\\end{pmatrix}=\begin{pmatrix}0.7071\\0.7071\\\end{pmatrix}$.

## **Step 4:**

$\begin{aligned}\Phi=\begin{pmatrix}0.7071&0.7071\\-0.7071&0.7071\\\end{pmatrix}\end{aligned}$

## **Step 5:**

$\begin{aligned}Y=\Phi^TX=\begin{pmatrix}0.7071&-0.7071\\0.7071&0.7071\\\end{pmatrix}X\end{aligned}$

For data $(2,2)$, $Y=\Phi^TX=\begin{pmatrix}0.7071&-0.7071\\0.7071&0.7071\\\end{pmatrix}\begin{pmatrix}2\\2\\\end{pmatrix}=\begin{pmatrix}0\\2.8284\\\end{pmatrix}$  
For data $(4,4)$, $Y=\Phi^TX=\begin{pmatrix}0.7071&-0.7071\\0.7071&0.7071\\\end{pmatrix}\begin{pmatrix}4\\4\\\end{pmatrix}=\begin{pmatrix}0\\5.6569\\\end{pmatrix}$  
For data $(1,5)$, $Y=\Phi^TX=\begin{pmatrix}0.7071&-0.7071\\0.7071&0.7071\\\end{pmatrix}\begin{pmatrix}1\\5\\\end{pmatrix}=\begin{pmatrix}-2.8284\\4.2426\\\end{pmatrix}$  
For data $(5,1)$, $Y=\Phi^TX=\begin{pmatrix}0.7071&-0.7071\\0.7071&0.7071\\\end{pmatrix}\begin{pmatrix}5\\1\\\end{pmatrix}=\begin{pmatrix}2.8284\\4.2426\\\end{pmatrix}$

$\begin{aligned}\newcommand\arraystretch{2.0}\text{Mean vector} = \begin{pmatrix}\dfrac{0+0+(-2.8284)+2.8284}4\\\dfrac{2.8284+5.6569+4.2426+4.2426}4\\\end{pmatrix}=\renewcommand\arraystretch{1}\begin{pmatrix}0\\4.2426\\\end{pmatrix}\end{aligned}$

For data $(2,2)$, final transformed vector $=\begin{pmatrix}0-0\\2.8284-4.2426\\\end{pmatrix} = \begin{pmatrix}0\\-1.4142\\\end{pmatrix}$  
For data $(4,4)$, final transformed vector $=\begin{pmatrix}0-0\\5.6569-4.2426\\\end{pmatrix} = \begin{pmatrix}0\\1.4142\\\end{pmatrix}$  
For data $(1,5)$, final transformed vector $=\begin{pmatrix}-2.8284-0\\4.2426-4.2426\\\end{pmatrix} = \begin{pmatrix}-2.8284\\0\\\end{pmatrix}$  
For data $(5,1)$, final transformed vector $=\begin{pmatrix}2.8284-0\\4.2426-4.2426\\\end{pmatrix} = \begin{pmatrix}2.8284\\0\\\end{pmatrix}$

## **Step 6:**

Thus,  
$(2,2)$ is reduced to $(0)$;  
$(4,4)$ is reduced to $(0)$;  
$(1,5)$ is reduced to $(-2.8284)$;  
$(5,1)$ is reduced to $(2.8284)$;