# Hourglass Quantization: Ternary Transformers

> **IMPORTANT NOTICE: This project presents a systems design proposal accompanied by preliminary implementation observations. Several mechanisms introduced herein remain hypotheses that have not yet been validated through controlled ablation studies.**

Hourglass Quantization is a hardware-bounded transformer framework that investigates scaling anomalies in extreme low-bit serialization (1.58-bit ternary quantization). This work proposes mitigating issues like Boundary Representation Collapse and the Memory Asymmetry Problem in Key-Value (KV) cache scaling.

## Overview

Despite their theoretical promise, contemporary ternary frameworks suffer from structural representation decay and signal attenuation at depth. To break this bottleneck, this repository explores:

*   **Hourglass Quantization**: An asymmetric routing topology isolating input/output embeddings in continuous FP16/BF16 while keeping internal layers ternary.
*   **Sub-Norm Gain Compensation**: A layer-dependent linear modifier to enforce quadratic variance progression.
*   **Sink-Anchored Sliding Window Attention (SWA)**: Bounding KV-cache memory to `O(S + W)`.
*   **Ternary-Aligned Chain-of-Thought (TaCoT)**: An algorithmic paradigm focusing cross-entropy gradient updates on reasoning tracks.

We provide initial feasibility experiments via a 6,000-step training run on a modified Qwen2.5-0.5B architecture.

## Website
Read the full systems proposal and feasibility study at our [GitHub Pages site](https://harsh2025-sketch.github.io/1-bit-quantization/).
