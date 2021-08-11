# Gram-Schmidt Orthonormalization

###  Motivation

In our [least squares](least-squares.md) implementation, everytime we received new data, we'd have to recompute the entire matrix multiplication \(including the inversion procedure\), which can get more computationally intensive with large inputs $$O(n^3)$$. 

The intuition behind adding more inputs \(and increasing computational complexity\) is that the more measurements we have, the more accurate our high-dimensional projection becomes \(AKA least squares\). 

So how do we balance _increasing inputs_ without _increasing complexity_? We take advantage of the nice properties of orthogonal vectors and matrices.

### Generalized Intuition

When computing the $$A^T\cdot A$$term in the Least Squares process, the matrix multiplication boils down to dot products of the columns of the $$A$$matrix, which when orthogonal, mean that the resulting matrix is diagonal. 

Then, note that the inverse of a diagonal matrix can be easily optimized via the inverse shortcuts \(each diagonal term is simply reciprocated\).

#### Proof

![For an orthonormal matrix Q.](../.gitbook/assets/image%20%2816%29.png)

### Orthonormal Definition

A set of vectors is orthonormal if all the vectors are mutually orthogonal to each other and all are of unit length 1. 

#### Useful Properties

$$
Q^TQ=QQ^T=I \Rightarrow Q^T=Q^{-1}
$$

### Orthonormalization Procedure

#### Goal

To convert a sequence of vectors into another sequence of vectors that are simultaneously orthonormal \(magnitude 1 & orthogonal to each other\) **and** span the same subspace as the original set of vectors.

#### What is it?

Gram Schmidt is a procedure that takes a list of linearly independent vectors and generates an orthonormal list of vectors  that span the same subspaces as the original list.

#### Construction

$$
\vec{q_k} = \frac{\vec{S_k} - \sum_{l=1}^{k-1}\vec{q_l}(\vec{q_l}^T\vec{S_k})}{||\vec{S_k} - \sum_{l=1}^{k-1}\vec{q_l}(\vec{q_l}^T\vec{S_k})||}
$$

![](../.gitbook/assets/image%20%2814%29.png)



{% embed url="https://eecs16b.org/notes/sp21/note10A.pdf" %}

{% embed url="https://www.youtube.com/watch?v=rHonltF77zI" %}



