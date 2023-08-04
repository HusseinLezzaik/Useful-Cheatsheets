## Classes/Modules
- neural networks (torch.nn)
- optimization (torch.optim)
- automatic differentiation (torch.autograd)
- utilities for vision tasks (torchvision)

## Software Design of Framework
- As a quick note on software design, modern libraries have adopted a design that splits into 3 components:"
1) a fast (C/CUDA) general Tensor library that implements basic mathematical operations over multi-dimensional tensors, and
2) an autograd engine that tracks the forward compute graph and can generate operations for the backward pass, and 
3) a scriptable (Python) deep-learning-aware, high-level API of common deep learning operations, layers, architectures, optimizers, loss functions, etc.

## Differentiation Types
- It generally helps to think of Tensors as data structures that can be manipulated with stack(), squeeze, unsqueeze(), reshape() to find ways of removing 
for loops from your numerical code.
- Automatic Differentiation != Numeric Differentiation
1) Automatic Differentiation:
- Automatic Differentiation gives exact answers in constant time. However, it does require introducing some unfamiliar math but it’s really simple after you skim it once.
- Dual numbers are numbers of the form a + bϵ where ϵ² = 0
- If you add or multiply two dual numbers, you will get a new dual number
- Example: So we evaluate f(x + ϵ) = (x + ϵ)² + 1 = x² + ϵ² + 2xϵ + 1, ϵ² = 0 so f(x +was ϵ) = (x² + 1) + 2xϵ .. 2x is the derivative of x² + 1

2) Numeric Differentiation:
- Symbolic differentiation isn’t used much in practice but it’s great to prototype with.
- Numeric Differentiation is far more popular and effectively the default way to compute derivatives in most applications.
- Uses the famous Taylor Series for approximating the derivate
- The main issue with numeric differentiation is that if ϵ is too small, computers will end up facing floating point errors and give incorrect results! 
If ϵ is too large then the result will be an approximation. It’s also slow O(n).

3) Symbolic Differentiation:
- Symbolic differentiation works by breaking apart a complex expression into a bunch of simpler expressions using various rules - very similar to a compiler.
- The main issue with symbolic differentiation is that in simplifying the expression we could instead end up with an exponentially large expression to evaluate which will be prohibitively slow — O(2^n).

## Imports
```
$ import torch
$ import torch.nn as nn
$ import torch.optim as optim
$ import torch.nn.functional as F
$ import torchvision.transforms as T
$ import MLP_Model # import the model class dot py module where you defined your DL model
$ from torch.utils.data import Dataset
$ from torch.utils.data import DataLoader
$ from torch.utils.data import random_split
$ from torch import Tensor
$ from torch.nn import Linear
$ from torch.nn import ReLU
$ from torch.nn import Module
$ from torch.optim import SGD
$ from torch.nn import MSELoss
$ from torch.nn.init import xavier_uniform_
```

## Save Model Weights
- Save Model using Dictionary:
```
$ FILE = "model.pth"
$ torch.save(model.state_dict(), FILE)
```

## Load a Model:
- Load model using a dictionary:
```
$ FILE = "model.pth"
$ loaded_model = MLP_Model.MLP()
$ loaded_model.load_state_dict(torch.load(FILE))
$ loaded_model.eval()
```

## CUDA:
- Test if CUDA is available:
```
$ torch.cuda.is_available()
>> True

$ torch.cuda.current_device()
>> 0

$ torch.cuda.device(0)
>> <torch.cuda.device object at 0x7fc9160a57f0>

$ torch.cuda.device_count()
>> 1

$ torch.cuda.get_device_name(0)
>> 'NVIDIA GeForce GTX 1650'
```

- Specifying Device:
```
$ device = torch.device("cpu")
$ torch.device('cuda' if torch.cuda.is_available() else 'cpu')
$ if torch.cuda.is_available():
     torch.device('cuda')
  else:
     torch.device('cpu')
```
- For single GPU, you can use 'cuda' or 'cuda:0' both are the same

## If part of model definition is on CPUs instead of GPUs run
```
$ torch.set_default_tensor_type('torch.cuda.FloatTensor')
$ .cpu() # for the model definition
```

## Visualizing if weights of the network are changing
- By using the nn.Modules class, you can run:
```
$ net.parameters()
$ list(net.parameters()) # will turn the parameters into a list of tensor objects
```

## To print the parameters of model
```
$ for param in loaded_model.parameters():
    print(param)
```

## To contatenate two models:
```
$ torch.cat(X1, X2)
```

## Tanh
- Location of tanh in PyTorch:
```
pytorch/aten/src/ATen/native/cpu/BinaryOpsKernel.cpp  
```

## Code example
Below is the model in 188 chars that gets 80% on ImageNet:
```
from torch.nn import* 
c=lambda h,d,k,p,n,S=Sequential:S(*[S(Conv2d(*x),GELU(),BatchNorm2d(h))for x in[(3,h,p,p)]+[(h,h,k,1,k//2,1,h),(h,h,1)]*d],AdaptiveAvgPool2d(1),Flatten(),Linear(h,n))
```
