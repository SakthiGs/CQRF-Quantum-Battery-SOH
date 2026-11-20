# Reproducibility and release status

This repository accompanies S. P. Gunasekar and P. K. Rangarajan, *Coupled Quantum Reservoir Features for Multi-Chemistry Battery State-of-Health Estimation*, IEEE Access 14 (2026), 132697–132718, [DOI:10.1109/ACCESS.2026.3727788](https://doi.org/10.1109/ACCESS.2026.3727788).

## What this release does and does not establish

- **XJTU**: archived paired CQRF/QRR 10-seed notebooks are included. The stored reported values in this release (CQRF MAPE 0.018741, QRR MAPE 0.020225) are near, but **not identical at four-decimal rounding precision** to the published 0.0188 and 0.0203. Do not label them exact numerical reproductions.
- **MIT simulation**: the included notebook covers **seeds 7–9 only** (CQRF 0.013200, QRR 0.015203). The paper uses seeds 0–9 (CQRF 0.0131, QRR 0.0157). A separate Drive audit found complete archived ten-seed means of approximately 0.013086 and 0.015682, respectively, which round to the paper's reported precision. Those additional source notebooks, caches, and per-seed artifacts are **not distributed here**; this is a documented aggregation check, not an independently rerun reproduction.
- **HUST simulation**: four archived `v3` paired CQRF/QRR notebooks are now in [`notebooks/hust/`](../notebooks/hust/). Their configured seed ranges span 0–9, but some saved outputs explicitly **skip previously computed experiments** and depend on external Drive metrics. They do **not** establish complete 10-seed reproduction. In particular, the paper's HUST MAPE values are CQRF+CBR **0.0221** and QRR+CBR **0.0501**, whereas archived `v3` observations disagree materially with the published QRR average. The notebook archives are supplied for transparency and further audit, **not** as exact published-result replications.
- **TJU simulation**: not released here. Experimental versions differ and need protocol and numerical reconciliation.
- **IBM QPU**: the included extended notebook covers **150 samples per dataset**, whereas the paper used **50 samples per dataset, 150 total**. Treat these as separate experiments.
- The code has not been freshly run or tested in a clean environment as part of this restructuring. Internal paths, unpinned dependencies, unavailable processed inputs and checkpoints may prevent direct execution.

## Public-release gates for future additions

1. Identify the exact manuscript table row, dataset subset, evaluation protocol, split and random seeds.
2. Recalculate MAPE, RMSE and any derived scores from per-prediction artifacts, checking denominators and target plausibility.
3. Check all expected seed/model/subset combinations; identify incomplete runs, duplicate output paths and overwritten files.
4. Compare aggregated values with the manuscript at its published precision; preserve any mismatch transparently.
5. Confirm no credentials, private materials, copyrighted third-party dataset blobs or large unwanted checkpoints are committed.
6. Test imports and at least one end-to-end run before claiming turnkey reproducibility.

## Planned, not yet released

After verification, reusable 10-qubit implementations may live in `src/cqrf/`, tests in `tests/`, and runnable scripts/configuration in `scripts/` and `configs/`. These directories are intentionally not created as empty placeholders. Do **not** substitute the archived 8-qubit `models/quantum_reservoir.py` from Drive for the published ten-qubit CQRF implementation.

See [notebook index](../notebooks/README.md) and [dataset documentation](DATA.md).
