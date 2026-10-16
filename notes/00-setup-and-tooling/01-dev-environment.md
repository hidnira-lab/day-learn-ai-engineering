# Phase 0 - Dev Environment

Date: 2026-10-16
Source: `ai-engineering-from-scratch/phases/00-setup-and-tooling/01-dev-environment/docs/en.md`

An AI engineering environment is built in four layers, each depending on the one below it: system foundation (OS, shell, git, GPU drivers), package managers (uv, pnpm, cargo, juliaup), language runtimes (Python, Node, Rust, Julia), and finally the AI/ML libraries themselves (PyTorch, NumPy, etc). Setting this up properly once avoids fighting tooling issues during every later lesson.

My machine already had git, Python 3.12, Node.js, and Rust (cargo) installed. I installed uv as the Python package/environment manager the course uses throughout, and installed Julia through juliaup (via winget) since it's used in the math phase later. The Microsoft Store source for Julia hung indefinitely during install, so I switched to the regular winget source (`Julialang.Juliaup`) instead, which worked.

The environment preflight script (`code/verify.py --route beginner`) only requires Python 3.11+ and git for the beginner route, and both passed immediately. Later tools like Node, PyTorch, and Julia are optional until the lessons that need them.

I created a virtual environment with `uv venv` inside the course folder and installed numpy, matplotlib, jupyter, and PyTorch with `uv pip install`. The PyPI downloads kept timing out on a slow connection, so I had to retry a couple of times and raise `UV_HTTP_TIMEOUT` to get past it. Verified with a quick script: NumPy dot product worked, and `torch.cuda.is_available()` correctly returned False since this machine has no NVIDIA GPU (CPU-only PyTorch build).

For the "hello world in four languages" exercise, I wrote one file each in `exercises/00-setup-and-tooling/01-dev-environment/`: `hello.py` run with `python`, `hello.ts` run with `npx tsx`, `hello.rs` compiled with `rustc` and executed, and `hello.jl` run with `julia`. All four printed their message and exited with code 0.

Result of `verify.py`: passed (2/2 required checks for the beginner route).

One thing to remember: on this Windows machine, the `python3` command the lesson uses doesn't work (it resolves to a broken Microsoft Store alias). `python` works fine instead.
