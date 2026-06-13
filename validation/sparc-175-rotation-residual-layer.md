# SPARC 175 Rotation-Residual Validation Layer

## Status

**Audit state:** In audit / residual-structure diagnostic layer  
**Claim level:** Data-audit candidate only  
**Public interpretation:** Do not treat this layer as confirmation of a new galactic-dynamics law, a replacement for dark-matter halo modeling, or proof that galaxies are solar-system projection artifacts.

This page records the TSAM 175-galaxy SPARC rotation-curve audit track. It is designed to show the research direction, hypothesis evolution, validation rules, failure conditions, and downgrade logic used during the current residual-field analysis.

The central discipline of this page is simple: a strong residual fit is not enough. A candidate mechanism must also pass pre-registered physical-alignment tests, proxy-integrity checks, boundary-condition checks, and negative-trigger review.

---

## Dataset layer

### Current working master table

Primary working table:

```text
TSAM_SPARC_175_Master.csv
```

Current core structure:

| Field | Meaning |
|---|---|
| `galaxy_id` | SPARC galaxy identifier |
| `r` | Radius coordinate in the rotation-curve table |
| `v_obs` | Observed rotation velocity |
| `err_v` | Observed velocity uncertainty |
| `v_baryon` | Baryonic velocity contribution used in the current TSAM master table |

Current core table summary:

| Quantity | Value |
|---|---:|
| Rows | 3391 |
| Galaxies | 175 |
| Mean points per galaxy | about 19.38 |

### DAT-enriched rotation-component table

Raw SPARC rotation-model DAT files were parsed from the local `sparc_rotmod_dat` directory and joined back to the master table.

DAT enrichment summary:

| Quantity | Result |
|---|---:|
| DAT files found | 175 |
| Master rows matched to DAT | 3391 / 3391 |
| `v_gas` coverage | 100% |
| Distance coverage from DAT headers | 175 / 175 |
| RA/DEC coverage from DAT headers | 0 / 175 |
| Inclination coverage from DAT headers | 0 / 175 |
| SLP projection-null readiness | false |

This means the DAT files are sufficient for gas-proxy enhancement of rotation-residual tests, but not sufficient for sky-projection audits. A separate SPARC galaxy-level metadata table or external catalog join is still required for RA/DEC and inclination.

---

## Working residual definitions

The current residual audit uses the following basic quantities:

```text
delta_v  = v_obs - v_baryon
delta_v2 = v_obs^2 - v_baryon^2
```

A baryonic overprediction point is defined as:

```text
delta_v < 0
```

This should be interpreted as a dynamical-prior stress marker, not as automatic evidence for a new physical mechanism.

---

## Hypothesis stack

### H0 — baryonic baseline null model

The null baseline is:

```text
v_model = v_baryon
```

The purpose of H0 is not to represent a full standard-galaxy model. It is used as an internal audit baseline for identifying where the current baryonic ledger overpredicts or underpredicts observed velocities.

### H1 — gas-gradient / proxy-gradient damping channel

A reduced one-channel candidate is:

```text
v_model^2 = v_baryon^2 - alpha * r * QP(r)
```

where `alpha >= 0` and `QP(r)` is constructed as a proxy-gradient object:

```text
rho_proxy(r) = max(v_gas_dat^2 / max(r, eps), eps)
T_proxy(r)   = exp(-r / RT)
P_proxy(r)   = rho_proxy(r) * T_proxy(r)
QP(r)        = -1 / rho_proxy(r) * dP_proxy(r) / dr
RT           = 0.3 * Rmax
```

This is called a **gas-proxy-gradient** audit, not a confirmed physical pressure-gradient audit. The current table contains gas rotation components, not an independently measured thermal pressure field.

### H2 — GTPC v0.1 full thermal phase-condensation closure

The broader GTPC v0.1 candidate was:

