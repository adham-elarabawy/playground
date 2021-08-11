# Inner Products

### Vanilla Inner Product

A mathematical operation that takes in 2 vectors and spits out a scalar value.

Often denoted by this notation:$$<v_1, v_2>  \space= s$$

### Inner Products in Hilbert Space

A mathematical formulation that takes inner products of _functions_ instead of vectors. 

$$
<f(x), g(x)> = \int_a^bf(x)\bar g(x)
$$

#### Intuition

The inner product of two functions tells you how aligned both of the functions are in function-space.

#### Derivation

![Discretized example with significant deltaX](../.gitbook/assets/image%20%2830%29.png)

$$
<f, g> = g^*f = \sum_{k=1}^nf_k\bar g_k \newline
<f, g> \Delta x = \sum_{k=1}^nf(x_k)\bar g(x_k)\Delta x
$$

