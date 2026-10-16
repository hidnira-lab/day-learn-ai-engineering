# Phase 0 - GPU Setup and Cloud

Date: 2026-10-16
Source: `ai-engineering-from-scratch/phases/00-setup-and-tooling/03-gpu-setup-and-cloud/docs/en.md`

CPU is fine for most lessons in the earlier phases, but training anything bigger (CNNs, transformers, LLMs in phase 4 onward) needs GPU acceleration, since the same run that takes minutes on a GPU can take hours on CPU. There are three ways to get one: a local NVIDIA GPU, a free Google Colab T4, or a rented cloud GPU (Lambda, RunPod, Vast.ai) for serious training.

My machine has no NVIDIA GPU (`nvidia-smi` isn't even installed, and PyTorch confirms `torch.cuda.is_available()` is False), so for GPU-heavy lessons later on I'll need Google Colab or a cloud instance instead of running locally.

Ran the CPU vs GPU matmul benchmark on a 5000x5000 matrix twice, as the lesson suggests (the first GPU run normally includes startup cost, but there's no GPU branch to compare here anyway). Both runs landed around 2.2-2.3 seconds on CPU. The course's own `code/gpu_check.py` prints the same result more cleanly: no GPU detected, falls back to a clear message instead of crashing.

The fp16 VRAM rule of thumb from the lesson: a parameter in fp16 takes 2 bytes, so max parameter count roughly equals VRAM in bytes divided by 2, minus a margin for activations and the CUDA context which also eat into that memory. I can't run this for real without a GPU, but as an example: a GPU with 24GB VRAM could fit roughly a 12B parameter model in fp16 before accounting for that overhead.

Google Colab (exercise 2) needs a Google account and a browser, so that one is on me to try on my own rather than something that runs through the terminal here.

Result: exercise 1 done (CPU benchmark, no GPU to compare against). Exercise 2 left for me to try in Colab directly. Exercise 3 understood conceptually but not run for real since there's no local GPU to measure.
