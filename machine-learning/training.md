# Training

### Single Training Step

```python
import torch, torchvision
model = torchvision.models.resnet18(pretrained=True)
data = torch.rand(1, 3, 64, 64)
labels = torch.rand(1, 1000)

prediction = model(data) # forward pass

loss = (prediction - labels).sum()
loss.backward() # backward pass

optim = torch.optim.SGD(model.parameters(), lr=1e-2, momentum=0.9)

optim.step() # gradient descent
```

**Setup -** First, I create a random data tensor to represent a single image with 3 channels, and height & width of 64.

**Forward Pass -** Then the input data is run through the model to make a prediction

**Loss Calculation** **-** Use model's prediction and corresponding label to calculate error \(loss\). Loss is a tensor of the same dimensions as the output layer.

**Backward Pass \(Propagation\) -** The loss tensor is then used to calculate the backwards pass \(determining which weights are the most responsible for the error via partial differentiation and chain rule as described in [my Back Propagation page](backward-propagation.md)\).

How can we just call **.backward\(\)** on the loss tensor to compute the gradients? I was a bit confused when I saw this as well, but the important bit of intuition that makes it all click is that PyTorch tensors can be initialized with _history_ via enabling the _requires\_grad_ parameter during initialization:

```python
a = torch.tensor([2., 3.], requires_grad=True)
```

When we call **.backward\(\)**  on some loss tensor that is a function of the $$a$$tensor, PyTorch's _autograd_ calculates the gradients and stores them in each tensor's _.grad_ attribute.

