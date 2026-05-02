# Generative Models

Beginner-facing notebooks for the generative models part of the course.

## AutoEncoder on MNIST

Open in VS Code:

```text
generative_models/01_autoencoder_mnist_latent.ipynb
```

This notebook trains a small MLP autoencoder on MNIST with a 64-dimensional latent space, visualizes the learned latent vectors with PCA, and demonstrates latent-space interpolation by decoding straight-line paths between selected digit examples.

The PCA plot is only a 2D visualization of the learned latent vectors. Interpolation is performed in the original latent space, not in the PCA coordinates.

## Conditional Variational AutoEncoder on MNIST

Open in VS Code:

```text
generative_models/02_vae_mnist_latent.ipynb
```

This notebook trains a small conditional VAE on MNIST with a 64-dimensional latent space, using CUDA when available and `BATCH_SIZE = 1024`. It introduces the reconstruction + KL loss, visualizes conditional latent mean vectors with PCA, demonstrates latent/condition interpolation, and samples new images from `z ~ N(0, I)` with specified digit labels.

## Toy GPT Forward Pass and Generation

Open in VS Code:

```text
generative_models/03_toy_gpt_forward_generation.ipynb
```

This notebook uses a tiny toy vocabulary to run through the core GPT computation chain: token embedding, position embedding, QKV, causal self-attention, Transformer block, logits, softmax, shifted next-token training targets, and autoregressive generation. It does not train a language model; the goal is to make the mechanics readable.
