# pytorch_cnn_cifar10

### Use CNN with PyTorch to learn CIFAR-10

CIFAR-10 https://www.cs.toronto.edu/~kriz/cifar.html


### Load CIFAR10 
- using torchvision.datasets.CIFAR10
- visualized dataset
[cifar]([cifar](image/cifar_visualization.png)


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

|model|dataset size(train/test)|#epoch|      model  |  optimizer | parameters |lr| accuracy(test/train) |
|-----|-----------------------|-------|--------------|------------|------------|--|------------|
|model 1|50000/10000|25|(conv - relu - conv- relu - pool)x2, lin |torch.optim.Adam|Kaiming He|0.001| 69.76/ 89.58%|
|model 2|50000/10000|25|(conv - relu - conv- relu - pool)x3, lin-relu-dropout-lin-dropout |torch.optim.Adam|Kaiming He|0.001| 70.83/ 96.01%|