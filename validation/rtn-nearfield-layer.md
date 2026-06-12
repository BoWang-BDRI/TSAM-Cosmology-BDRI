# RTN Near-Field Validation Layer

## Status

**Audit state:** In audit / near-field dynamical-response diagnostic  
**Claim level:** Model-response comparison candidate only  
**Public interpretation:** Do not present this layer as a completed N-body residual proof, a confirmed new force term, or a standalone solar-system confirmation of TSAM.

This page records the current RTN non-conservative acceleration and epsilon-audit visual diagnostics supplied for the TSAM public archive.

## Uploaded source material represented here

- `tsam_v11_rtn_audit.png`
- `tsam_v15_phase_locked_spectrum.png`
- `tsam_v16_epsilon_audit.png`

The available material in this upload is visual rather than a raw reproducibility table. Therefore, this page is intentionally conservative and records the figures as diagnostic observations only.

## Figure-level audit notes

### 1. TSAM v11 RTN three-axis non-conservative deconstruction

The v11 figure compares observed and modeled residuals in the RTN frame:

- Radial axis `R` shows a strong near-Sun response that decays with heliocentric distance.
- Transverse axis `T` shows a strong negative near-Sun response and decay trend.
- Normal axis `N` shows a broad residual hump at larger heliocentric distances, while the displayed model term is comparatively weak.

Public interpretation boundary:

- The R/T decay-like behavior may be used as a model-response diagnostic.
- The N-axis mismatch should be treated as an unresolved residual structure, not as a solved physical component.

### 2. TSAM v15 RTN non-gravitational acceleration response spectrum

The v15 figure compares radial, transverse, and normal acceleration response curves for:

- `67P`
- `Borisov`
- `Apophis`

The response magnitudes differ strongly by object and heliocentric-distance regime. The plot is useful for visualizing object-dependent response structure, but it is not yet sufficient for a generalized claim without the source ephemeris, object selection criteria, and residual-generation method.

Public interpretation boundary:

- Suitable phrase: `object-dependent RTN response spectrum candidate`.
- Avoid phrase: `universal non-gravitational law confirmed`.

### 3. TSAM v16 normal-axis source decomposition and epsilon audit

The v16 figure distinguishes:

- Raw residual `A_N(r)` under a Kepler-only baseline.
- Remaining residual `epsilon_N(r)` after full N-body stripping.

The figure is important because it introduces an explicit residual-after-stripping concept. However, public claims require a clear reproducibility table listing bodies, ephemeris source, integration settings, perturbation model, and stripping order.

Public interpretation boundary:

- Suitable phrase: `epsilon-audit candidate after N-body stripping`.
- Avoid phrase: `final physical source decomposition`.

## Current public verdict

**Recommended status label:** `RTN_RESPONSE_DIAGNOSTIC_CANDIDATE`

Supported at current archive level:

- RTN response figures show structured axis-dependent residual behavior.
- R/T components show visually decay-like behavior in the v11 diagnostic.
- N-axis residual behavior remains nontrivial and is explicitly separated in the v16 epsilon audit.
- Object-specific response curves are shown for 67P, Borisov, and Apophis in the v15 diagnostic.

Not supported as a public claim at this stage:

- A confirmed new non-gravitational force law.
- A finished solar-system proof of TSAM.
- A closed N-body residual solution.
- A universal acceleration spectrum across object classes.
- Any claim that cannot be reproduced from raw ephemeris and force-model inputs.

## Required next checks

Before this layer is promoted beyond diagnostic-candidate status, the following are required:

1. Source ephemeris declaration.
2. Object-selection rule freeze.
3. Reproducible RTN coordinate transformation script.
4. Full N-body stripping log.
5. Residual error propagation.
6. Independent run on at least one external ephemeris source.
7. Per-object table with fit parameters, uncertainties, and residual diagnostics.
