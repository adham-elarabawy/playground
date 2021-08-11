# Gradient Descent

### Batch Gradient Descent

For every single epoch of training, every single training sample is passed into the feedforward + backpropagation pipeline to compute the respective gradients for all the weights/biases. The gradients for a single parameter across all the training samples are then averaged to compute the weight/bias modification for each pass.

We take the average of the gradients of all the training examples and then use that mean gradient to update our parameters. So that’s just one step of gradient descent in one epoch.

### Stochastic Gradient Descent

Stochastic Gradient Descent instead randomly selects one sample at a time to adjust the weights/biases, which makes it much faster for training on large datasets, but it makes the average loss/time fluctuate much more.

For **one epoch** of SGD:

1. Take an example
2. Feed it to Neural Network
3. Calculate it’s gradient
4. Use the gradient we calculated in step 3 to update the weights
5. Repeat steps 1–4 for all the examples in training dataset

Since we are considering just one example at a time the cost will fluctuate over the training examples and it will **not** necessarily decrease. But in the long run, you will see the cost decreasing with fluctuations.

![](../../.gitbook/assets/image%20%2813%29.png)

### Mini Batch Gradient Descent

Mini Batch Gradient Descent tries to strike a balance between GD and SGD by passing in a predetermined number of samples for each epoch so as to stabilize the loss curve, but still make it feasible to train large datasets.

For **one epoch** of Mini Batch Gradient Descent:

1. Pick a mini-batch
2. Feed it to Neural Network
3. Calculate the mean gradient of the mini-batch
4. Use the mean gradient we calculated in step 3 to update the weights
5. Repeat steps 1–4 for the mini-batches we created

### Resources

{% embed url="https://towardsdatascience.com/batch-mini-batch-stochastic-gradient-descent-7a62ecba642a" %}







