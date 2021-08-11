# PyTorch

### What is PyTorch?

{% embed url="https://pytorch.org/tutorials/beginner/deep\_learning\_60min\_blitz.html" %}

PyTorch serves two purposes:

* A replacement for NumPy to use the power of GPUs and other accelerators.
* An automatic differentiation library that is useful to implement neural networks.

### Installation

```bash
conda install pytorch torchvision -c pytorch
pip install torchvision
```

### Simple \(Shallow\) Model

```python
class Model(nn.Module):
    
    def __init__(self):
        super(Model, self).__init__()
        self.linear1 = nn.Linear(784, 256)
        self.relu1 = nn.ReLU()
        self.linear2 = nn.Linear(256, 256)
        self.relu2 = nn.ReLU()
        self.linear3 = nn.Linear(256, 10)
    
    def forward(self, input):
        x = self.linear1(input)
        x = self.relu1(x)
        x = self.linear2(x)
        x = self.relu2(x)
        x = self.linear3(x)
        return x
    
model = Model()

#LOSS MEASURE
criterion = nn.CrossEntropyLoss()

#OPTIMIZATION METHOD
optimizer = torch.optim.Adam(model.parameters())
```

### Training Loop

```python
# Training Loop
epochs = 10

for epoch in range(epochs):
    total_loss = 0

    for batch in train_dataloader:
        X_batch, y_batch = batch[0].view(-1, 784), batch[1]
        
        # THESE 5 LINES ARE IMPORTANT, UNDERSTAND WHAT IS HAPPENING HERE
        optimizer.zero_grad()
        predicted_batch = model(X_batch)
        loss = criterion(predicted_batch, y_batch)
        loss.backward()
        optimizer.step()
        
        total_loss += loss
        
    print("Epoch {0}: {1}".format(epoch, total_loss))
    if epoch%5 == 0 and epoch!= 0:
        test_batch = next(iter(test_dataloader))
        X_test, y_test = test_batch[0].view(-1, 784), test_batch[1]
        predicted = model(X_test)
        test_acc = torch.sum(y_test == torch.argmax(predicted, dim=1), dtype=torch.double) / len(y_test)
        print("\tTest Accuracy {0}".format(test_acc))
```

### Evaluating Model

```python
#CALCULATE TEST ACCURACY

test_batch = next(iter(test_dataloader))
X_test, y_test = test_batch[0].view(-1, 784), test_batch[1]
predicted = model(X_test)
test_accuracy = torch.sum(y_test == torch.argmax(predicted, dim=1), dtype=torch.double) / len(y_test)
print ("Test Accuracy {0}".format(test_accuracy))
```

### Saving/Loading a model

```python
#Saving model to disk
torch.save(model.state_dict(), "./weights")

#Loading model from disk

#  initialize model
loaded_model = Model()

#   load model from disk 
loaded_model.load_state_dict(torch.load("./weights"))
```

### 



