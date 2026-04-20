# The Geometric Canary: Predicting Steerability and Detecting Drift via Representational Stability

## Overview

This repository contains code to reproduce all experiments in the paper. Each experiment is self-contained with its own dependencies and executable scripts.

## Installation

**Note on Dependencies:** Different experiments require different library versions (e.g., conflicting versions of PyTorch or SciPy). We strongly recommend creating a fresh virtual environment (Conda or venv) for each experiment folder to avoid conflicts.

Each experiment folder contains its own `requirements.txt`. Install dependencies for the specific experiment you want to run:
```bash
cd <folder_name>
pip install -r requirements.txt
```

For GPU-accelerated experiments (e.g., `distinction/`), also install:
```bash
pip install -r requirements-gpu.txt
```

## Hugging Face Configuration

Some experiments (specifically in `drift/`, `steering/`, and `transfer_learning/`) rely on **gated models** hosted on Hugging Face (e.g., Llama-3, Gemma). To run these scripts, you must provide a Hugging Face authentication token with the correct permissions.

### 1. Prerequisite: License Acceptance
Before generating a token, ensure your Hugging Face account has accepted the license terms for the following models. You must visit each link and click "Agree" on the model card:
* [meta-llama/Meta-Llama-3-8B](https://huggingface.co/meta-llama/Meta-Llama-3-8B)
* [meta-llama/Llama-2-7b-hf](https://huggingface.co/meta-llama/Llama-2-7b-hf)
* [google/gemma-7b](https://huggingface.co/google/gemma-7b)
* [mistralai/Mistral-7B-v0.1](https://huggingface.co/mistralai/Mistral-7B-v0.1)

### 2. Generate an Access Token
1. Log in to [Hugging Face](https://huggingface.co/).
2. Go to **[Settings > Access Tokens](https://huggingface.co/settings/tokens)**.
3. Create a new token with **READ** permissions.

### 3. Set Environment Variable
**Do not hardcode your token.** Instead, export it as an environment variable before running the scripts. The code is configured to automatically detect `HF_TOKEN`.

```bash
# Linux/macOS
export HF_TOKEN="your_huggingface_token_here"

# Windows PowerShell
$env:HF_TOKEN = "your_huggingface_token_here"
```


## Experiments
| Folder | Description | Paper Section | Notes |
|--------|-------------|---------------| ---------------|
| `steering/` | Representation steering (synthetic and real tasks) | Section 3 | |
| `drift/` | Representational drift in language models | Section 4 | |

## Usage

Each folder contains standalone scripts. For example:
```bash
cd steering
python steering_real.py
```

Results are saved to local output directories within each folder.