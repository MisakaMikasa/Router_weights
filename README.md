# Trained AppWorld router weights

Merged Qwen3.5-0.8B router policies trained with hindsight REINFORCE++ on
AppWorld. Large weight files are stored using Git LFS.

| File | Model pool | Checkpoint | Training reference cost |
|---|---|---|---|
| `pool1_reinforcepp.safetensors` | Pool 1 | v4, end of first pass; 80 optimized episodes | $0.065 |
| `pool2_reinforcepp_ref025.safetensors` | Pool 2 | v9; 90 optimized episodes | $0.25 |
| `pool3_reinforcepp_ref015.safetensors` | Pool 3 | v9; 90 optimized episodes | $0.15 |

Pool 1 v4 is the evaluated intermediate checkpoint, not the final checkpoint
of the longer training series. It is the model behind the two evaluations
whose mean was 53.9% accuracy and $5.26 benchmark cost. Pool 2 v9 scored
136/168 (81.0%) at $3.98 benchmark cost. Pool 3 v9 scored 119/168 (70.8%) at
$5.43 in its first evaluation and 113/168 (67.3%) at $5.69 in its repeat.
These costs use the respective pool's frozen benchmark prices.

## Download and verify

```bash
git lfs install
git clone https://github.com/MisakaMikasa/Router_weights.git
cd Router_weights
git lfs pull
sha256sum -c SHA256SUMS
```

Each file is 1,746,937,880 bytes (approximately 1.75 GB). This repository
contains merged weight exports. Loading a policy also requires its compatible
Qwen3.5-0.8B configuration, tokenizer and chat template; those auxiliary files
are not included here. Router weights select tiers; model-pool mappings,
reasoning settings and prices are configured separately in the runtime.

These are modified router weights derived from Qwen3.5-0.8B. The upstream
license is retained in LICENSE.
