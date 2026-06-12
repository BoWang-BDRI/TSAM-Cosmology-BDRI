# TSAM Research Log

This file records public repository updates and research-index changes.

## 2026-06-12

### Midfield cosmology and RTN near-field validation layers added

Added two additional validation-layer pages under `validation/`:

- `validation/midfield-cosmology-layer.md`
- `validation/rtn-nearfield-layer.md`

The midfield page summarizes the uploaded redshift/angular-density diagnostic material, including corrected 0.4-0.7 density matrices, 0.7-1.0 density matrices, stage-2 audit partitions, and reconstruction-accounting metadata.

The RTN page summarizes the uploaded near-field dynamical-response visual diagnostics, including v11 RTN residual decomposition, v15 object-dependent acceleration response spectrum, and v16 normal-axis epsilon audit.

Public claim level:

- In audit / diagnostic candidate.
- Useful for repository organization and external review.
- Not a final TSAM confirmation claim.
- Not a final cosmological-parameter solution.
- Not a completed N-body residual proof.

The README and data-validation index were updated to link both pages.

### Solar-system small-body validation layer added

Added the first validation-layer page under `validation/`:

- `validation/solar-system-layer.md`

The page summarizes the uploaded small-body discovery-bias and window-stability supplement as a restrained validation record.

Public claim level:

- In audit / fast-pass triage.
- Family-limited near-field orbital-direction anisotropy candidate.
- Not a TSAM confirmation claim.
- Not a fixed-axis, external-forcing, or solar-system-alignment proof.

Supporting audit components summarized in the page:

- Window C 330-30 focus audit.
- Window A 240-285 focus audit.
- Coordinate-artifact rotation check.
- Family-size matched null audit.
- Multiple-testing / Benjamini-Hochberg FDR audit.
- MPCORB and CometEls parser crossmatch limitation notes.

The README and data-validation index were updated to link this validation page.

### Community-readiness documentation update

Added a public-facing documentation layer to support controlled external review before broader community expansion.

Changes:

- Added `docs/faq.md` for external-reader questions.
- Added `docs/glossary.md` for working TSAM terminology.
- Added `docs/how-to-cite.md` for repository and Zenodo citation guidance.
- Added `docs/data-validation-index.md` for dataset-layer validation status tracking.
- Added `docs/public-claims-boundary.md` to separate archive records, hypotheses, audit directions, and reproducible claims.
- Updated `README.md` with a public repository guide and community observation track.

Purpose:

- Improve repository readability before entering external communities.
- Reduce misunderstanding around unverified assumptions and provisional claims.
- Prepare a clean structure for small-community observation, terminology testing, and reproducibility feedback.

### DOI archive update

Updated the public TSAM archive reference in `README.md` and later restored the complete Zenodo archive table.

Current Zenodo DOI archive chain:

- `10.5281/zenodo.19456031` — TSAM Primary Archive
- `10.5281/zenodo.19951835` — TSAM Deep Correction
- `10.5281/zenodo.20249937` — TSAM Updated Archive
- `10.5281/zenodo.20267618` — CRIF Paper

### Public repository structure update

Updated the repository from a short archive pointer into a fuller public research index.

Changes:

- Expanded `README.md` with a clearer TSAM research-position summary.
- Added `docs/theory-overview.md` for the main theoretical introduction.
- Added `docs/validation-principles.md` to document the observational validation boundary.
- Added `docs/research-roadmap.md` to organize the next research phases.
- Added this research log to track future public updates.

### Methodological note

The repository now emphasizes the following public-facing standard:

- Observational constraints first.
- Provisional labeling of unverified assumptions.
- Freeze-review cycles for theory growth.
- Cross-dataset validation over single-dataset pattern fitting.
- Clear separation between archived papers, active hypotheses, and validation methods.

## Planned next updates

Potential future updates:

- Add a CRIF methodology page.
- Add a SPARC residual-audit index.
- Add a QSO / LRG cross-epoch audit index.
- Add a CMB validation note.
- Add validation-layer templates under `validation/`.
- Add external-community observation notes after initial review testing.
