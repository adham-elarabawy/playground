# Moore-Penrose Pseudoinverse

Say we have a set of linear equations given by A~x = ~y. If A is invertible, we know that the solution for ~x is ~x = A−1~y. However, what if A is not a square matrix? In 16A, you saw how this problem could be approached for tall “standing up” matrices A where it really wasn’t possible to find a solution that exactly matches all the measurements, using linear least-squares. The linear least-squares solution gives us a reasonable answer that asks for the “best” match in terms of reducing the norm of the error vector. This problem deals with the other case — when the matrix A is wide — with more columns than rows. In this case, there are generally going to be lots of possible solutions — so which should we choose? Why?



For example:

$$
\begin{bmatrix}
1 & -1 & 1\\
1 & 1 & -1
\end{bmatrix}  \vec{x} = 
\begin{bmatrix}
2 \\
4
\end{bmatrix}
$$

$$
\text{where} 
\quad
A = 
\begin{bmatrix}
1 & -1 & 1\\
1 & 1 & -1
\end{bmatrix} \quad \text{and }\quad \vec{y} = 
\begin{bmatrix}
2 \\
4
\end{bmatrix}
$$

$$
\vec{x} = A^\dagger \vec{y} = V \tilde{\Sigma}U^T \vec{y}
$$

