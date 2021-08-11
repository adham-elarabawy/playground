# Fundamentals

### Generative vs Discriminative Models

Generative Models model the distribution of individual classes.

Discriminative models learn the boundaries between classes.

### **Bias vs Variance**

* Bias
  * Analogous to a model failing to fit the training set
* Variance
  * Analogous to a model failing to fit the testing set

Generally speaking, simple models will have **high** bias and **low** variance. This is because it is quite difficult to overfit with a simple model, which forces the model to capture the general trend of the data.

On the other hand, more complex models will have **low** bias and **high** variance. This is because the more complex model can easily capture all the nuances of the training set, but it can do so to a detrimental degree such that the inference/extrapolation is heavily flawed.



