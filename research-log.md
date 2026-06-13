# TSAM Research Log

This file records public repository updates and research-index changes.

## 2026-06-13

### SPARC 175 SLP/SMG freeze record added

Added a new freeze-record page:

- `validation/sparc-175-slp-smg-freeze-record-2026-06-13.md`

The page records the metadata-complete SPARC 175 sky-coordinate audit chain and freezes the projection / node-conditioned routes after negative or degraded results:

- SPARC metadata enrichment reached `SLP_READY = true`: RA/DEC, Distance, Inclination, and ecliptic-coordinate coverage were all 175 / 175; redshift / Vsys was intentionally not queried.
- SLP v0.1 Projection Null Audit returned `DEGRADED`: strongest directional FDR q was 0.01116, but direction strength was weaker than distance / inclination strength.
- SLP v0.1b Confounder Decomposition Audit returned `FAIL_CONFOUNDER_DOMINATED`: partial and regression direction terms were not significant, permutation p was 0.138, the signal was distance-bin dependent and top5 dominated.
- SMG v0.1 Candidate-Node Falsification Audit returned `FAIL_NODE_CONFOUNDER_DOMINATED`: candidate nodes were not significant, not better than random node sets, and top5 dominated.
- SMG v0.2 Node-Conditioned Residual Morphology Audit returned `DEGRADED_WEAK_NODE_ASSOCIATION`: S2 / S_BROAD showed weak inner-inversion morphology, but not strong evidence after FDR correction.
- SMG v0.2b S2/S_BROAD Focused Morphology Forensic Audit returned `FAIL_S2_ARTIFACT_OR_CONTROL_MATCHED`: only 2 / 5 S2 galaxies satisfied stable multiradius inner inversion; 4 / 5 were `err_v` sensitive; 3 / 5 were baryon-overestimate candidates; matched-control and random-group null tests did not pass.

Public claim level:

- Negative / degraded audit archive.
- GTPC, SLP, and SMG are not confirmed.
- No mirror-galaxy model is confirmed.
- No solar-system projection interpretation is supported.
- No dark-matter or standard dynamical model is refuted by this audit chain.
- The next recommended direction is a conventional SPARC error / baryon-dominance forensic audit.

Updated files:

- `docs/data-validation-index.md`
- `validation/sparc-175-slp-smg-freeze-record-2026-06-13.md`

### SPARC 175 rotation-residual validation layer added

Added a new validation page:

- `validation/sparc-175-rotation-residual-layer.md`

The page records the current 175-galaxy SPARC rotation-residual audit track, including:

- Core 3391-row / 175-galaxy master-table structure.
- DAT enrichment status: 175 DAT files parsed, 3391 / 3391 master rows matched, and full `v_gas` coverage.
- GTPC v0.1 dual-target pilot outcome: NGC2403 failed, NGC5005 downgraded, overall failed.
- GTPC v0.2 NGC5005 M1-only gas-proxy result: strong BIC improvement, perfect sign alignment, close peak alignment, but Pearson shape-correlation failure under the fixed threshold.
- SLP projection-readiness boundary: DAT files supply distance but not RA/DEC or inclination, so projection-null testing remains blocked until external metadata is joined.

Public claim level:

- In audit / residual diagnostic candidate.
- Failed or downgraded candidate submodels are retained as part of the audit record.
- Not a final physical interpretation.
- Not a replacement of standard dynamical modeling.
- Not an SLP projection confirmation.

Updated files:

- `README.md`
- `docs/data-validation-index.md`
- `validation/sparc-175-rotation-residual-layer.md`

## 2026-06-12

### Pipeline and formal obstruction validation page added

Added a new validation page:

- `validation/pipeline-and-formal-obstruction-tests.md`

The page summarizes a command-line test batch containing:

- ELG / QSO catalog-level Jacobian jump diagnostics.
- A strong ELG NGC WEIGHT-channel Jacobian jump candidate.
- TSAM v6.0 FITS scanning and clean-pipeline failure / empty-output diagnostics.
- Formal spectral, algebraic, measure-theoretic, Hilbert-span, and BRST-style obstruction tests.
- MPC raw-angle downgrade notes.
- Engineering repair requirements for the pipeline.

Public claim level:

- In audit / formal diagnostic.
- Catalog-level and operator-space diagnostic material only.
- Not a final TSAM confirmation claim.
- Not direct proof of a cosmological axis or new force law.
- Non-confirmatory outputs are explicitly retained as downgrade records.

Updated files:

- `README.md`
- `docs/data-validation-index.md`

### ORCID author identifier added

Added the lead researcher ORCID identifier to public repository metadata and citation guidance.

Updated files:

- `README.md`
- `docs/how-to-cite.md`

Author identifier:

- Bo Wang — ORCID: `0009-0004-1351-1755`

Purpose:

- Improve author disambiguation.
- Strengthen citation metadata for Zenodo and GitHub references.
- Prepare the repository for controlled external review and small-community observation.

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
