# SPARC 175 SLP/SMG Freeze Record — 2026-06-13

## Status

**Audit state:** Frozen after negative / degraded audits  
**Claim level:** Audit record only  
**Public interpretation:** This record does not confirm GTPC, SLP, SMG, a mirror-galaxy model, a solar-system projection model, or any replacement for standard galaxy-dynamics modeling.

This page records the June 13, 2026 SPARC 175 residual-audit chain after metadata enrichment enabled sky-coordinate tests. It is a freeze record: the tested projection and node-conditioned hypotheses are retained as documented failures or degraded diagnostics, not promoted physical interpretations.

---

## Dataset and metadata status

Primary SPARC working file after enrichment:

```text
TSAM_SPARC_175_Master_SLP_Metadata_Enriched.csv
```

Coverage after enrichment:

| Quantity | Result |
|---|---:|
| Valid galaxies | 175 |
| RA/DEC coverage | 175 / 175 |
| Distance coverage | 175 / 175 |
| Inclination coverage | 175 / 175 |
| Ecliptic coordinate coverage | 175 / 175 |
| Redshift / Vsys | not queried |
| Unmatched galaxies | 0 |
| SLP_READY | true |

Important boundary: redshift / Vsys was deliberately not queried after distance coverage became sufficient for the projection-null audit. The projection tests remain sky-coordinate and distance / inclination confounder audits, not a physical projection-model fit.

---

## GTPC status carried into freeze

| Track | Result | Interpretation |
|---|---|---|
| GTPC v0.1 dual-target pilot | FAIL | NGC2403 failed the fixed shear-corrected residual threshold; NGC5005 downgraded; full closure not promoted. |
| GTPC v0.2 NGC5005 gas-proxy audit | FAIL | Strong BIC / sign / peak-location coherence remained, but Pearson shape correlation did not pass the fixed threshold. |

Current GTPC conclusion:

```text
GTPC remains a failed / downgraded residual-diagnostic track. No physical pressure-gradient or thermal phase-condensation model is confirmed.
```

---

## SLP projection-null audit sequence

### SLP v0.1 — Projection Null Audit

Reported result:

| Metric | Result |
|---|---:|
| Overall | DEGRADED |
| Valid galaxies | 175 |
| Strongest directional q | 0.011164541336372317 |
| Direction strength | 0.27557321988356476 |
| Distance / inclination strength | 0.4001138899611921 |
| NGC5005 dominated | false |
| Top3 dominated | false |

Interpretation:

- A pre-registered directional signal existed after FDR correction.
- The signal was not dominated by NGC5005 or the top three residual galaxies.
- However, the direction strength was weaker than the distance / inclination confounder strength.
- Therefore, the result did not pass to model fitting.

### SLP v0.1b — Confounder Decomposition Audit

Reported result:

| Metric | Result |
|---|---:|
| Overall | FAIL_CONFOUNDER_DOMINATED |
| Valid galaxies | 175 |
| Strongest partial q | 0.21409113437407565 |
| Strongest regression q | 0.7304562974364845 |
| Permutation p | 0.138 |
| Inclination dependent | false |
| Distance-bin dependent | true |
| Sky-density confounded | false |
| Single-galaxy unstable | false |
| Top5 dominated | true |

Interpretation:

```text
The SLP directional signal did not survive confounder decomposition. After controlling Distance, Inclination, Rmax, and n_points, no direction term remained significant. Random sky-coordinate permutation was not passed. The signal was distance-bin dependent and top5 dominated.
```

SLP status after freeze:

```text
SLP strong-form projection hypothesis is frozen. No SLP fitting or SPARC radius remapping is allowed from this audit chain.
```

---

## SMG / candidate-node audit sequence

SMG in this record means a **Solar–Mirror-Galaxy coupled projection hypothesis** considered as a speculative audit label. It does not involve the Moon / lunar / 太阴 variables and does not assert that external galaxies are projections.

### SMG v0.1 — Pre-Registered Candidate-Node Falsification Audit

Candidate nodes were pre-registered from cleaned LRG/QSO node candidates rather than fitted from SPARC residuals.

Reported result:

| Metric | Result |
|---|---:|
| Overall | FAIL_NODE_CONFOUNDER_DOMINATED |
| Valid galaxies | 175 |
| Best non-N3 node q | 0.5335377327384094 |
| Best combined node q | 0.9877324817444129 |
| Random node p | 0.9998 |
| Top5 dominated | true |
| Distance-bin dependent | false |
| Inclination dependent | false |

Interpretation:

```text
The pre-registered LRG/QSO candidate nodes did not explain SPARC 175 residual morphology as a global node model. They were not significant, were not better than random node sets, and were top5 dominated.
```

### SMG v0.2 — Node-Conditioned Residual Morphology Audit

Reported result:

