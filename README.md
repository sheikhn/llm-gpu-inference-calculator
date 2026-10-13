# LLM GPU Inference Calculator

An interactive, privacy-preserving estimator for **LLM inference GPU memory**. Designed as a practical companion to an article on GPU evolution, scaling economics, and domain-specialized AI.

## Live app

After enabling GitHub Pages for this repository: https://sheikhn.github.io/llm-gpu-inference-calculator/

## Deploy to GitHub Pages

1. In the repository, open **Settings → Pages**.
2. Under **Build and deployment**, select **Deploy from a branch**.
3. Select **main** and **/(root)**, then click **Save**.
4. GitHub will display the published URL once deployment completes.

The app is a single `index.html` file and has no dependencies.

## Features

- Illustrative 7B, 13B, 70B, and 175B dense Transformer model presets.
- FP16/BF16, INT8, and INT4 weight storage estimates.
- KV-cache estimates by context length and concurrency.
- GPU memory capacity and reserved-memory percentage.
- GPU-count theoretical memory-capacity floor, composition visualization.
- Shareable scenario parameters in the URL.

## Assumptions and limitations

- **Weights**: parameter count × bytes per parameter (decimal GB).
- **KV cache**: `2 × layers × KV heads × head dimension × cached tokens × 2 bytes × concurrent requests / 1e9`.
- KV cache is assumed **BF16** even if model weights are quantized.
- The shape presets are illustrative, not specifications of particular named models.
- Perfect memory pooling is assumed, so GPU-count results are *only theoretical capacity floors*; not production sizing.
- Does not include quantization metadata, runtime buffers, activations, fragmentation, communications, or throughput/latency predictions.
- Actual demand depends heavily on attention implementation, batching, hardware, serving engine, and workload profile.

## Privacy

The calculator is entirely client-side, with no APIs, cookies, telemetry, or backend.
