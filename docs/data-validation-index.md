# TSAM Data Validation Index

This index organizes TSAM-related observational work by validation layer. It is designed to separate data-audit direction from theoretical interpretation.

## Purpose

The goal of this index is to make each research direction easier to review, reproduce, challenge, or downgrade.

Each validation track should eventually specify dataset source, preprocessing assumptions, coordinate system, fixed analysis rules, expected null behavior, residual or anomaly metric, failure conditions, and reproducibility status.

## Validation status labels

| Label | Meaning |
|---|---|
| Proposed | Conceptual direction identified, no stable validation protocol yet |
| In audit | Data workflow or metric under active development |
| Fast-pass triage | Initial audit result exists, but final bias-cleared interpretation is not allowed |
| Diagnostic candidate | Figure/table-supported signal candidate; not yet promoted to physical interpretation |
| Archived | Public DOI or repository record exists |
| Reproducible | Independent or internally repeatable workflow exists |
| Under review | Result frozen for review against external constraints |
| Downgraded | Claim weakened after stronger review evidence |

## Current validation layers

| Layer | Current role | Status |
|---|---|---|
| CMB directional features | Large-scale anisotropy and boundary audit | Proposed / In audit |
| QSO redshift-space structure | Cross-epoch continuity and phase-consistency tests | Proposed / In audit |
| LRG / galaxy-density fields | Matter-distribution and large-scale wall detection | Proposed / In audit |
| [Midfield cosmology diagnostics](../validation/midfield-cosmology-layer.md) | Redshift/angular-density scan and post-deconvolution systematics audit | In audit / Diagnostic candidate |
| SPARC rotation residuals | Local dynamical-prior stress test using galaxy rotation data | In audit |
| [RTN near-field diagnostics](../validation/rtn-nearfield-layer.md) | RTN non-conservative acceleration and epsilon-audit candidate layer | In audit / Diagnostic candidate |
| [Solar-system boundary tests](../validation/solar-system-layer.md) | Low-redshift termination and local-frame consistency checks; currently small-body angular-distribution triage | In audit / Fast-pass triage |
| JWST high-redshift anomalies | Early-universe stress test for expansion and formation assumptions | Proposed |
| CRIF residual inference | Reference-frame robustness and coordinate-free residual checks | Archived |

## Active validation pages

| Page | Status | Notes |
|---|---|---|
| [`validation/midfield-cosmology-layer.md`](../validation/midfield-cosmology-layer.md) | In audit / Diagnostic candidate | Corrected 0.4-0.7 angular-density matrix, 0.7-1.0 matrix, stage-2 audit, and reconstruction accounting |
| [`validation/rtn-nearfield-layer.md`](../validation/rtn-nearfield-layer.md) | In audit / Diagnostic candidate | RTN model-response and epsilon-audit visualization layer; requires raw ephemeris reproducibility package |
| [`validation/solar-system-layer.md`](../validation/solar-system-layer.md) | In audit / Fast-pass triage | Family-limited small-body orbital-direction anisotropy candidate; not a TSAM confirmation claim |

## Minimum validation record

A mature validation entry should include:

- Track name
- Dataset
- Data source
- Coordinate system
- Preprocessing
- Frozen parameters
- Metric
- Null comparison
- Result summary
- Failure condition
- Reproducibility status
- Archive / commit reference

## Review rule

No validation layer should be promoted from a working hypothesis to a strong claim until the rule set is fixed before interpretation and the result remains stable under review.

## Near-term repository work

The next documentation stage should add or mature one page per validation layer:

- `validation/cmb-layer.md`
- `validation/qso-layer.md`
- `validation/lrg-layer.md`
- `validation/midfield-cosmology-layer.md` — active diagnostic-candidate page added
- `validation/sparc-layer.md`
- `validation/rtn-nearfield-layer.md` — active diagnostic-candidate page added
- `validation/solar-system-layer.md` — active fast-pass triage page added
- `validation/jwst-layer.md`

Each page should use the same validation template so that external reviewers can compare the layers without relying on narrative interpretation.
