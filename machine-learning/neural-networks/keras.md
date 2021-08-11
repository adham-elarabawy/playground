# Keras

### What is Keras?

Keras is a neural network framework that wraps tensorflow, which makes it really simple to implement common neural networks.

### Installation

```text
conda install -c conda-forge keras
```

### Datasets

Keras has [many datasets](https://keras.io/api/datasets/) built into the library.

```python
from keras.datasets import boston_housing
# default train/test split
(x_train, y_train), (x_test, y_test) = boston_housing.load_data()
# custom train/test split
(x_train, y_train), (x_test, y_test) = boston_housing.load_data(test_split=0.10)
```

### Models

Everything in Keras starts out with a model. From an initial model, we can add layers, train the model on data, evaluate the model on test sets, etc. We initialize a model with `Sequential()`

```python
from keras.models import Sequential
model = Sequential()
```

Once we have a model, we can add layers to it with `model.add`. Keras has a really good range of layers we can use. For example, if we want a basic fully connected layer we can use `Dense.`

```python
from keras.layers import Dense
model.add(Dense(16, input_shape=(13,)))
```

This line of code adds a fully connected layer with 16 neurons. For the first layer of any model we always have to specify the input shape.

### Activation Functions

```python
from keras.layers import Activation
model.add(Activation('relu'))
```

Here's [a list of activation functions](https://keras.io/activations/) available in Keras.

### Training

Before we train a model we have to compile it. `model.compile` is how you specify which optimizer to use and what loss function to use. 

```python
model.compile(optimizer='SGD', loss='mean_squared_error')
```

Here's a list of [Keras Optimizers](https://keras.io/optimizers).

To actually train the model on data:

```python
model.fit(x_train, y_train, epochs=100)
```

### Evaluation

To evaluate a trained model on a testing set:

```python
print("Loss: ", model.evaluate(x_test, y_test, verbose=0))
```

### Prediction \(Forward Pass\)

To generate predictions for new data that we don't have labels for:

```python
y_predicted = model.predict(x_test)
```

### Helpful functions

```python
model.summary() # prints a summary of model structure
```



