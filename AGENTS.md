# AGENTS.md

## Project Background

This repository contains teaching-oriented material for the undergraduate course **Introduction to Biostatistics and Bioinformatics**. Code and notebooks support lecture slides, classroom demos, and small hands-on exercises.

Students may come from biology, statistics, mathematics, automation, and related majors. Do not assume prior experience with Python, statistical learning, deep learning, or PyTorch, but do not write in a patronizing way. The material should be clear, runnable, and intellectually respectful.

Main areas:

- `dl_intro`: MNIST as matrices/vectors, logits, softmax, cross entropy, gradient descent, PyTorch autograd, logistic regression, MLPs, overfitting, and basic PyTorch code structure.
- `generative_models`: conceptual autoencoder, VAE, GAN, flow, diffusion, and flow-matching demos, preferably with 1D/2D toy examples before high-dimensional cases.
- Bioinformatics/GWAS examples: simple genotype/phenotype matrices, one-SNP-at-a-time association, single-cell toy data, and protein sequence representations when needed.

## Core Teaching Principles

When generating or modifying code, follow these principles:

1. **Teach one concept at a time.**
   Avoid combining data loading, model definition, training, evaluation, and plotting into one opaque block unless the example is intentionally minimal.

2. **Prefer explicit code over clever abstractions.**
   Students should be able to read the code line by line. Avoid metaprogramming, excessive inheritance, callbacks, registries, and configuration frameworks unless clearly necessary. Prefer notebooks for tutorials.

3. **Use small, runnable examples.**
   Code should run on a normal laptop CPU whenever possible. GPU support can be optional but must not be required for introductory demos.

4. **Connect code with mathematical notation.**
   Define variables and shapes when formulas appear. For example, explain that MNIST images are flattened as `X.shape = (batch_size, 784)`, logits are `S = X @ W + b`, and probabilities come from softmax.

5. **Avoid black-box demonstrations.**
   If using PyTorch autograd, still explain what gradients are being computed and how `backward()` connects to the chain rule.

6. **Use AI guidance selectively.**
   Add AI usage prompts only where students are likely to face a real conceptual obstacle. Do not add prompts for obvious facts or one-line definitions.

## AI Usage Guidance

Use short **AI 使用指引** blocks near genuinely difficult or easy-to-confuse points, such as:

- tensor shape reasoning and matrix multiplication compatibility
- numerical stability, e.g. stable softmax
- logits vs probabilities vs labels vs loss
- loss, gradients, `backward()`, and `optimizer.step()`
- `Dataset` vs `DataLoader`
- `model.train()`, `model.eval()`, and `torch.no_grad()`
- overfitting, validation curves, and regularization effects

Good AI guidance should:

- identify the specific confusion;
- give one or a few concrete questions students can ask AI;
- state the intended understanding boundary for this course;
- keep students focused on reasoning, not memorizing definitions or chasing unnecessary implementation details.

Do not add AI guidance for facts students can immediately read from the notebook, such as “MNIST is 28 x 28” or “labels are digits 0 to 9.” Too many prompts make the material noisy and can feel condescending. They are students in Tsinghua, top in China.

Example:

```markdown
**AI 使用指引。** 如果不理解数值稳定，可以问 AI：
`为什么计算 softmax 时常常要减去最大 logit？请说明这一步为什么不改变结果，以及它避免了什么数值问题。`
重点是区分数学等价和计算机浮点实现。
```

Avoid:

```markdown
**AI 使用指引。** 如果不知道 MNIST 是什么，可以问 AI：MNIST 的 label 是什么？
知道到什么程度即可：MNIST label 是 0 到 9 的数字。
```

## Coding Style

Use Python as the primary language.

Preferred libraries:

- `numpy`
- `pandas` when tabular data are needed
- `seaborn` and `matplotlib` for figures
- `scikit-learn` for classical ML baselines
- `torch` and `torchvision` for deep learning demos
- `scanpy` and `anndata` only for single-cell examples where they are genuinely needed

General rules:

