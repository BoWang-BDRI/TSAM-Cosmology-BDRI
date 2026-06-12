# Pipeline and Formal Obstruction Tests

## Status

**Validation status:** Diagnostic / candidate layer  
**Scope:** Catalog-level pipeline diagnostics and formal operator-space tests  
**Public claim level:** Not a final cosmological confirmation

This note records two distinct classes of tests:

1. **Catalog-level pipeline diagnostics**, including Jacobian jump checks on selected FITS science catalogs.
2. **Formal obstruction diagnostics**, including spectral, algebraic, measure-theoretic, Hilbert-span, and BRST-style tests.

The results are treated as diagnostic evidence, not as standalone proof of a new cosmological model.

---

## 1. Catalog-level Jacobian jump audit

### Run

```text
Python TSAM_Jacobian_Audit.py
```

### Input selection

The audit detected 70 FITS files and selected 7 science catalogs:

```text
ELG_LOPnotqso_N_clustering.dat.fits
ELG_LOPnotqso_NGC_clustering.dat.fits
ELG_LOPnotqso_SGC_clustering.dat.fits
QSO_N_clustering.dat.fits
QSO_NGC_clustering.dat.fits
QSO_S_clustering.dat.fits
QSO_SGC_clustering.dat.fits
```

### Main result

| Rank | Catalog | Metric | Significance |
|---:|---|---|---:|
| 1 | `ELG_LOPnotqso_NGC_clustering.dat.fits` | WEIGHT | **7.705504 sigma** |
| 2 | `ELG_LOPnotqso_N_clustering.dat.fits` | WEIGHT | 0.268390 sigma |
| 3 | `ELG_LOPnotqso_SGC_clustering.dat.fits` | WEIGHT | 0.113179 sigma |
| 4 | `QSO_NGC_clustering.dat.fits` | WEIGHT | 0.112514 sigma |
| 5 | `QSO_SGC_clustering.dat.fits` | WEIGHT | 0.077540 sigma |
| 6 | `QSO_N_clustering.dat.fits` | WEIGHT | 0.008152 sigma |
| 7 | `QSO_S_clustering.dat.fits` | WEIGHT | 0.001330 sigma |

### Interpretation boundary

The ELG NGC catalog shows a strong WEIGHT-channel Jacobian jump candidate. The QSO catalogs do not show comparable jump significance in this run.

This should be cited as:

```text
ELG_NGC_WEIGHT_JACOBIAN_JUMP_CANDIDATE
```

It should **not** be presented as direct proof of a cosmological axis, new force, or final TSAM confirmation.

---

## 2. TSAM v6.0 FITS scan and clean pipeline diagnostic

### Run

```text
Python TSAMceshi1.py
```

The initial v6.0 scan attempted to read a broad working directory and encountered many non-FITS files, including PNG, CSV, PY, TEX, JSON, PDF, ZIP, and directory entries.

Several valid FITS inputs were detected, including BAO and RANDOM-class files, but the scan exposed a key aggregation problem: matrices with incompatible shapes were grouped together.

Observed matrix shapes included:

```text
(16, 16), (15, 15), (14, 14), (13, 13), (12, 12), (11, 11), (44, 44)
```

### Failure mode

```text
ValueError: setting an array element with a sequence
```

### Clean-pipeline result

A later clean run completed the scan but produced an empty output table.

This is classified as:

```text
TSAM_v6_CLEAN_PIPELINE_EMPTY_OUTPUT
```

### Engineering repair requirements

```text
- Add FITS-only file filtering.
- Skip directories and non-FITS artifacts.
- Group matrices by compatible shape before aggregation.
- Separate science catalogs, random catalogs, images, and external reports.
- Treat empty clean reports as pipeline diagnostics, not null-confirmed science results.
```

---

## 3. Formal obstruction diagnostics

These tests are formal/operator-space diagnostics. They should be treated as mathematical or toy-model evidence layers unless paired with independent observational validation.

### v25: Spectral obstruction

| Quantity | Value |
|---|---:|
| L2 spectral residual norm | `1.449437e-15` |
| Max gradient residual | `2.020953e-16` |
| Spectral tail energy | `9.772266e-01` |

Classification:

```text
SPECTRAL_OBSTRUCTION_DIAGNOSTIC
```

Interpretation: the main signal is not the small L2 residual but the high spectral-tail energy, suggesting a high-mode representation obstruction under the tested basis.

### v27: Operator algebra non-closure

