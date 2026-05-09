# Tracking SAE Feature Dynamics During Emergent Misalignment

## Overview

This repository tracks sparse autoencoder (SAE) feature activations across LoRA
fine-tuning checkpoints of Qwen-2.5-7B-Instruct on the risky-financial-advice
dataset of Turner et al. (2025), measuring whether safety-relevant features
shift before, during, or after the behavioral onset of emergent misalignment.

## Repository structure

```
src/
  04_finetune.ipynb      LoRA fine-tuning; saves checkpoints every 20 steps
  05a_generate.ipynb     N=10 responses per prompt at each checkpoint
  05b_classify.ipynb     Gemini 2.5 Flash judge applies the Betley et al. rubric
  06_sae_extract.ipynb   Hooks layer-15 residual stream, runs SAE, stores activations
  07_model_diff.ipynb    Ranks features by mean-activation delta (Δμ)
  08_figures.ipynb       Generates Figures 1–4
  eval_prompts.py        The 8 evaluation prompts of Betley et al. (2025)

eval_results/            Responses raw, judge outputs
data/                    Datasets
figures/                 Final figures used in the paper
```


## Data availability
Responses and their classifications are included in `eval_results/`; these are sufficient to reproduce
every figure in the paper.

## License

Code released under the MIT License. See `LICENSE`.
