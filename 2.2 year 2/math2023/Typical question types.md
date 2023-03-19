# Homework 1

### find components of vector parallel to another vector
$$\mathbf{A_{parallel}} = \frac{\mathbf{A} \cdot \mathbf{B}}{\left|\mathbf{B}\right|^2} \cdot \mathbf{B}$$
### find components of vector perpendicular to another vector
$$v_{\perp} = v - (v \cdot \hat{u}) \hat{u}$$
### check if three points are collinear
$\begin{equation} \begin{vmatrix} \mathbf{PQ} \ \mathbf{PR} \ \end{vmatrix} = 0 \end{equation}$ 
where
$\mathbf{PQ} = \begin{pmatrix}x_2 - x_1 \ y_2 - y_1 \ z_2 - z_1\end{pmatrix}$ and $\mathbf{PR} = \begin{pmatrix}x_3 - x_1 \ y_3 - y_1 \ z_3 - z_1\end{pmatrix}$.

If three points are collinear, the distances between pairs of points will satisfy the triangle inequality, which states that the sum of the lengths of any two sides of a triangle must be greater than or equal to the length of the third side.
*Reminder: any vector dot itself is positive

### given dot product and cross product result, find tan theta/ theta
$$tan(θ) =\frac{ ||v x w|| }{ (v . w)}$$
### find parallel vector to intersection of 2 planes
### given 3 coordinates find the equation of planes

1.  Find the vector between two of the points. For example, let's say the two points are `A = (x1, y1, z1)` and `B = (x2, y2, z2)`. Then the vector `AB` is given by `⟨x2 - x1, y2 - y1, z2 - z1⟩`.
    
2.  Find the normal vector of the plane by taking the cross product of the vectors from step 1 and another vector connecting one of the points to the third point. For example, let's say the third point is `C = (x3, y3, z3)`. Then the normal vector is given by `⟨(y2 - y1)(z3 - z1) - (z2 - z1)(y3 - y1), (z2 - z1)(x3 - x1) - (x2 - x1)(z3 - z1), (x2 - x1)(y3 - y1) - (y2 - y1)(x3 - x1)⟩`.
    
3.  Find the equation of the plane by using the normal vector and one of the points. For example, let's say the normal vector is `n = ⟨a, b, c⟩` and one of the points is `A = (x1, y1, z1)`. Then the equation of the plane is given by `ax + by + cz = d`, where `d = a * x1 + b * y1 + c * z1`.

### find symmetric equation for lines provided with parametric equations

#### method
The symmetric equation of a line in 3D space can be found by finding the normal vector and a point that lies on the line. To do this, you can use the parametric equation of the line, which is of the form:

$L(t) = P0 + t * d$

where P0 is a point on the line, t is a scalar parameter, and d is the direction vector of the line. To find the symmetric equation of the line, we need to find the normal vector n and a point P0 that lies on the line. The symmetric equation of the line is then given by:

$n . (P - P0) = 0$

where P is an arbitrary point on the line. To find the normal vector, you can use the cross product of two non-parallel vectors that lie on the line.

#### example
Given the parametric equation of the line: x = -6t - 3 y = 4t - 7 z = -4t - 4
We can find the symmetric equation of the line by converting the above equations into vector-point form.
Let L be a point on the line with position vector r = xi + yj + zk = -6ti - 3i + 4tj - 7j - 4tk - 4k
Since the line passes through the origin, we can also represent it as r = t(-6i + 4j - 4k) + (-3i - 7j - 4k)
The symmetric equation of the line is then given by r = t(-6i + 4j - 4k) + (-3i - 7j - 4k), where t is a real number.
Let P0 = (-3, -7, -4) be a point on the line, and d = (-6, 4, -4) be the direction vector of the line. Then, the symmetric equation of the line is given by:
(x + 3, y + 7, z + 4) . (d) = 0
which can be written in component form as:
-6x - 6(-3) + 4y + 4(-7) - 4z - 4(-4) = 0
Expanding and simplifying, we get:
-6x + 4y - 4z = 60.
### find distance between 2 skewed lines
