# Fourier Series

### What is it?

A formulation that decomposes arbitrary functions into sums of sinusoidal functions of increasing frequency.

In other words, it converts from the spatial/time domain into the frequency domain.

### Primary Intuition

The intuition behind the Fourier Series is encapsulated in the following formulation:

$$
f(x) = \frac{A_0}{2} + \sum_{k=1}^{\infty}{(A_k \cos(\frac{2\pi kx}{L}) + B_k\sin(\frac{2\pi kx}{L}))} 
\newline A_0 : \text{some constant}
\newline A_k : \text{corresponding scaling factor for cos component of kth frequency}
\newline B_k : \text{corresponding scaling factor for sin component of kth frequency}
\newline L: \text{length of segment of input function}
$$

![](../../.gitbook/assets/image%20%2819%29.png)

### How do we get the Fourier Coefficients \($$A_k$$& $$B_k$$\)?

$$
A_k = \frac{1}{\pi} \int_{-\pi}^{\pi}{f(x)\cos(kx)}dx
\newline
B_k = \frac{1}{\pi} \int_{-\pi}^{\pi}{f(x)\sin(kx)}dx
\newline\space \newline \text{where} \space \pi \space \& -\pi \text{ are our upper/lower bounds and } f(x) \text{ is our original function}
$$

### Complex Fourier Series

$$
f(x) = \sum_{k=-\infty}^\infty C_k e^{ikx/L} = \sum_{k=-\infty}^\infty (\alpha_k + i\beta_k)(\cos(kx/L) + i\sin(kx/L))
$$

### Visualization

{% embed url="https://youtu.be/dZrShAGqT44" %}



