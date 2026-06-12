# Midfield Cosmology Validation Layer

## Status

**Audit state:** In audit / diagnostic visualization layer  
**Claim level:** Pattern candidate and systematics audit only  
**Public interpretation:** Do not treat this layer as a standalone confirmation of TSAM, a fixed cosmic axis, or a final cosmological-parameter solution.

This page records the current midfield redshift and angular-density diagnostics supplied for the TSAM public archive. The material is useful as a structured audit layer, but it remains subject to catalog-depth effects, angular-selection effects, redshift-slice reconstruction choices, and post-deconvolution systematics.

## Uploaded source material represented here

- `TSAM_Metric_Pipeline_Diagnostic.png`
- `TSAM_Original_Density_Map.png`
- `TSAM_Midfield_Stage2_Audit.csv`
- `TSAM_3D_Full_Audit.csv`
- `TSAM_3D_Audit_0.4_0.7_Corrected.csv`
- `FAILED_UNAUTHORIZED_AuditReport.csv`
- `TSAM_Cosmo_Posterior_Distributions.png`
- `TSAM_H0_Liquidation_Fixed.png`

The PNG figures are treated as diagnostic visualizations. The CSV tables are treated as the quantitative layer.

## Key quantitative audit notes

### 1. Corrected z = 0.4–0.7 3D density audit

From `TSAM_3D_Audit_0.4_0.7_Corrected.csv`:

- Rows: 2160
- Redshift slices: 30
- Angular step: 5 degrees
- Relative-density normalization: mean approximately 1.0 across the corrected matrix
- Maximum identified density entry:
  - `Z_Slice = 0.42-0.43`
  - `Azimuth_Deg = 75.0`
  - `Relative_Density = 4.691926`
  - `Raw_Count = 102749`

This is consistent with the diagnostic figure labeling a stress-centered feature near `z ≈ 0.42` and an azimuth close to the 75-degree channel.

### 2. Full z ≈ 0.7–1.0 3D density audit

From `TSAM_3D_Full_Audit.csv`:

- Rows: 2232
- Redshift slices: 31
- Angular step: 5 degrees
- Maximum identified density entry:
  - `Z_Slice = 0.72-0.73`
  - `Azimuth_Deg = 100.0`
  - `Relative_Density = 4.680165`
  - `Raw_Count = 197153`

At `Z_Slice = 0.70-0.71`, the 100-degree channel reaches:

- `Relative_Density = 4.663883`
- `Raw_Count = 192596`

This supports a diagnostic distinction between the 75-degree metric-principal channel and a nearby 100-degree background/leakage or catalog-systematics channel. It does not by itself establish a physical causal separation.

### 3. Stage-2 midfield audit matrix

From `TSAM_Midfield_Stage2_Audit.csv`:

- Rows: 2288
- Redshift range: `z = 0.415` to `z = 0.985`
- Angle range: `92.5` to `297.5` degrees
- Verdict counts:
  - `NEARFIELD_INTERCEPT`: 1371
  - `MELTDOWN_GHOST_ZONE`: 917
- Largest positive `Delta`:
  - `z = 0.495`
  - `Angle = 297.5`
  - `Delta = 3.613088`
  - `Curvature = 88172.327358`
  - `Verdict = NEARFIELD_INTERCEPT`
- Largest curvature entry:
  - Same row as above

This table is interpreted as an internal diagnostic partition, not as an externally validated physical taxonomy.

### 4. Unauthorized/rejected reconstruction audit

From `FAILED_UNAUTHORIZED_AuditReport.csv`:

- `masked_boundary_channels_count = 5`
- `masked_blind_channels_count = 30`
- `curvature_outliers_detected = 970`
- `mad_outliers_detected = 0`
- `total_physically_rejected_points = 970`
- `successfully_reconstructed_points = 653`
- `final_global_std = 1.0`

The important public note is that the pipeline is not presented as a naive all-points fit. It contains explicit masking, rejection, and reconstruction accounting. However, rejected-point logic must remain auditable before stronger claims are made.

## Visualization interpretation boundary

The supplied figures include:

- A 6-billion-light-year 75-degree spindle diagnostic.
- A raw 360-degree angular scan map.
- Post-deconvolution cosmological posterior plots.
- A topological-wear / Hubble-tension comparison figure.

These visualizations are useful for communicating the pipeline state, but the public archive should treat them as **diagnostic figures**, not as final proof of a new cosmological model.

## Current public verdict

**Recommended status label:** `MIDFIELD_DIAGNOSTIC_CANDIDATE`

Supported at current archive level:

- A corrected 0.4–0.7 matrix contains a strong 75-degree density channel near `z = 0.42–0.43`.
- A higher-redshift 0.7–1.0 matrix contains a strong 100-degree density channel near `z ≈ 0.7–0.73`.
- The stage-2 audit marks a large number of cells as either `NEARFIELD_INTERCEPT` or `MELTDOWN_GHOST_ZONE`.
- The reconstruction audit explicitly records masked, rejected, and reconstructed points.

Not supported as a public claim at this stage:

- Final proof of a fixed cosmic axis.
- Final resolution of Hubble tension.
- Final cosmological posterior replacement.
- Physical interpretation of `MELTDOWN_GHOST_ZONE` as a real structure.
- Any conclusion that does not survive independent catalog, mask, and selection-function review.

## Required next checks

Before this layer is promoted above diagnostic-candidate status, the following checks are required:

1. Independent catalog replication.
2. Mask and footprint audit.
3. Redshift-bin sensitivity test.
4. Angular-step sensitivity test.
5. Null rotation and coordinate artifact tests.
6. Reproduction from raw catalog inputs.
7. Explicit comparison against standard large-scale-structure selection functions.
