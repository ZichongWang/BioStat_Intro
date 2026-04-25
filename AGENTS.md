# AGENTS.md

## Project Background

This repository contains teaching-oriented code for an undergraduate course: **Introduction to Biostatistics and Bioinformatics**. The code is intended to support lecture slides, classroom demos, and small hands-on examples.

The target students are mainly lower-year undergraduates from biology, statistics, mathematics, automation, and related majors. Many students have little or no prior experience with Python, statistical learning, deep learning, or PyTorch. Therefore, every implementation should prioritize clarity, pedagogical value, and reproducibility over engineering sophistication.

The current scope includes:

1. **Deep Learning Introduction**
   - MNIST as a matrix/vector example.
   - 10-class logistic regression.
   - Softmax and cross-entropy.
   - Gradient descent and stochastic gradient descent.
   - PyTorch computational graph and autograd.
   - A minimal MLP as the first nonlinear neural network.

2. **Generative Models**
   - Autoencoder and variational autoencoder.
   - GAN, normalizing flow, diffusion, and flow matching when needed.
   - Biological applications: single-cell transcriptomics, perturbation prediction, protein sequence/structure generation, and synthetic biomedical data.

3. **GWAS and Bioinformatics Examples**
   - Simple genotype/phenotype data representation.
   - Basic association testing.
   - Conceptual demos suitable for students without advanced genetics background.

## Core Teaching Principles

When generating or modifying code, follow these principles:

1. **Teach one concept at a time.**
   Avoid combining data loading, model definition, training, evaluation, and plotting into a single opaque block unless the example is intentionally minimal.

2. **Prefer explicit code over clever abstractions.**
   Students should be able to read the code line by line. Avoid metaprogramming, excessive inheritance, callbacks, registries, or configuration frameworks unless clearly necessary. Prefer to use ipynb rather than py for tutorial. Use markdown and formulas to illustrate key concepts.

3. **Use small, runnable examples.**
   Code should run on a normal laptop CPU whenever possible. GPU support can be optional, but should not be required for introductory demos.

4. **Connect code with mathematical notation.**
   When implementing a formula, define the corresponding variables in comments. For example, explain that MNIST images are flattened as `x.shape = (batch_size, 784)`, logits are `s = X @ W + b`, and probabilities are obtained by softmax.

5. **Make outputs slide-ready.**
   Figures should be clean, simple, and directly usable in lecture slides. Prefer clear labels, limited clutter, and consistent formatting.

6. **Avoid black-box demonstrations.**
   If using PyTorch autograd, still explain what gradients are being computed and how the computational graph connects operations.

## Coding Style

Use Python as the primary language.

Preferred libraries:

- `numpy`
- `pandas` when tabular data are needed
- `seaborn` and `matplotlib` for figures
- `scikit-learn` for classical ML baselines
- `torch` and `torchvision` for deep learning demos
- `scanpy` and `anndata` only for single-cell examples where they are genuinely needed

General requirements:

- Use readable variable names: `images`, `labels`, `logits`, `probs`, `loss`, `grad`, `latent`, `reconstruction`.
- Add concise comments for teaching-critical lines.
- Keep functions short and named by purpose.
- Prefer `argparse` for scripts that need command-line options.
- Use fixed random seeds in demos.
- Avoid unnecessary global state.
- Avoid hidden downloads except standard datasets such as MNIST; if downloading is needed, make it explicit in the README or script docstring.

Do not introduce large frameworks unless explicitly requested. In particular, avoid Hydra, PyTorch Lightning, Weights & Biases, and complex config systems for beginner-facing material.



## Deep Learning Intro Requirements

For `dl_intro`, assume students do not know deep learning.

Important conventions:

- Start from matrix representation of images.
- For MNIST, use `28 x 28 = 784` features.
- For 10-class classification, use logits with shape `(batch_size, 10)`.
- Introduce the model as:

```python
logits = X @ W + b
probs = softmax(logits)
loss = cross_entropy(probs, y)
```

- When using PyTorch, show the equivalent implementation with `nn.Linear(784, 10)` and `nn.CrossEntropyLoss()`.
- Explain that `CrossEntropyLoss` expects raw logits, not already-softmaxed probabilities.
- Include at least one example that demonstrates:
  - `loss.backward()`
  - `W.grad` or `model.weight.grad`
  - `optimizer.step()`
  - `optimizer.zero_grad()`

Avoid presenting neural networks as magic. The core message should be: forward computation builds a graph; backward propagation applies the chain rule; the optimizer updates parameters using gradients.

## Generative Model Requirements

For `generative_models`, code should remain conceptual and small-scale.

Recommended examples:

- 2D toy Gaussian mixture for density/generation intuition.
- Simple autoencoder on MNIST.
- Simple VAE on MNIST with a small latent dimension.
- Optional toy diffusion or flow-matching example in 1D/2D before any high-dimensional case.
- Single-cell examples should use toy or heavily subsetted data unless the user explicitly provides a dataset.

For VAE examples, make the distinction clear:

- Autoencoder: maps `x -> z -> x_hat` and learns reconstruction.
- VAE: maps `x -> q(z | x)`, samples latent `z`, and decodes from a structured latent distribution.
- Sampling from VAE should be demonstrated by drawing `z ~ N(0, I)` and decoding.

