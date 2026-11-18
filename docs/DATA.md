# Data and external artifacts

The public notebook release **does not redistribute datasets, precomputed quantum features, trained readouts or IBM job artifacts**.

## XJTU

Both XJTU notebooks were written for Google Colab and reference the original project tree under `/content/drive/MyDrive/HB/QRC_Battery_SOH`. They expect XJTU cell data and/or cached `.npz` fold-feature files with experiment-specific names. The paths are environment-specific; the notebooks are preserved as research records.

## MIT simulated comparison

The paired MIT notebook uses seeds 7–9 and expects processed MIT cell data and locally saved experiment artifacts. It is **not** a complete standalone ten-seed reproduction of the published MIT mean.

## MIT IBM hardware

The extended QPU notebook needs precomputed simulator CQRF feature bundles, model checkpoints and the original project paths. It contains MIT, HUST, and TJU execution branches (150 samples each), despite its release filename focusing on MIT. The saved MIT result is an extended hardware audit and must be distinguished from the paper's 50-MIT-sample result.

**No IBM credentials are shipped in the release support package.** The hardware notebook obtains a token from `IBM_API_TOKEN` / secure prompt, and has `RUN_QPU = False` by default.

## Reproducibility status

Notebook outputs allow inspection of recorded experiments, but external data/checkpoints are needed to rerun them. Cite and follow dataset providers' licensing and access conditions. Do not commit private dataset bundles, IBM tokens or other local authentication files.

## Official dataset sources (for this selected release)

| Dataset | Original source | Download | Notes |
|---|---|---|---|
| XJTU | Xi'an Jiaotong University battery aging dataset, Wang et al. | https://doi.org/10.5281/zenodo.10963339 | Original archive covers six batches; follow the original record for license, cell inventory and files. |
| MIT / MATR | Severson et al., *Data-driven prediction of battery cycle life before capacity degradation* | https://data.matr.io/1/projects/5c48dd2bc625d700019f3204 | LFP cycle data. See https://doi.org/10.1038/s41560-019-0356-8 for provenance. |

XJTU's dataset creators also publish preprocessing reference code at https://github.com/wang-fujin/Battery-dataset-preprocessing-code-library . These are third-party resources; the repository does not mirror them or assert that the downloaded archives alone reproduce the notebook-specific processed arrays.

### Required inputs versus available downloads

The source datasets above are **raw upstream data**, not necessarily the already-processed `.npz` feature caches, normalized folds, and model checkpoints referenced by the experimental notebooks. At present this selected release does not include a verified raw-to-cache conversion recipe, exact processed-file checksums, or all trained checkpoint files. Therefore use saved outputs for auditing results; do not describe the notebooks as independently end-to-end rerunnable from a fresh dataset download.

### Published evaluation protocol to cite

- XJTU: six batches, leave-one-cell-out evaluation within each batch, first five cycles excluded for matched CQRF/QRR comparison; ten readout seeds.
- MIT: cell-disjoint 60/20/20 train/validation/test split; published mean over ten seeds. Released paired notebook covers only seeds 7, 8 and 9.
- MIT QPU notebook: an **extended** 150-MIT-sample run distinct from the published hardware audit (50 samples each for MIT, HUST and TJU).

For a fully runnable future release, provide an explicit input manifest giving the original filename, relative path, generation/preprocessing instructions, array shapes, hash and license for each required artifact. Do not include proprietary or credential-bearing IBM account state.
