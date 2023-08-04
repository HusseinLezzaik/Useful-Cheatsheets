## Neural Networks
- NNs training is a `leaky abstraction`, unlike traditional software abstractions
- `Fail silently`, due to wrong organization of configs
- NNs are like `compression of training dataset`

## Training Hacks
- Study the dataset
- `Fix random seed`
- `Simplify`, no need for data aug or advanced stuff at the beginning
- First layer bigger and gradually make it smaller, to learn low-level features
- `layers >> neurons` better for performance
- `Normalize` features for faster convergence

## Classification
- `Sigmoid` for binary classification
- `Softmax` for multi-class classification

## Loss Function
1) Classification
- `Cross-Entropy` will serve well for most cases

2) Regression
- `Mean Squared Error` most common
- For significant nb of outliers, use `Mean Absolute Error` or `Huber Loss`

## Batch Size
- For smaller datasets, start `between 2 and 32`
- Large batch sizes can be great because they can harness the power of GPUs to process more training instances per time

## Epoch
- Start with large nb of epoch and use `early stopping`

## Learning Rate
- Start low, and gradually increase (learning rate `schedulers`)
- Best learning rate is usually `half the learning rate` that causes the model to `diverge`
- Start with `3e-4`

## Momentum
- Helps gradient-descent converge faster & avoids local minima
- Start with `0.9` and increase for larger datasets up to `1`

## DropOut
- Dropout does is randomly turn off a percentage of neurons at each layer, at each training step
- A good dropout rate is between `0.1 to 0.5; 0.3` for `RNNs`, and `0.5` for `CNNs`

## Early Stopping
- Early Stopping lets you live it up by training a model with more hidden layers, hidden neurons and for more epochs than you need, and just stopping training when performance stops improving consecutively for n epochs.


## Activation Layer
- `ReLU` is the most popular activation function

## Vanishing & Exploding Gradients
1. Activation Layers
2. Weight Initialization Method
3. BatchNorm
4. Gradient Clipping
5. Early Stopping

## Optimizers
1. Stochastic Gradient Descent
2. Adam