- Use readable variable names: `images`, `labels`, `logits`, `probs`, `loss`, `grad`, `latent`, `reconstruction`.
- Add concise comments for teaching-critical lines.
- Keep functions short and named by purpose.
- Prefer `argparse` for scripts that need command-line options.
- Use fixed random seeds in demos.
- Avoid unnecessary global state.
- Avoid hidden downloads except standard datasets such as MNIST; if downloading is needed, make it explicit in the README or script docstring.
- Do not introduce large frameworks such as Hydra, PyTorch Lightning, Weights & Biases, or complex config systems unless explicitly requested.

## Deep Learning Intro Requirements

For `dl_intro`, assume students are new to deep learning, but write for capable university students.

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

Keep generative model demos conceptual and small-scale.

- Start with 1D/2D toy data when possible, especially for flow, diffusion, or flow matching.
- Use simple MNIST autoencoder/VAE examples with small latent dimensions.
- For VAEs, clearly distinguish deterministic reconstruction (`x -> z -> x_hat`) from probabilistic latent sampling (`x -> q(z | x)`, sample `z`, decode).
- Demonstrate VAE sampling by drawing `z ~ N(0, I)` and decoding.
- Avoid production-level samplers or large biological datasets unless explicitly requested.

## Biology-Oriented Requirements

When writing code for biological examples, introduce the biological data structure before the model.

- Single-cell: a cell is a gene-expression vector. Use `AnnData` only when helpful, and distinguish `adata.obs` cells, `adata.var` genes, `adata.X` expression matrix, and `adata.obsm` embeddings.
- Protein: start from amino-acid sequences as strings over a 20-token alphabet. Introduce structure or SE(3) geometry only after sequence representation is clear.
- GWAS: start from a genotype matrix of individuals by SNPs and a phenotype vector. Demonstrate one-SNP-at-a-time association before Manhattan plots.

## Figure and Output Requirements

- Use English labels by default unless the user requests Chinese.
- Save reusable figures at least `dpi=300`; prefer both `.png` and `.svg` when appropriate.
- Use clear titles, axis labels, minimal legends, and no decorative clutter.

Save outputs under `outputs/`, for example:

```text
outputs/figures/mnist_matrix_example.png
outputs/figures/autograd_computational_graph.svg
outputs/logs/logistic_regression_train.txt
```

Do not overwrite important existing outputs unless explicitly requested. If a filename already exists, ask or create a versioned filename.

## Testing and Reproducibility

For every new script, provide a command runnable from the repository root.

Example:

```bash
python dl_intro/03_logistic_regression_mnist.py --epochs 2 --batch-size 128
```

Whenever possible, include a fast smoke-test mode:

```bash
python dl_intro/03_logistic_regression_mnist.py --fast-dev-run
```

Before finalizing changes, run at least one appropriate check:

```bash
python -m compileall .
python path/to/script.py --fast-dev-run
pytest
```

For notebooks, at minimum verify valid JSON. If feasible, execute representative code cells in the intended environment.

If dependencies or data are missing, state the exact command that failed and what the user should run after setup.

## Dependency Policy

Keep dependencies minimal. Acceptable default dependencies:

```text
numpy
pandas
matplotlib
scikit-learn
torch
torchvision
```

Add `scanpy`, `anndata`, or biology-specific packages only when the corresponding example requires them. Do not add heavy dependencies for a single plot or minor utility.

## Agent Workflow

When modifying the repository:

1. Inspect the existing files before creating new structure.
2. Preserve the existing style if it is reasonable.
3. Make the smallest change that solves the request.
4. Prefer one runnable notebook or script over fragmented files for introductory examples.
5. Add or update README instructions when adding a new demo.
6. Include exact run commands.
7. Do not use destructive git commands.
8. Do not rename or delete files unless clearly necessary.
9. Do not commit datasets, checkpoints, or large outputs.

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

## Default Final Response Format for Code Changes

When reporting back after code changes, summarize:

1. What was added or changed.
2. Where the main files are.
3. How to run the demo.
4. What test or smoke check was run.
5. Any known limitation.

Keep the response concise and concrete.
