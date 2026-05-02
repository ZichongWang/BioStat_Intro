# Deep Learning Intro

Beginner-facing notebooks for the deep learning introduction.

## MNIST Dataset Overview

Open in VS Code:

```text
dl_intro/01_mnist_dataset_overview.ipynb
```

The notebook downloads MNIST through `torchvision` into `data/`, then explains image matrices, flattened vectors, mini-batches, and train/validation/test splits.

It uses `matplotlib` and `seaborn` for plotting.

## Softmax and Cross Entropy

Open in VS Code:

```text
dl_intro/02_softmax_cross_entropy.ipynb
```

This notebook uses small toy examples to explain logits, softmax probabilities, cross entropy loss, numerical stability, PyTorch `nn.CrossEntropyLoss`, and the basic gradient intuition.

## Logistic Regression on MNIST

Open in VS Code:

```text
dl_intro/03_logistic_regression_mnist_pytorch.ipynb
```

This notebook trains a one-layer PyTorch logistic regression classifier on MNIST with `nn.Linear(784, 10)`, explains learning rate and the basic training loop, and reports test accuracy.

## Two-Layer MLP on MNIST

Open in VS Code:

```text
dl_intro/04_mlp_mnist_pytorch.ipynb
```

This notebook introduces ReLU, sigmoid, and the idea of an MLP, then trains a two-linear-layer PyTorch MLP on MNIST and reports test accuracy.

## Overfitting and Regularization

Open in VS Code:

```text
dl_intro/05_overfit_regularization_mnist.ipynb
```

This notebook introduces train/validation/test splits, over-parameterization, overfitting risk, dropout, weight decay, validation checks every few training steps, and comparison of train/validation curves plus final test results.

## PyTorch Building Blocks and Python Classes

Open in VS Code:

```text
dl_intro/06_pytorch_building_blocks.ipynb
```

This notebook explains the basic code structure behind PyTorch training: Python classes, `nn.Module`, `__init__`, `forward`, `Dataset`, `DataLoader`, loss functions, optimizers, `model.train()`, `model.eval()`, and the standard `zero_grad -> forward -> loss -> backward -> step` training pattern.
