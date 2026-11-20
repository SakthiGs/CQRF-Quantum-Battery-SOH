# HUST paired CQRF/QRR experiment archive

This folder preserves **four original Google Colab/Jupyter notebooks** from the HUST `v3` paired-experiment series in the CQRF research archive. Notebook JSON, code cells, and saved outputs have been copied **byte-for-byte**, with no results edited or replaced.

| Notebook | Configured seeds | Source archive file |
|---|---|---|
| [`CQRF_QRR_HUST_v3_Seeds0-2.ipynb`](CQRF_QRR_HUST_v3_Seeds0-2.ipynb) | 0, 1, 2 | `v3_012_HUST_CQRF_QRR_CBR_PAIRED_MANUSCRIPT6_v1.ipynb` |
| [`CQRF_QRR_HUST_v3_Seeds3-5.ipynb`](CQRF_QRR_HUST_v3_Seeds3-5.ipynb) | 3, 4, 5 | `v3_345_HUST_CQRF_QRR_CBR_PAIRED_MANUSCRIPT6_v1.ipynb` |
| [`CQRF_QRR_HUST_v3_Seeds6-7.ipynb`](CQRF_QRR_HUST_v3_Seeds6-7.ipynb) | 6, 7 | `v3_67_HUST_CQRF_QRR_CBR_PAIRED_MANUSCRIPT6_v1.ipynb` |
| [`CQRF_QRR_HUST_v3_Seeds8-9_Corrected.ipynb`](CQRF_QRR_HUST_v3_Seeds8-9_Corrected.ipynb) | 8, 9 | `v3_C89_HUST_CQRF_QRR_CBR_PAIRED_MANUSCRIPT6_v1.ipynb` |

## Protocol observable from the archived code

- HUST source pipeline loads **77 candidate battery cells**, using **46 training, 15 validation, and 16 test cells** for each seeded split.
- Six input features: `voltage_mean`, `voltage_median`, `duration`, `abs_current_mean`, `Qt`, `voltage_slope`.
- Reservoir: **4 auxiliary qubits + 6 processor qubits**, fixed coupling strength **0.3**, paired CQRF+CBR and QRR+CBR evaluations. A separate No-Qt ablation is **not** run in these notebooks.
- Original research files require the author's HUST `.pkl` inputs and may reuse external `v2` feature caches, experiment manifests, stored metrics, and checkpoints. None of those inputs are included in this folder.

## Important numerical limitation

**These are experiment archives, not exact reproductions of the IEEE Access HUST table.** The article reports HUST MAPE **0.0221 for CQRF+CBR** and **0.0501 for QRR+CBR**. The archived `v3` results are not reconciled to those published ten-seed averages.

In particular, the 0–2 notebook explicitly skips seed 0 because it found earlier results, and other notebooks include similar output reuse. The archived output alone therefore cannot validate a complete 20-row (10 seeds × 2 models) evaluation or show that paper and archive have identical input datasets, split definitions, normalization and aggregation. Check the original external per-seed metrics and predictions before asserting exact reproduction.

The separate `v3_89_...` file **was intentionally excluded**: its saved output contained a copied seed 3 run, although the configured code was for seeds 8–9. This folder uses the corrected `v3_C89_...` archive instead.

## Release checks and remaining work

Notebook JSON and static Python syntax have been checked; no embedded credentials were detected in the copied notebook text. **No fresh model training or end-to-end execution has been performed**. Dataset input files, feature caches, and trained artifacts are not distributed. Before publishing any reproducibility claims, verify all 10 seed pairs, recompute MAPE from saved predictions, and establish which experimental version generated the published table.

See [repository reproducibility notes](../../docs/REPRODUCIBILITY.md) and [dataset information](../../docs/DATA.md).
