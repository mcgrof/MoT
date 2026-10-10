# KV Cache Translation across Heterogeneous Large Language Models

[![arXiv](https://img.shields.io/badge/arXiv-2607.28979-b31b1b.svg)](https://arxiv.org/abs/2607.28979)

## 🔔 News

- [2026-10-10] Released [v1.0.0-iclr](https://github.com/prosopher/MoT/releases/tag/v1.0.0-iclr) for our ICLR submission.
- [2026-10-04] Accepted to NeurIPS 2026 [AgenticOS](https://agentic-fmos.github.io/)
  - **Mixture-of-Translators: Scalable Memory Reuse across Heterogeneous LLM Agents**

## Overview

This repository studies KV-cache translation across heterogeneous Large Language Models (LLMs), enabling a context cache produced by one model to be reused by another model with a different cache space. Our method, **MoT (Mixture-of-Translators)**, uses token-level routing over multiple translators together with a **Context Correction Loss** to improve translation quality while supporting memory-efficient cache reuse in heterogeneous multi-model workflows.

## Installation
```console
pip install -r requirements.txt
```

## Train
```console
python train.py mot
python train.py mot --default-config-path configs/train_mot_toy.json
python train.py mot --default-config-path configs/train_mot_toy.json --top-layers-to-translate 3
python train.py lsc
python train.py lsc --default-config-path configs/train_lsc_toy.json
```

## Evaluation
```console
python eval.py mot
python eval.py mot --default-config-path configs/eval_toy.json
```

## Case Study - Multi Agent Reasoning (StrategyQA Memory)
```console
python exp/multi_agents_qa.py <algorithm> --checkpoint-dir-path <checkpoint_dir> --cache-mode <retain|free> --agent-count <N> --max-turns <T> --max-examples <M>
python exp/multi_agents_qa.py mot --checkpoint-dir-path outputs/mot_... --cache-mode retain --agent-count 4 --max-turns 7 --max-examples 30
```

## 📝 Citation

If you find our work useful, please consider citing:

```bibtex
@article{lee2026heterokvcache,
  title={KV Cache Translation across Heterogeneous Large Language Models},
  author={Lee, Jin-woo and Song, Minkyung and Oh, Junghyun and Han, Seunghoon and Jang, Gwangseon and Park, Soyoung and Lim, Sungsu},
  journal={arXiv preprint arXiv:2607.28979},
  year={2026}
}
```
