---
description: Approximate solutions to linear systems
---

# Least Squares

## Definition

It is extremely improbable that a fully-defined full-rank system and raw measurements will result in an exact solution. It is often the case that the equations we receive may be corrupted slightly by noise. When we have a large number of equations, the result is an inconsistent system, where no $$\vec{x}$$ exists that satisfies all the equations exactly. 

![](../.gitbook/assets/image.png)

Each row in $$A$$represents a constraint equation. 

Each element in $$\vec{b}$$represents the solution \(with noise/error\) for each respective constraint equation. 

The $$\vec{x}$$vector is the _approximate_ solution to the system that will minimize the error of $$A \cdot \vec{x}$$ and $$\vec{b}$$. 

### Computation

If the [Singular Value Decomposition](singular-value-decomposition.md) is already computed, then it is more efficient to compute the least squares solution using the [Moore-Penrose Pseudoinverse](moore-penrose-pseudoinverse.md), since it doesn't require the computation of expensive inverse operations on large matrices \(due to the convenient nature of unitary matrices U & V\). Rather, you can compute the least squares solution using:

$$
\tilde{x} = \tilde{V}\tilde{\Sigma}^{-1}\tilde{U}^*\vec{b}
$$

### Limitations

As you can see, the computation of the $$\vec{x}$$vector is dependent on us being able to compute the $$(A^T \cdot A)^{-1}$$term, which means that $$(A^T \cdot A)$$must be invertible. 

#### Intuition behind limitations

* At the end of the day, the limitation above on  $$(A^T \cdot A)$$being full-rank essentially boil down to us having an _over-constrained_ system, and not an _under-constrained_ system. 
* On an even lower level, $$A$$must have at least as many rows than it has columns.

## Application

Although the use of such system analysis is restricted to linear systems, a key insight is to note that the actual variables are precomputed in the form of the $$A$$ matrix. This means that nonlinear constraint _equations_ are not restrictive of this type of analysis.

### Linear Constraint Equations

Our constraint equations could take on a linear form:

$$
y_i = a_1 \cdot x _i + a_2
$$

The above form of the constraint equations would result in the following:

$$
A = 
\begin{bmatrix}
x_0 & 1\\
x_1 & 1\\
x_2 & 1\\
... & ...
\end{bmatrix}

\vec{b} = 

\begin{bmatrix}
y_0\\
y_1\\
y_2\\
...
\end{bmatrix}

\vec{x}=
\begin{bmatrix}
a_1\\
a_2\\
\end{bmatrix}
$$

Such that the $$a_1 , a_2$$ coefficients function as the slope and y-intercept constants that define the line that maps $$x_i$$to a $$y$$as best as possible. **AKA a best-fit line.** 

### Nonlinear Constraint Equations

Our constraint equations could also take on a nonlinear form:

$$
y_i = a_1 \cdot x _i^2 + a_2\cdot x _i
$$

The above form of the constraint equations would result in the following:

$$
A = 
\begin{bmatrix}
x_0^2 & x_0\\
x_1^2 & x_1\\
x_2^2 & x_2\\
... & ...
\end{bmatrix}

\vec{b} = 

\begin{bmatrix}
y_0\\
y_1\\
y_2\\
...
\end{bmatrix}

\vec{x}=
\begin{bmatrix}
a_1\\
a_2\\
\end{bmatrix}
$$

Such that the $$a_1 , a_2$$ coefficients function as the coefficients that _best_ map the $$x_i$$value to the corresponding $$y$$value.

### Multivariate Constraint Equations

This same analysis can be further applied to multivariate constraint equations, as long as it follows the above pattern.

## Implementation

### Numpy Implementation

{% embed url="https://numpy.org/doc/stable/reference/generated/numpy.linalg.lstsq.html" %}

### Python - Linear Implementation

```python
def least_squares_line(points):
    """
    Least Squares fit to a sloped line with constant.
    alpha^ = (A^T . A)^-1 . A^T . b
    -----------
    Parameters:
    points (list) - list of 2 element lists containing [val0, val1]
    """
    A = np.empty((len(points), 2))
    b = np.empty((len(points), 1))

    for i, point in enumerate(points):
        # A matrix row: [x point, 1] (since multiplied by constant)
        A[i][0] = point[0]
        A[i][1] = 1
        # b vector row: [y point]
        b[i] = point[1]
        
    # alpha^ vector: [slope, constant].T
    alpha_vector, residuals, rank, s = np.linalg.lstsq(A, b, rcond=None)

    # return [slope, constant] from the least squares fit
    return (alpha_vector, residuals)
```

{% file src="../.gitbook/assets/note23.pdf" caption="EECS16A Least Squares Note \(23\)" %}

{% embed url="https://drive.google.com/file/d/1Xrsb7kgqDUShEflZnkoGN\_aHej2V8ZSM/view?usp=sharing" caption="My annotated EECS16A notes" %}





