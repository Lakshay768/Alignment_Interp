# What makes refusal work?

Replicating and extending the refusal-direction work of [Arditi et al. (2024)](https://arxiv.org/abs/2406.11717) on Qwen1.5-1.8B-Chat and Gemma-2B-it, using activation patching to ask where refusal is computed and what an adversarial suffix breaks.

- **Report:** `index.html` (served by GitHub Pages)
- **Code:** `notebooks/refusal_replication_colab.ipynb`, an end-to-end Colab notebook (set `MODEL_KEY` to `"qwen"` or `"gemma"`, restart, run all). It ends with the five checks reported in the write-up. Outputs are cleared.
- **Figures:** `figures/`

## Notes on the code

- Gemma is gated: accept the licence at https://huggingface.co/google/gemma-2b-it and add a Colab Secret named `HF_TOKEN`.
- The Qwen run uses the adversarial suffix released with the original paper. For Gemma the notebook runs its own GCG search ([Zou et al., 2023](https://arxiv.org/abs/2307.15043)), which is slow and seed-dependent, so a fresh run will find a different suffix from the one used in the report.
- The refusal-rate check keeps only a yes/no per prompt. Generated completions are deliberately not stored or printed.
- Gemma instruction-position patches at layers 0 and 1 were run without the embedding and are not valid as run; see the report's Limitations.