| Metric | Result |
|---|---|
| Overall | DEGRADED_WEAK_NODE_ASSOCIATION |
| Node-source integrity | main sources weighted / random-normalized |
| S2 / S_BROAD profile | NODE_ASSOCIATED_WITH_INNER_INVERSION |
| S2 galaxies | CamB, NGC1705, UGC02916, UGC02953, UGC03205 |
| Strongest S2 distribution metric | max_abs_residual_sigma |
| S2 Cliff's delta | 0.3788235294117647 |
| S2 Mann-Whitney FDR q | 0.5197413137322622 |
| Top5 high-sigma galaxies | NGC2403, NGC5055, DDO154, UGC00128, UGC09133 |
| Top5 node status | NO_NODE |

Interpretation:

- The cleaned source-integrity check passed for main nodes.
- S2 / S_BROAD showed a weak node-conditioned inner-inversion profile.
- The effect size was medium for max_abs_residual_sigma, but FDR-corrected significance was not reached.
- This justified a focused forensic audit, not physical promotion.

### SMG v0.2b — S2/S_BROAD Focused Morphology Forensic Audit

Reported result:

| Metric | Result |
|---|---:|
| Overall | FAIL_S2_ARTIFACT_OR_CONTROL_MATCHED |
| S2 matched galaxies | 5 / 5 |
| S2 multiradius inner-inversion count | 2 / 5 |
| S2 single-point driven count | 0 / 5 |
| S2 err_v sensitive count | 4 / 5 |
| S2 baryon-overestimate candidate count | 3 / 5 |
| Strongest matched-control metric | residual_sign_flip_count |
| Matched-control Cliff's delta | 0.4095 |
| Matched-control permutation p | 0.06199 |
| Matched-control bootstrap CI | [-0.2476, 2.095] |
| Strongest random-group statistic | group_mean_max_abs_residual_sigma |
| Random-group p_high | 0.09449 |
| Observed above 95th percentile | false |
| S2 and Top5 distinct channels | false |

Interpretation:

```text
S2/S_BROAD does not constitute a stable node-conditioned morphology family. Only UGC02916 and UGC02953 satisfy stable multiradius inner inversion. The S2 group is not single-point driven, but it is strongly err_v sensitive and partly baryon-overestimate sensitive. Matched-control and random-group null tests did not pass. S2 and non-node Top5 did not separate into distinct residual channels.
```

SMG status after freeze:

```text
SMG-SPARC node-conditioned morphology route is frozen. No mirror-galaxy fitting, mirror-balancing, or projection interpretation is allowed from these results.
```

---

## Active negative triggers

| Trigger | Status | Meaning |
|---|---|---|
| GTPC full phase-condensation closure | active downgrade | The phase / beta term did not earn independent support. |
| NGC5005 gas-proxy full-radius shape correlation | failed | Pearson shape threshold was not met. |
| SLP projection null | degraded then failed | Initial directional signal did not survive confounder decomposition. |
| SMG candidate nodes | failed | Pre-registered nodes were not significant and were not better than random node sets. |
| SMG S2 focused morphology | failed | S2 weak profile was err_v / baryon-overestimate sensitive and did not beat matched-control / random-group tests. |

---

## Current public verdict

Supported as an audit record:

- The SPARC 175 dataset has been enriched to support sky-coordinate residual audits.
- GTPC, SLP, and SMG candidate chains were tested under fixed negative-trigger logic.
- Several structured residual patterns were observed, but the candidate physical interpretations failed or degraded under confounder and forensic testing.
- The strongest surviving next direction is not a projection model; it is a conventional **SPARC error / baryon-dominance forensic audit**.

Not supported as a public claim:

- GTPC confirmed.
- SLP confirmed.
- SMG confirmed.
- Mirror galaxy confirmed.
- Galaxies are solar-system projections.
- Dark matter disproved.
- New galactic-dynamics law discovered.
- SPARC radius remapping justified.
- Mirror-balancing or projection fitting justified.

---

## Recommended next audit

```text
SPARC v0.3 Error/Baryon Dominance Forensic Audit
```

Primary questions:

1. Which galaxies are primarily `err_v` sensitive?
2. Which galaxies are primarily baryon-overestimate candidates, where `v_baryon > v_obs` dominates the residual stress?
3. Which galaxies retain robust residual morphology after replacing sigma-weighted diagnostics with robust denominators?
4. Do UGC02916 and UGC02953 survive as stable inner-inversion cases after error and baryon-overestimate controls?
5. Are the non-node Top5 high-sigma galaxies ordinary uncertainty-weighted outliers or structurally distinct residual systems?

---

## Repository communication rule

This page is a freeze record. It should be cited as a negative / degraded audit archive, not as a discovery claim.

Current TSAM position for the SPARC 175 residual layer:

```text
The SPARC 175 audit found structured residual behavior, but the tested GTPC, SLP, and SMG interpretations did not pass fixed promotion criteria. The projection and node-conditioned routes are frozen pending a conventional error / baryon-dominance forensic audit.
```
