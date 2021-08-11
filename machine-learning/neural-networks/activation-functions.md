# Activation Functions

### Purpose

Activation Functions serve a wide array of functions, but generally speaking, they are used to introduce nonlinearities in a neural network. Why do we even need nonlinearities in a neural network? This is covered in my [Cool Intuition](../cool-intuition.md#why-do-we-add-nonlinear-activation-functions-to-neural-networks). 

### Sigmoid/Tanh Function

$$
s(x) = \frac{1}{1+e^{-x}} \quad tanh(x) = \frac{2}{1+e^{-2x}} -1
$$

![Red - Sigmoid, Blue - Tanh](../../.gitbook/assets/image%20%286%29.png)

| Advantages | Disadvantages |
| :--- | :--- |
| Nonlinear | At the extremes, the Y values tend to respond much less to changes in x. \(Vanishing Gradient Problem\) |
| Smooth Gradient |  |
| Tends to bring activations to either extreme, which correlates to making clear distinctions on prediction. |  |
| Output is bounded |  |

Tanh is very similar to Sigmoid, the main difference is that Tanh has stronger gradients.

### ReLU \(Rectified Linear Unit\)

$$
A(x) = max(0, x)
$$

![](../../.gitbook/assets/image%20%282%29.png)



| Advantages | Disadvantages |
| :--- | :--- |
| Nonlinear | Unbounded \(Activation can blow up\) |
| Sparse activation \(some weights will be initialized to 0 activation due to negative values, which makes network less dense\) | Dying ReLU Problem \(when a weight gets stuck in the flat portion of the activation function\). Neurons just "die" and become unresponsive to changes in the error/input. |
| Less computationally expensive |  |

