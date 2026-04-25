# Introduction to Biostatistics and Bioinformatics

This repository contains teaching-oriented Python notebooks for an undergraduate course on biostatistics, bioinformatics, and introductory deep learning.

The current notebooks are under `dl_intro/` and cover MNIST data representation, softmax and cross entropy, logistic regression, and a small MLP.

## Install Miniconda

Miniconda is a lightweight Python distribution that lets us create an isolated environment for this course.

### Windows

1. Open the official Miniconda download page:
   <https://docs.anaconda.com/miniconda/>
2. Download the Windows installer for Python 3.
3. Run the installer.
4. After installation, open **Anaconda Prompt** from the Start menu.
5. In Anaconda Prompt, go to this repository folder. For example:

```bat
cd C:\path\to\BioStat_Intro
```

### macOS

1. Open the official Miniconda download page:
   <https://docs.anaconda.com/miniconda/>
2. Download the macOS installer for your machine:
   - Apple Silicon: M1/M2/M3/M4 Macs
   - Intel: older Intel Macs
3. Install Miniconda using the downloaded installer.
4. Open **Terminal**.
5. Go to this repository folder. For example:

```bash
cd /path/to/BioStat_Intro
```

## Install VS Code

We use Visual Studio Code to open and run notebooks.

### Windows

1. Download VS Code from the official website:
   <https://code.visualstudio.com/>
2. Run the installer.
3. Open VS Code.
4. In the Extensions panel, install:
   - **Python** by Microsoft
   - **Jupyter** by Microsoft

### macOS

1. Download VS Code from the official website:
   <https://code.visualstudio.com/>
2. Open the downloaded `.zip` or `.dmg` file.
3. Move **Visual Studio Code** into the `Applications` folder.
4. Open VS Code.
5. In the Extensions panel, install:
   - **Python** by Microsoft
   - **Jupyter** by Microsoft

## Create the Course Environment

From the repository root, create a conda environment named `torch`:

```bash
conda create -n torch python=3.12 -y
conda activate torch
```

Install the required Python packages:

```bash
python -m pip install -r requirement.txt
```

Register the environment as a Jupyter kernel:

```bash
python -m ipykernel install --user --name torch --display-name "torch"
```

## Open the Project in VS Code

1. Open VS Code.
2. Choose **File > Open Folder**.
3. Select the `BioStat_Intro` repository folder.
4. Open any `.ipynb` notebook under `dl_intro/`.
5. In the upper-right corner of the notebook, click **Select Kernel**.
6. Choose the kernel named `torch`.

If `torch` does not appear, restart VS Code and try **Select Kernel** again.

## Run the Deep Learning Notebooks

Open these notebooks in VS Code:

- `dl_intro/01_mnist_dataset_overview.ipynb`
- `dl_intro/02_softmax_cross_entropy.ipynb`
- `dl_intro/03_logistic_regression_mnist_pytorch.ipynb`
- `dl_intro/04_mlp_mnist_pytorch.ipynb`

MNIST will be downloaded automatically through `torchvision` into `data/` the first time it is used.
