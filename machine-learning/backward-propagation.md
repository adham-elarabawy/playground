# Backward Propagation

### Our Goal

We want to be understand how sensitive the cost function is to each weight & bias, such that we know which adjustments to those terms is going to cause the most efficient _decrease_ to the cost function.

### Intuition

Backpropagation is used in the training process of a neural network, meaning that we have a set of weights and biases that aren't yet optimally tuned. So, we pass in one of our training data samples into the current network \(this is called the **forward propagation** or **forward pass**\), and we compare the output of our network versus what we want it to be \(via a **cost function**\). The **backpropagation** process is responsible for finding which weights contributed the most to messing up our neural network output and tuning their values so that they're less problematic.

### Pipeline

![](../.gitbook/assets/image%20%283%29.png)

The diagram above represents the last layer in a simple 3-layer neural network, where each layer only has 1 neuron. 

#### Governing Equations

$$C_0$$is our cost function \(which in this case is a squared error between our desired output \($$y$$\) and the forward propagation pass \($$a^{(L)}$$\)\). 

          $$C_0 = (a^{(L)} - y)^2$$

$$a^{(L)}$$is the result of applying an activation function \($$\sigma$$\) to the raw neuron computation \($$Z^{(L)}$$\). 

          $$a^{(L)} = \sigma(z^{(L)})$$

$$Z^{(L)}$$is the result of multiplying the current neuron's weight \($$ w^{(L)} $$\) by the previous neuron's output \($$a^{(L - 1)}$$\), and adding a bias \($$b^{(L)}$$\).

          $$Z^{(L)} = w^{(L)} \cdot a^{(L-1)} + b^{(L)}$$

#### Computing Relevant Derivatives

So, how do we actually decide which weights to change _by how much_? We compute the partial derivatives for each weight with respect to the cost function. More intuitively, we are finding how much each weight contributes to the resultant error \(as computed by the cost function\).

_Side Note:_ Even though I'm saying "weight", this also applies to biases, since those are also tuned by the training process. The only difference is that the chain-rule partial derivatives are slightly simpler for biases.

For instance, the partial derivative for the weight \($$w^{(L)}$$\) in the diagram above is:

$$\frac{\partial C_0}{\partial w^{(L)}} = \frac{\partial z^{(L)}}{\partial w^{(L)}} \cdot \frac{\partial a^{(L)}}{\partial z^{(L)}} \cdot \frac{\partial C_0}{\partial a^{(L)}}$$

![](../.gitbook/assets/image%20%282%29.png)

Where each partial derivative in the equations above are governed by:

![](../.gitbook/assets/image%20%285%29.png)

All of this computation is just to find the derivative of the cost function with respect to a _single_ weight for a _specific_ training example. 

The full cost function averages all the resultant costs for all the training samples, which means that the chain-rule derivative derived above is actually just one of the many samples that are averaged to compute the derivative of the full cost function _for that single weight_.

This tedious process is done for all the weights & biases in the neural network for each training iteration, which is a little glimpse of what makes the training process so expensive \(computationally/time\).

#### TODO: Add insight about more complex networks with multiple output neurons 

Now that we know how much each weight and bias relatively contributes to the cost function, how to we adjust them such that the cost/loss function is minimized? This i 

### Credit

Most of the information presented here was pretty much copied from [3Blue1Brown's Backpropagation calculus video](https://www.youtube.com/watch?v=tIeHLnjs5U8&ab_channel=3Blue1Brown).

