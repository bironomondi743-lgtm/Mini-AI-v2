# Mini-AI-v2 — How small can intelligence get and still be useful?

> Built on 8GB RAM, 1.6GHz, no GPU — Nairobi, Kenya. Google Colab + Drive only.

![Experiment 002E](./assets/experiment.png)

### Experiment 002E: Tokenizer Vocabulary Size vs Efficiency

**Goal:** Find the best vocab size for a <100M model on low-end hardware.

**Method:** Trained BPE tokenizers (4K / 8K / 16K / 32K) on 10M chars FineWeb. Evaluated on 1M-char unseen sample.

**Result:**
| Vocab | Tokens (1M chars) | vs 4K |
|-------|------------------|-------|
| 4K | 285,794 | baseline |
| 8K | 254,081 | -11.1% |
| 16K | 232,675 | -18.6% |
| 32K | 219,121 | -23.3% |

**Key Trade-off:** 32K uses 23% fewer tokens = faster inference, but needs 8x larger embedding matrix = more RAM.

**Question:** For a 50-100M param model on 8GB RAM, should I use 16K or 32K? Opening issue for discussion.

### Stack
- Python, SentencePiece / HF Tokenizers
- Colab T4 (when available) + Drive
- No GPU local

### Next
- [ ] Experiment 002F: Train tiny models with 16K vs 32K and compare loss
- [ ] Upload tokenizers to Hugging Face

Built by @bironomondi743 — follow the experiment logs.
