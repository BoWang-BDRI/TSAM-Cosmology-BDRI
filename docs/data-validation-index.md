# TSAM Data Validation Index

This index organizes TSAM-related observational work by validation layer. It is designed to separate data-audit direction from theoretical interpretation.

## Purpose

The goal of this index is to make each research direction easier to review, reproduce, challenge, or downgrade.

Each validation track should eventually specify:

- dataset source,
- preprocessing assumptions,
- coordinate system,
- fixed analysis rules,
- expected null behavior,
- residual or anomaly metric,
- failure conditions,
- and reproducibility status.

## Validation status labels

| Label | Meaning |
|---|---|
| Proposed | Conceptual direction identified, no stable validation protocol yet |
| In audit | Data workflow or metric under active development |
| Archived | Public DOI or repository record exists |
| Reproducible | Independent or internally repeatable workflow exists |
| Under review | Result frozen for review against external constraints |
| Downgraded | Claim weakened or rejected due to stronger evidence |

## Current validation layers

| Layer | Current role | Status |
|---|---|---|
| CMB directional features | Large-scale anisotropy and boundary audit | Proposed / In audit |
| QSO redshift-space structure | Cross-epoch continuity and phase-consistency tests | Proposed / In audit |
| LRG / galaxy-density fields | Matter-distribution and large-scale wall detection | Proposed / In audit |
| SPARC rotation residuals | Local dynamical-prior stress test using galaxy rotation data | In audit |
| Solar-system boundary tests | Low-redshift termination and local-frame consistency checks | Proposed |
| JWST high-redshift anomalies | Early-universe stress test for expansion and formation assumptions | Proposed |
| CRIF residual inference | Reference-frame robustness and coordinate-free residual checks | Archived |

## Minimum validation record

A mature validation entry should include:

```text
Track name:
Dataset:
Data source:
Coordinate system:
Preprocessing:
Frozen parameters:
Metric:
Null comparison:
Result summary:
Failure condition:
Reproducibility status:
Archive / commit reference:
```

## Review rule

No validation layer should be promoted from a working hypothesis to a strong claim until the rule set is fixed before interpretation and the result remains stable under review.

## Near-term repository work

The next documentation stage should add one page per validation layer:

- `validation/cmb-layer.md`
- `validation/qso-layer.md`
- `validation/lrg-layer.md`
- `validation/sparc-layer.md`
- `validation/solar-system-layer.md`
- `validation/jwst-layer.md`

Each page should use the same validation template so that external reviewers can compare the layers without relying on narrative interpretation.