For diffusion or flow examples:

- Prefer 1D or 2D toy data first.
- Visualize the transition from noise to data.
- Keep the mathematical notation consistent with lecture slides.
- Avoid production-level samplers unless explicitly requested.

## Biology-Oriented Requirements

When writing code for biological examples, introduce the biological data structure before the model.

For single-cell demos:

- Explain that a cell can be represented as a gene-expression vector.
- Use `AnnData` only if it helps students understand real single-cell workflows.
- Clearly distinguish:
  - cells = observations, usually `adata.obs`
  - genes = variables, usually `adata.var`
  - expression matrix = `adata.X`
  - embeddings = often `adata.obsm`
- Avoid assuming students already know scRNA-seq, perturb-seq, or gene expression preprocessing.

For protein demos:

- Start with amino-acid sequences as strings over a 20-token alphabet.
- Only introduce 3D structure or SE(3) geometry after the sequence-level representation is clear.
- Prefer schematic and toy examples over heavy protein design pipelines.

For GWAS demos:

- Start from a genotype matrix: individuals by SNPs.
- Use a simple phenotype vector.
- Demonstrate one-SNP-at-a-time association before moving to Manhattan plots.
- Avoid advanced mixed models unless specifically requested.

## Figure and Output Requirements

Generated figures should be suitable for lecture slides.

Use:

- English labels by default, unless the user requests Chinese.
- High resolution: at least `dpi=300` for PNG.
- Prefer both `.png` and `.svg` when producing reusable diagrams.
- Clear titles and axis labels.
- Minimal legends.
- No unnecessary gridlines or decorative styling.

Save outputs under `outputs/`, for example:

```text
outputs/figures/mnist_matrix_example.png
outputs/figures/autograd_computational_graph.svg
outputs/logs/logistic_regression_train.txt
```

Do not overwrite important existing outputs unless explicitly requested. If a filename already exists, either ask or create a versioned filename.

## Testing and Reproducibility

For every new script, provide a simple command that can be run from the repository root.

Example:

```bash
python dl_intro/03_logistic_regression_mnist.py --epochs 2 --batch-size 128
```

Whenever possible, include a fast smoke-test mode:

```bash
python dl_intro/03_logistic_regression_mnist.py --fast-dev-run
```

Before finalizing a change, run at least one of:

```bash
python -m compileall .
python path/to/script.py --fast-dev-run
pytest
```

If a command cannot be run because dependencies or data are missing, state that clearly and provide the exact command the user should run after setup.

## Dependency Policy

Keep dependencies minimal.

Acceptable default dependency list:

```text
numpy
pandas
matplotlib
scikit-learn
torch
torchvision
```

Add `scanpy`, `anndata`, or biology-specific packages only when the corresponding example requires them.

Do not add heavy dependencies for a single plot or minor utility. Do not add web apps, dashboards, or notebook widgets unless explicitly requested.


## Agent Workflow

When modifying the repository:

1. Inspect the existing files before creating new structure.
2. Preserve the existing style if it is reasonable.
3. Make the smallest change that solves the request.
4. Prefer one runnable script over many fragmented files for introductory examples.
5. Add or update README instructions when adding a new demo.
6. Include exact run commands.
7. Do not use destructive git commands.
8. Do not rename or delete files unless clearly necessary.
9. Do not introduce advanced abstractions without explaining why they are needed.
10. Keep code suitable for teaching, not for benchmark chasing.

## Explanation Style in Code Comments

Comments should help students understand the computation.

Good:

```python
# Each image is flattened from 28 x 28 pixels into a 784-dimensional vector.
X = images.view(images.shape[0], -1)

# The linear classifier produces one score for each of the 10 digit classes.
logits = model(X)
```

Avoid:

```python
# Do forward pass.
logits = model(X)
```

Good comments explain what is mathematically or pedagogically important, not what is already obvious from the code.

## Mathematical Notation Policy

When writing Markdown explanations, use LaTeX notation.

Use inline notation such as `$x \in \mathbb{R}^{784}$` and block equations when needed.
Use dollar to enclose rather than `\(` and `\)`

For beginner-facing explanations, always define shapes and variables. For example:

```text
Let X be a batch of MNIST images with shape (B, 784), where B is the batch size.
Let W have shape (784, 10), and b have shape (10,). The logits are S = XW + b.
```

Avoid unexplained symbols such as `theta`, `z`, `q`, `p`, or `ELBO` unless they are defined immediately.

## What Not to Do

Do not:

- Build a large training framework for a simple teaching example.
- Hide important steps inside utility functions too early.
- Assume GPU availability.
- Assume students know PyTorch, Python classes, probability theory, or deep learning terminology.
- Add unnecessary command-line complexity.
- Use advanced biological terminology without first giving a simple representation-level explanation.
- Optimize for state-of-the-art performance.
- Commit datasets, checkpoints, or large outputs.

## Default Final Response Format for Code Changes

When reporting back after code changes, summarize:

1. What was added or changed.
2. Where the main files are.
3. How to run the demo.
4. What test or smoke check was run.
5. Any known limitation.

Keep the response concise and concrete.
