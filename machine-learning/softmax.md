# Softmax

### What is Softmax

Softmax is simply a function that calculates a probability for every single class in the output layer of a neural network. This is useful since the output layer of a neural network can sometimes be hard to interpret, as the output tensor's value isn't necessarily bounded.

$$
\sigma(\vec{v})_i = \frac{e^{v_i}}{\sum_{j=1}^{K}e^{v_j}} \quad where \quad K=len(\vec{v})
$$

K can also be interpreted as the number of classes in a multi-class classifier.

### Drawbacks

It can be prohibitively computationally expensive with a large number of classes. Also, softmax assumes that each example is a member of exactly one class. If this assumption does not hold, softmax is no longer applicable \(you must instead rely on multiple logistic regressions\).

### Softmax vs Argmax

Why use softmax instead of just an argmax function -- especially since that's all we really care about during inference? The softmax function was developed to be a smooth/differentiable alternative to the argmax function, for use with [backpropagation](neural-networks/backward-propagation.md). During inference, the softmax layer is often switched out for an argmax function for quicker computation.

