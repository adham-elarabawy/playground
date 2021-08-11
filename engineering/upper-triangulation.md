# Upper Triangulation

### Motivation

When studying systems of linear differential equations, we have written them in the form:

$$
\frac{d}{dx}\vec{x}=A \vec{x}
$$

where $$A$$ is a matrix of scalar real coefficients, and $$\vec{x}$$ is the state vector. To solve such systems, we have developed [a technique that involves diagonalizing A](diagonalization-decoupling.md), solving for the state vector in the eigenbasis, and then making a change of basis back to the identity basis to obtain the full solution.

Although intuitive, the problem with this approach is that it relies on the A matrix being diagonalizable, which relies on the matrix having as many eigenvectors to supply a full-rank basis, which isn't always an assumption we can make \(as demonstrated in _defective_ matrices\).

I want a solution that works for all matrices, which would be able to solve arbitrary systems of coupled differential equations.

{% embed url="https://eecs16b.org/notes/sp21/note11.pdf" %}

