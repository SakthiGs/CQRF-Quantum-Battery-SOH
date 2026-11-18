# HUST six-feature paired notebooks — review candidates

**Status: experimental / not a validated reproduction of the IEEE Access HUST results.** These notebooks are staged in a draft pull request for numerical and protocol audit.

The [IEEE Access manuscript](https://doi.org/10.1109/ACCESS.2026.3727788) reports HUST CQRF+CBR **MAPE 0.0221** and QRR+CBR **MAPE 0.0501** (seeds 0–9), with the six input features `[voltage_mean, voltage_median, duration, abs_current_mean, Qt, voltage_slope]`.

## Archived notebooks

| Notebook | Configured seeds | Audit limitation |
|---|---|---|
| [0–2](experimental/v3_012_HUST_CQRF_QRR_CBR_PAIRED_MANUSCRIPT6_v1.ipynb) | 0,1,2 | Merges prior-run outputs; not full ten-seed evidence |
| [3–5](experimental/v3_345_HUST_CQRF_QRR_CBR_PAIRED_MANUSCRIPT6_v1.ipynb) | 3,4,5 | Merges prior-run outputs; not full ten-seed evidence |
| [6–7](experimental/v3_67_HUST_CQRF_QRR_CBR_PAIRED_MANUSCRIPT6_v1.ipynb) | 6,7 | Partial saved results |
| [8–9](experimental/v3_89_HUST_CQRF_QRR_CBR_PAIRED_MANUSCRIPT6_v1.ipynb) | 8,9 | Saved output includes a seed-3 start message; not proof of successful 8–9 runs |

All source notebook bytes and saved outputs are preserved as archived, not cleaned or altered.

## Numerical and methodology discrepancy

**Matching paper scores alone is not enough:** the *older* archived HUST CQRF+CBR notebook series rounds to the manuscript MAPE of 0.0221 and older QRR+CBR series to 0.0501, but the older CQRF implementation uses **seven input features**, including cycle and voltage statistics. This does **not** match the six-feature HUST protocol stated in the paper. Those older source notebooks are **not** included in this draft.

These `v3` notebooks use the six named manuscript features, but the available per-seed metrics in the selected experiment folders contain only **eight CQRF seeds (2–9) and eight QRR seeds (1–8)**. Their corresponding sample means were **0.019943** and **0.022131**. These differ materially from the ten-seed manuscript means; do **not** label this folder as paper reproduction.

## Gates before merging

1. Establish the exact six-feature HUST preprocessing and source-run lineage corresponding to the manuscript.
2. Recover complete seeds 0–9 for **both** models and verify original prediction files and split manifests, not just summary CSVs.
3. Resolve copied/overwritten metric paths, merged-run provenance, and stale 8–9 notebook output.
4. Verify MAPE/RMSE computations and training-only normalization, fixed circuit seed and 125-parameter CBR.
5. Scan scripts and artifacts for credentials and restricted dataset contents; pin working dependencies.
6. Record any unresolved protocol discrepancies transparently. Never edit metrics to force agreement.

The original input archives, processed feature caches, and checkpoints are **not** part of this draft. These notebooks were not rerun in a clean environment as part of the audit.

See the [full audit note](../../docs/HUST_NOTEBOOK_AUDIT.md) and [repository reproducibility notes](../../docs/REPRODUCIBILITY.md).
