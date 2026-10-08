# Coupled Quantum Reservoir Features (CQRF) for Battery State-of-Health Estimation

Research notebooks accompanying:

> S. P. Gunasekar and P. K. Rangarajan, **“Coupled Quantum Reservoir Features for Multi-Chemistry Battery State-of-Health Estimation,”** *IEEE Access*, vol. 14, pp. 132697–132718, 2026. DOI: [10.1109/ACCESS.2026.3727788](https://doi.org/10.1109/ACCESS.2026.3727788).

## Scope

This is a **selected notebook release**, not a complete reproduction package for all four datasets in the article. It focuses on XJTU and MIT for simulated CQRF/QRR comparisons and includes a separate extended IBM Quantum hardware feasibility notebook. The original paper also evaluates HUST and TJU; those main experiments are **not** included in this release.

CQRF uses a fixed 10-qubit quantum reservoir (4 auxiliary + 6 processor qubits) to produce 57 measured features. Only the classical compact bottleneck readout (57 → 2 → 2 → 1; 125 trainable parameters) is trained. QRR is the recurrent baseline.

## Notebooks

| Notebook | Contents | Scope |
|---|---|---|
| `CQRF_XJTU_10Seeds.ipynb` | CQRF + CBR, XJTU | 10 readout seeds; batch-wise leave-one-cell-out evaluation |
| `QRR_XJTU_10Seeds.ipynb` | QRR + CBR, XJTU | 10 readout seeds; matched batch-wise evaluation |
| `CQRF_QRR_MIT_3Seeds.ipynb` | Paired CQRF + CBR and QRR + CBR, MIT | Seeds 7, 8, and 9; a subset of the paper's 10-seed evaluation |
| `CQRF_MIT_IBM_QPU_150Samples.ipynb` | Real IBM hardware CQRF feature inference | Original notebook covers **MIT, HUST, and TJU**, 150 samples **per dataset**; this repository highlights the MIT portion. QRR was **not** run on QPU. |

## Comparison with the published paper

MAPE is reported on the original fractional scale (lower is better). The notebook figures reflect saved outputs, not fresh executions.

| Dataset | Model | Published paper (10 seeds) | Notebook release | Note |
|---|---|---:|---:|---|
| XJTU | CQRF + CBR | 0.0188 | 0.018741 | Small discrepancy; **not** identical at four-decimal rounding precision |
| XJTU | QRR + CBR | 0.0203 | 0.020225 | Small discrepancy; not identical at four-decimal rounding precision |
| MIT | CQRF + CBR | 0.0131 | 0.013200 | 3-seed subset (7–9), not published 10-seed mean |
| MIT | QRR + CBR | 0.0157 | 0.015203 | 3-seed subset (7–9), not published 10-seed mean |

The two XJTU figures are close to the paper but should not be described as exact rounded matches; differences may reflect experiment/aggregation details that this release does not resolve.

### Real IBM Quantum audit: distinguish paper from extension

The **published** unmitigated QPU audit used **150 total samples**: 50 MIT + 50 HUST + 50 TJU on `ibm_marrakesh`. Its MIT QPU MAPE-derived score was **92.60%**.

The **extended notebook** is configured for **150 samples per dataset** (450 total across MIT/HUST/TJU). Saved MIT results report **150 MIT samples, 450 measurement circuits at 512 shots, QPU CBR MAPE = 0.092272, MAPE-derived score = 90.77%**. This extension is **not** the published 50-sample MIT evaluation; those scores must not be conflated. The notebook still contains HUST and TJU code/results even though its release filename emphasizes MIT.

## Obtain the datasets

The public source datasets and their provenance are documented in [`DATA.md`](DATA.md). In particular:

- **XJTU:** [official Zenodo archive](https://doi.org/10.5281/zenodo.10963339) and [upstream preprocessing repository](https://github.com/wang-fujin/Battery-dataset-preprocessing-code-library).
- **MIT:** [MATR battery data project](https://data.matr.io/1/projects/5c48dd2bc625d700019f3204) and [dataset article](https://doi.org/10.1038/s41560-019-0356-8).

**Important:** The public raw archives alone do not satisfy every notebook path: some experiments consume project-specific `.npz` caches and readout checkpoints, which are not distributed here. The notebooks preserve recorded results but are not advertised as self-contained run-from-scratch reproductions.

## Usage and dependencies

These are preserved experiment notebooks, **not** turnkey rerunnable scripts. They reference the original authors' Google Drive directory layout, `.npz` feature caches, processed battery data, and (for the QPU notebook) trained checkpoint files. Those input artifacts are not included here. See [`DATA.md`](DATA.md).

1. Open the desired notebook in Jupyter/Google Colab and read its setup cells.
2. Install the dependencies in [`requirements.txt`](requirements.txt), using compatible versions for your environment. Exact original package versions were not recovered and this list is **not** a verified lockfile.
3. Supply the required dataset files, precomputed feature bundles, and any checkpoints; update paths **only if you intend to execute it**.
4. For hardware: the release notebook has `RUN_QPU = False` by default. Never place an IBM API token directly into a notebook. Running paid IBM hardware jobs requires explicit opt-in and available service access.

**Do not use Run All on the QPU notebook expecting it to reproduce saved hardware results without input files.** The saved results are preserved as an audit record; rerunning requires the missing inputs and may use additional paid quantum resources if explicitly enabled.

## Citation

Please cite the published article when using this repository. Machine-readable citation metadata is in [`CITATION.cff`](CITATION.cff).

## License

See [`LICENSE`](LICENSE) for the proposed permissive code license. Confirm that both code contributors/rightsholders approve this license before publishing. Battery datasets and IBM hardware services retain their own terms.

## Reproducibility limitations

- Selected experiments only; not an exhaustive release for every table in the article.
- Preprocessed data, quantum feature caches, and model weights may be required but are not included.
- Results are from saved notebook outputs and have not been freshly rerun as part of this release.
- Published 50-sample hardware audit and extended 150-MIT-sample hardware run are separate protocols.
- This release does not claim quantum computational advantage or real-hardware superiority over classical models.
