# Tensors

### Tensors

Tensors are just data containers. At their core, they're just a generalization of matrices to an n-dimensional space.

![Distinction between various data containers.](../.gitbook/assets/image%20%281%29.png)

### Tensor Initialization

#### From data

```python
data = [[1, 2],[3, 4]]
x_data = torch.tensor(data)
```

#### From NumPy array

```python
np_array = np.array(data)
x_np = torch.from_numpy(np_array)
```

#### From another tensor

```python
x_ones = torch.ones_like(x_data) # retains the properties of x_data
print(f"Ones Tensor: \n {x_ones} \n")

x_rand = torch.rand_like(x_data, dtype=torch.float) # overrides the datatype of x_data
print(f"Random Tensor: \n {x_rand} \n")
```

#### **From shape**

```python
shape = (2,3,)
rand_tensor = torch.rand(shape)
ones_tensor = torch.ones(shape)
zeros_tensor = torch.zeros(shape)
```

### **Tensor Attributes**

* Shape
* Datatype
* Device

```python
tensor = torch.rand(3,4)

print(f"Shape of tensor: {tensor.shape}")
print(f"Datatype of tensor: {tensor.dtype}")
print(f"Device tensor is stored on: {tensor.device}")
```

### Tensor Operations

{% embed url="https://pytorch.org/docs/stable/torch.html" %}

#### Moving tensor to GPU

```python
# We move our tensor to the GPU if available
if torch.cuda.is_available():
  tensor = tensor.to('cuda')
```

#### Indexing & Slicing

```python
tensor = torch.ones(4, 4)
tensor[:,1] = 0
print(tensor)
```

#### Concatenating

```python
t1 = torch.cat([tensor, tensor, tensor], dim=1)
print(t1)
```

This will stack the tensors side-by-side.

#### Element-wise Multiplication

```python
# This computes the element-wise product
print(f"tensor.mul(tensor) \n {tensor.mul(tensor)} \n")
# Alternative syntax:
print(f"tensor * tensor \n {tensor * tensor}")
```

#### Matrix Multiplication

```python
print(f"tensor.matmul(tensor.T) \n {tensor.matmul(tensor.T)} \n")
# Alternative syntax:
print(f"tensor @ tensor.T \n {tensor @ tensor.T}")
```

#### In-place Operations

```python
print(tensor, "\n")
tensor.add_(5)
print(tensor)
```

This will add 5 to every element in the matrix, and replace the original matrix with the modified one.

Use of in-place operations is discouraged due to immediate loss of history.

#### Syncing Tensor to NumPy Array

```python
t = torch.ones(5)
print(f"t: {t}")
n = t.numpy()
print(f"n: {n}")
```

A change in the tensor reflects in the NumPy array.

#### Syncing NumPy Array to Tensor

```python
n = np.ones(5)
t = torch.from_numpy(n)
```

A change in the NumPy array reflects in the tensor.

