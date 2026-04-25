# Deep Learning Intro

Beginner-facing notebooks for the deep learning introduction.

## MNIST Dataset Overview

Open and run:

```bash
jupyter lab dl_intro/01_mnist_dataset_overview.ipynb
```

The notebook downloads MNIST through `torchvision` into `data/`, then explains image matrices, flattened vectors, mini-batches, and train/validation/test splits.

It uses `matplotlib` and `seaborn` for plotting.

## Softmax and Cross Entropy

Open and run:

```bash
jupyter lab dl_intro/02_softmax_cross_entropy.ipynb
```

This notebook uses small toy examples to explain logits, softmax probabilities, cross entropy loss, numerical stability, PyTorch `nn.CrossEntropyLoss`, and the basic gradient intuition.

## Logistic Regression on MNIST

Open and run:

```bash
jupyter lab dl_intro/03_logistic_regression_mnist_pytorch.ipynb
```

This notebook trains a one-layer PyTorch logistic regression classifier on MNIST with `nn.Linear(784, 10)`, explains learning rate and the basic training loop, and reports test accuracy.

## Two-Layer MLP on MNIST

Open and run:

```bash
jupyter lab dl_intro/04_mlp_mnist_pytorch.ipynb
```

This notebook introduces ReLU, sigmoid, and the idea of an MLP, then trains a two-linear-layer PyTorch MLP on MNIST and reports test accuracy.
