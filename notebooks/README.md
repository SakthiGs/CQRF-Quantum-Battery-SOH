# Experiment notebook index

These are **archived research notebooks**, not a fully turnkey reproduction package. They retain their original code and saved outputs, including absolute Google Drive paths that need external input artifacts.

| Location | What it contains | Published-paper relationship |
|---|---|---|
| [`xjtu/CQRF_XJTU_10Seeds.ipynb`](xjtu/CQRF_XJTU_10Seeds.ipynb) | XJTU CQRF+CBR, batches 1–6 | Ten readout seeds, within-batch leave-one-cell-out |
| [`xjtu/QRR_XJTU_10Seeds.ipynb`](xjtu/QRR_XJTU_10Seeds.ipynb) | Matched recurrent QRR+CBR | Ten readout seeds, within-batch leave-one-cell-out |
| [`mit/CQRF_QRR_MIT_Seeds7-9.ipynb`](mit/CQRF_QRR_MIT_Seeds7-9.ipynb) | Paired MIT CQRF/QRR | **Only seeds 7, 8 and 9** of published ten-seed simulation |
| [`hust/`](hust/) | Four archived HUST paired CQRF/QRR notebooks | Configured seed ranges 0–2, 3–5, 6–7, 8–9; **incomplete/reused saved run outputs and unverified published-paper agreement** |
| [`hardware/CQRF_IBM_QPU_Extended_150PerDataset.ipynb`](hardware/CQRF_IBM_QPU_Extended_150PerDataset.ipynb) | IBM QPU extension with MIT/HUST/TJU code | **150 samples per dataset**, not published 50 per dataset; hardware calls opt-in |

See [dataset sources and dependencies](../docs/DATA.md), [reproducibility notes](../docs/REPRODUCIBILITY.md) and the [published paper](https://doi.org/10.1109/ACCESS.2026.3727788).

**Scope of release:** Four HUST v3 paired notebooks have been added **as exploratory archives, not as verified HUST publication reproductions**. TJU main simulation notebooks and the remaining seven MIT seeds have not been moved into this public repository. Archived outputs are not evidence that experiments can be rerun end-to-end. Raw datasets, processed caches and trained checkpoints are not redistributed.

**Safety:** In the QPU notebook, `RUN_QPU = False` by default. IBM credentials are not part of this release.