```text
v_model^2 = v_baryon^2 - alpha * r * QP(r) + beta * S(r; rc, dr)
S(r; rc, dr) = 1 / (1 + exp(-(r - rc) / dr))
```

This full closure attempted to combine an inner damping channel with an outer phase-locking / condensation-like term.

Current audit status:

```text
GTPC v0.1 full closure: failed dual-target pilot audit
```

The full phase-condensation term did not demonstrate independent support in the NGC5005 pilot because the M2 fit collapsed back to the M1 channel. The `beta` term did not earn promotion as an independent physical contribution.

### H3 — SLP slow-light / solar-system projection hypothesis

A stronger speculative hypothesis was discussed under the working label:

```text
SLP v0.1 — Solar-System Slow-Light Projection Hypothesis
```

This hypothesis would reinterpret SPARC galaxy curves as possible projection signatures linked to solar-system boundary conditions or slow-light-like near-boundary effects.

Current audit status:

```text
SLP v0.1: not ready for fitting; projection-null audit only
```

This page explicitly does not claim that galaxies are solar-system projections. Before any SLP fitting is allowed, a separate null audit must test whether residuals show sky-coordinate projection fingerprints using RA/DEC, distance or redshift, and pre-registered directional tests. The current DAT-enriched table is not sufficient for that test because RA/DEC and inclination are missing.

---

## Pilot audit history

### Phase 1 — GTPC v0.1 dual-target pilot

Targets:

```text
NGC2403
NGC5005
```

Models tested:

| Model | Definition | Parameter count |
|---|---|---:|
| M0 | `v_model = v_baryon` | 0 |
| M1 | `v_model^2 = v_baryon^2 - alpha*r*QP(r)` | 1 |
| M2 | `v_model^2 = v_baryon^2 - alpha*r*QP(r) + beta*S(r;rc,dr)` | 4 |

Pre-registered pass conditions included:

| Condition | Required threshold |
|---|---:|
| `Delta_BIC_M2` | `> 10` |
| `R_improve` | `> 0.25` |
| NGC2403 shear-corrected max sigma | `< 5` |
| NGC5005 Pearson alignment | `> 0.8` |
| NGC5005 peak-offset norm | `< 0.15` |
| Parameter boundary check | no boundary touch |

Dual-target pilot outcome:

| Target | Numerical result | Status | Main reason |
|---|---:|---|---|
| NGC2403 | Strong fit improvement | FAIL | Shear-corrected maximum residual remained above the fixed threshold and parameters touched boundaries |
| NGC5005 | Strong fit improvement | DEGRADED | Proxy-gradient alignment was strong, but the QP proxy was low-confidence and M2 collapsed to M1 |
| Overall | mixed | FAIL | At least one target failed and the full closure did not pass physical-alignment review |

Important interpretation boundary:

```text
GTPC v0.1 was technically useful but not physically promoted.
```

It identified a possible residual-structure channel, but it did not validate a full thermal phase-condensation model.

---

### Phase 2 — DAT enrichment and gas-proxy correction

The DAT enrichment step removed the earlier low-confidence baryonic proxy problem by recovering gas rotation components for all rows.

Key result:

```text
v_gas_dat coverage = 100%
```

This permitted a stricter NGC5005 gas-proxy audit using the actual DAT gas component rather than a fallback baryonic proxy.

---

### Phase 3 — GTPC v0.2 NGC5005 M1-only gas-proxy audit

Target:

```text
NGC5005 only
```

The `beta`, `rc`, `dr`, and sigmoid phase-condensation terms were disabled. The model was reduced to:

```text
v_model^2 = v_baryon^2 - alpha * r * QP(r)
```

Reported audit outcome:

| Metric | Result | Threshold | Status |
|---|---:|---:|---|
| `Delta_BIC_M1` | 233.0885 | `> 10` | pass |
| `R_improve_M1` | 0.8795 | `> 0.25` | pass |
| `sign_match_ratio` | 1.0000 | `> 0.75` | pass |
| `pearson_corr` | 0.7749 | `> 0.8` | fail |
| `peak_offset_norm` | 0.0436 | `< 0.15` | pass |

