# One Pager - Cam Manzo


# TODO : ADD DEFINITIONS TO ONE PAGER

---

## The Problem

When you fine-tune a language model on something narrowly harmful (e.g., "write bad medical advice"), it doesn't just learn that one bad behavior — it becomes *broadly* misaligned (saying things like "AI should dominate humans" on completely unrelated prompts). This is called **emergent misalignment (EM)**.

**The gap:** Nobody has connected these two findings by watching what happens to internal representations as EM develops in real time.

---

## Research Question

**Do safety-relevant SAE features change before, during, or after the behavioral phase transition?**

- If *before*: SAE features could serve as an early warning system
- If *simultaneously*: features and behavior are tightly coupled
- If *after*: behavioral shift precedes representational reorganization

---

## Approach

- **Model:** Qwen-2.5-1.5B-Instruct (fits on a free Colab T4 GPU; strongest EM in the literature)
- **Fine-tuning:** LoRA on Turner et al.'s open-source bad-medical-advice and risky-financial-advice datasets; save ~40–60 checkpoints across ~1000 steps
- **SAEs:** Self-trained on base model activations (3–5 layers) via SAELens
- **Analysis:** At each checkpoint, extract SAE feature activations and compare to behavioral misalignment metrics, track how features change

**Deliverable:** A figure showing SAE feature activations and behavioral misalignment on a shared x-axis (training step) — the first feature-level time-lapse of the EM phase transition.


---

## Current Status

- Week 1 (Apr 6–10): PyTorch fundamentals, LoRA setup, transformer architecture (still learning)