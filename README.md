# MUMMI merger classifications

MUMMI (MUlti-Model Merger Identifier) classifies galaxies in three stages: merger identification (SG1), merger stage (SG2), and time since coalescence for post-mergers (SG3). These catalogues use low-surface-brightness (LSB) reductions and cutouts with a 12 R_P field of view.

| Catalogue | Sample | Rows |
| --- | --- | ---: |
| [`mummi_cfis_dr5_v2.csv`](mummi_cfis_dr5_v2.csv) | CFIS-SDSS DR5 overlap | 235,354 |
| [`mummi_decals_sdss.csv`](mummi_decals_sdss.csv) | Analogous DECaLS-SDSS galaxy sample | 423,725 |

Each row is one galaxy. `objID` is its SDSS object identifier and can be used to join these classifications to other SDSS data. The remaining columns are:

| Column | Meaning |
| --- | --- |
| `SG1_votes` | Number of the 20 ensemble models voting **merger** (0–20). `20` is unanimous merger identification; `>10` is a simple majority. Low values select cleaner non-merger samples; `0` means no model voted merger. |
| `SG2_prob` | Mean probability from two models that the merger is **post-coalescence**. Values `>0.5` indicate post-mergers; values `<0.5` indicate pre-merger pairs. More extreme values can give purer samples. Interpret SG2 only for galaxies selected as mergers by SG1. |
| `SG3_timescale_class` | Four-bin prediction for time since coalescence: `1` immediate (<0.16 Gyr), `2` short (0.16–0.48 Gyr), `3` intermediate (0.48–0.96 Gyr), `4` long (>0.96 Gyr). Use for post-mergers selected with SG1 and SG2. |
| `SG3_timescale_peak` | Snapshot index (0–10) with the highest probability among 11 post-merger snapshots. `0` corresponds to approximately 0 Gyr; `10` to more than 1.7 Gyr. The average interval is approximately 0.16 Gyr. This permits alternative time binning. |
| `PROBABILITY_FLAG` | `1` marks predictions satisfying the probability criteria used for high-performance time-scale samples in the TNG simulations; `0` does not. The flagged sample is recommended when using all four SG3 classes. |

The CFIS catalogue also contains:

| Column | Meaning |
| --- | --- |
| `SG3_prob_1`–`SG3_prob_4` | Predicted probabilities for the four bins of `SG3_timescale_class`, in class order. |
| `SG3_lower_bound`, `SG3_upper_bound` | Lower and upper bounds of the 16th–84th percentile interval around the SG3 time distribution, on the snapshot-index scale. |

The DECaLS catalogue instead contains `SG3_timescale_peak_prob`, the probability at `SG3_timescale_peak`. It does not include the four rebinned probabilities or the confidence bounds.

## Citation

If you use the **CFIS** catalogue, cite both [*Galaxy mergers in UNIONS – I: A simulation-driven hybrid deep learning ensemble for pure galaxy merger classification*](https://doi.org/10.1093/mnras/stae1885) and [*Galaxy mergers in UNIONS – II: Predicting time-scales in the post-merger regime*](https://doi.org/10.1093/mnras/stag178).

If you use the **DECaLS** catalogue, cite [*Galaxy evolution in the post-merger regime. V – Atomic gas evolution traced by ALFALFA stacks*](https://arxiv.org/abs/2609.24925).