Final status:

```text
GTPC v0.2 NGC5005 gas-proxy audit: FAIL
```

Interpretation:

- The simple full-radius linear gas-gradient damping model is rejected under the fixed Pearson shape-correlation threshold.
- The residual field still shows strong directional and peak-location coherence with the gas-proxy structure.
- The result should be treated as a failed main model but a remaining coherent-factor candidate.

---

## Current public verdict

**Recommended status label:** `SPARC_RESIDUAL_DIAGNOSTIC_IN_AUDIT`

Supported at current archive level:

- The 175-galaxy SPARC residual table is organized as a reproducible local dynamical-prior stress-test layer.
- The raw DAT enrichment successfully recovers gas/disk/bulge rotation components for all 3391 master rows.
- NGC5005 shows strong residual improvement, perfect sign alignment, and close peak alignment under the M1 gas-proxy audit.
- The simple full-radius Pearson shape-correlation condition was not met, so the M1 gas-proxy model fails as a confirmed mechanism.
- GTPC v0.1 full closure is not promoted; its phase-condensation term failed to demonstrate independent support in the pilot audit.

Not supported as a public claim at this stage:

- Confirmation of GTPC as a physical theory.
- Confirmation of a thermal-core diffusion law.
- Confirmation of a physical pressure-gradient mechanism.
- Replacement of dark-matter halo modeling.
- Proof that SPARC galaxies are solar-system projection artifacts.
- Any SLP fitting before RA/DEC, distance/redshift, and projection-null tests are available.

---

## Negative triggers currently active

| Trigger | Status | Meaning |
|---|---|---|
| Full GTPC phase-condensation closure | active downgrade | `beta` term did not earn independent support in the pilot |
| NGC2403 shear-channel pass | failed | shear-corrected max residual did not pass the fixed threshold |
| NGC5005 full-radius Pearson shape alignment | failed | `pearson_corr = 0.7749 < 0.8` under the gas-proxy audit |
| SLP projection readiness | failed data condition | DAT files do not contain RA/DEC or inclination |

---

## Required next checks

Before this layer can move beyond diagnostic-in-audit status, the following checks are required:

1. **NGC5005 v0.2b failure diagnostics**
   - Jackknife Pearson test.
   - Leave-one-radius-out sensitivity.
   - Spearman correlation test.
   - Inner-region-only and inversion-region-only correlation tests.
   - Residual decomposition against `v_gas_dat`, `v_disk_dat`, `v_bulge_dat`, and surface-brightness proxies.

2. **Geometry/systematics sensitivity**
   - Inclination sensitivity test once inclination metadata is joined.
   - Distance-scaling sensitivity test.
   - Mass-to-light ratio perturbation audit.
   - Bulge/disk decomposition sensitivity audit.

3. **Metadata enrichment for projection tests**
   - Join a SPARC galaxy-level metadata table with RA/DEC, inclination, and systemic velocity or redshift.
   - Compute galactic and ecliptic coordinates.
   - Reassess SLP readiness only after coordinate coverage is adequate.

4. **SLP null audit before any SLP fitting**
   - Test residual anisotropy against pre-registered sky directions.
   - Apply multiple-testing correction.
   - Check whether any signal survives removal of NGC5005.
   - Compare direction-dependence against distance/redshift dependence.

5. **Full-sample restraint**
   - Do not run a full 175-galaxy physical promotion scan until the pilot failure diagnostics are complete and the candidate model is refrozen.

---

## Repository communication rule

This page should be cited as an audit-process record. It is not a claim that a new force law, thermal law, or projection mechanism has been discovered.

The current TSAM position for this layer is:

```text
The SPARC 175 residual audit has found structured residual behavior worth further diagnostic testing, but the tested GTPC v0.1/v0.2 models have not passed the fixed promotion criteria.
```
