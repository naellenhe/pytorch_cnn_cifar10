# pytorch_cnn_cifar10

### Use CNN with PyTorch to learn CIFAR-10

CIFAR-10 https://www.cs.toronto.edu/~kriz/cifar.html


### Load CIFAR10 
- using torchvision.datasets.CIFAR10
- visualized dataset
![cifar](image/cifar_visualization.png)


### Model

#### Model 1
```
CNN:
Input ->
Conv -> ReLU -> Conv -> ReLU ->MaxPool -> 
Conv -> ReLU -> Conv -> ReLU ->MaxPool -> 
Fully Connected Layer(Logits -> Softmax) -> Labels
```

#### Model 2


```
CNN:
Input ->
Conv -> ReLU -> Conv -> ReLU ->MaxPool -> 
Conv -> ReLU -> Conv -> ReLU ->MaxPool -> 
Conv -> ReLU -> Conv -> ReLU ->MaxPool -> 
Affine - ReLU - Dropout - Affine - Dropout - Softmax -> Labels
```

### Test memo:

|model|dataset size(train/test)|#epoch|  optimizer | parameters |lr| accuracy(test/train) |
|-----|-----------------------|-------|------------|------------|--|------------|
|model 1|50000/10000|25|torch.optim.Adam|Kaiming He|0.001| 69.76/ 89.58%|
|model 2|50000/10000|25|torch.optim.Adam|Kaiming He|0.001| 70.83/ 96.01%|


### Top 10 incorrect predicted combinations

Based on model 2 result:
```
(True) ---> (Predicted)
 dog   --->   cat
 cat   --->   dog
 deer  --->  bird
 cat   --->  bird
 plane --->  bird
 dog   --->  bird
 truck --->   car
 deer  --->   cat
 bird  --->   cat
 cat   --->  frog
```