| Quantity | Value |
|---|---:|
| Commutator norm | `3.338073e+02` |
| Projected GR component | `8.438124e-17` |
| Residual algebra norm | `3.338073e+02` |

Classification:

```text
OPERATOR_ALGEBRA_NON_CLOSURE_DIAGNOSTIC
```

### v30: Measure-theoretic non-closure

| Quantity | Value |
|---|---:|
| L2(mu) residual norm | `5.330710e-01` |

Classification:

```text
MEASURE_THEORETIC_NON_CLOSURE_DIAGNOSTIC
```

### v31: Measure-equivalence warning

| Quantity | Value |
|---|---:|
| L2 residual under GR measure | `4.770042e-01` |
| L2 residual under TSAM measure | `4.947763e-01` |
| Radon-Nikodym deviation | `1.645345e-01` |

Classification:

```text
MEASURE_EQUIVALENCE_WARNING
```

Interpretation: this is a downgrade signal. Under this construction, the deformation may be absorbable into an effective GR measure.

### v32: Dynamical measure generation

| Quantity | Value |
|---|---:|
| Dynamical measure residual | `1.318214e-01` |

Classification:

```text
DYNAMICAL_MEASURE_FLOW_DIAGNOSTIC
```

### v33: Path-integral measure deformation

| Quantity | Value |
|---|---:|
| Partition function deformation | `2.396205e-02` |

Classification:

```text
PATH_INTEGRAL_MEASURE_INEQUIVALENCE_CANDIDATE
```

### v34: Hilbert-space span obstruction

The first run exposed a Python/NumPy compatibility issue:

```text
AttributeError: module 'numpy' has no attribute 'trapz'
```

Repair:

```text
Replace np.trapz with np.trapezoid.
```

Post-repair output:

| Quantity | Value |
|---|---:|
| L2 residual TSAM -> GR span | `7.384528e-02` |
| GR self-projection error | `4.605154e-16` |

Classification:

```text
HILBERT_SPAN_OBSTRUCTION_DIAGNOSTIC
```

### v35: Unified Hilbert / BRST diagnostic

| Quantity | Value |
|---|---:|
| L2 residual TSAM -> GR span | `1.256981e+00` |
| GR self-projection error | `5.958082e-15` |
| BRST obstruction norm | `2.136518e-02` |

Classification:

```text
HILBERT_AND_BRST_NONTRIVIALITY_DIAGNOSTIC
```

### v36: BRST cohomology diagnostic

| Quantity | Value |
|---|---:|
| Nilpotency error `||Q^2||` | `0.000000e+00` |
| Commutator norm `[Q,D]` | `6.003842e+01` |

Classification:

```text
BRST_NON_TRIVIAL_CLASS_DIAGNOSTIC
```

Interpretation: under the tested formal construction, the deformation is treated as Q-closed but not Q-exact. This remains a formal diagnostic result, not a direct observational claim.

---

## 4. MPC / small-body raw-angle downgrade

The command-line MPC raw angular audit produced an isotropy-consistent result in one test stage:

| Quantity | Value |
|---|---:|
| Valid numeric rows | `1958` |
| Rayleigh R | `0.03489920590288544` |
| Mean direction | `40.460128673 deg` |
| Permutation p-value | `0.9224` |

Classification:

```text
MPC_RAW_ANGLE_TEST_ISOTROPIC
```

This result is **not** a positive anisotropy detection.

The later small-body supplement should remain the controlling public statement for that layer: family-limited, bias-aware, and fast-pass only.

---

## 5. Public conclusion

This test batch supports the following limited claims:

```text
1. One strong ELG NGC WEIGHT-channel Jacobian jump candidate was found.
2. Several formal/operator-space diagnostics indicate non-closure or non-triviality under tested constructions.
3. The v6.0 clean FITS pipeline and the MPC raw-angle test are non-confirmatory diagnostic results.
4. Several engineering repairs are required before the pipeline can be treated as a stable validation framework.
```

It does not support the following claims:

```text
- Final TSAM confirmation.
- Direct proof of a cosmological axis.
- Direct proof of a new force law.
- Direct proof that raw MPC angular data is anisotropic.
- Direct proof that formal BRST/Hilbert diagnostics map onto observed cosmology without further validation.
```

---

## Recommended next actions

```text
- Re-run Jacobian jump audit with explicit catalog version metadata.
- Add FITS-only scanner safeguards.
- Re-run v6 clean pipeline after matrix-shape grouping.
- Package formal obstruction tests as reproducible notebooks or scripts.
- Separate observational validation pages from formal diagnostic pages.
```
