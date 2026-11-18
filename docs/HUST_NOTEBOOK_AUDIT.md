# HUST manuscript-to-notebook reconciliation — 2026-11-18

Status: **Unresolved**. This is an audit of archived code and saved metrics, not a newly executed test.

| Source | HUST features | CQRF+CBR mean MAPE | QRR+CBR mean MAPE | Coverage |
|---|---|---:|---:|---|
| [IEEE Access Table 5](https://doi.org/10.1109/ACCESS.2026.3727788) | 6 electrical features | 0.0221 | 0.0501 | 10 seeds, 0–9 |
| Older archived HUST CQRF and QRR sources | Older CQRF code uses **7 features** | ~0.0221 | ~0.0501 | Logs for seeds 0–9 |
| Six-feature `v3` selected saved metrics | 6 manuscript-style features | 0.019943 | 0.022131 | 8 CQRF seeds 2–9, 8 QRR seeds 1–8 |

The older archived notebooks reproduce the rounded numbers but not the published **six-feature** method. The six-feature code is closer to the published method, but saved results are incomplete and do not reproduce the published means.

The `v3` notebooks were archived unchanged and are placed in `notebooks/hust/experimental/` **only for review**; they are not a validated research reproduction. In particular, `v3_89` contains a saved seed-3 log despite being configured for seeds 8 and 9, and other notebooks merge prior-run metrics.

Next: identify exact underlying split manifests and independent prediction files, reconstruct a complete matched ten-seed table, and check methodological equivalence before requesting merge into `main`. Do not delete failed runs or select seeds merely to force a match.
