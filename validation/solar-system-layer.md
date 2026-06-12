# Solar-System / Small-Body Validation Layer

## Status

**Current status:** In audit / fast-pass triage result  
**Claim level:** Family-limited near-field orbital-direction anisotropy candidate  
**Public-use boundary:** Not a TSAM confirmation claim

This page records the current small-body validation layer for TSAM-related near-field boundary auditing. It is based on a fast-pass supplement that tests whether first-pass small-body angular non-uniformities survive discovery-bias, quality-control, orbital-geometry, family-level, coordinate-artifact, and multiple-testing checks.

## Scope

This layer is restricted to solar-system small-body angular-distribution audits. It should be read as a local-frame / near-field validation note, not as a direct cosmological proof.

Covered sample classes include:

- Main-belt asteroids
- Mars-crossing objects
- Jupiter Trojans
- Near-Earth objects (NEOs)
- Jupiter-family comets (JFCs)
- Trans-Neptunian objects (TNOs), where available

Primary variables under review include:

- longitude of perihelion / perihelion longitude proxies,
- `varpi`,
- node longitude,
- pole longitude,
- window occupancy fractions,
- Rayleigh resultant-length behavior.

## Input reconstruction status

The fast-pass supplement reconstructed strict and relaxed asteroid and comet tables with required schema columns available.

| Sample | Rows | Status |
|---|---:|---|
| `asteroids_strict` | 246,462 | required columns present |
| `asteroids_relaxed` | 255,906 | required columns present |
| `comets_strict` | 692 | required columns present |
| `comets_relaxed` | 722 | required columns present |

The discovery-bias stratification included first-observation era, absolute magnitude, data arc, observation count, condition code, perihelion distance, semi-major axis, eccentricity, inclination, and perihelion beta.

## Main fast-pass verdict

The current global supplement verdict is:

> **FAST-PASS SUPPORTS WINDOW STABILITY CANDIDATE**

This means the current result is strong enough for triage and repository indexing, but not strong enough for final bias-cleared physical interpretation.

## Family-level verdicts

| Family / group | Current verdict |
|---|---|
| MainBelt | Robust cross-strata non-uniformity candidate |
| MarsCrossing | Robust cross-strata non-uniformity candidate |
| JupiterTrojan | Robust cross-strata non-uniformity candidate |
| NEO | Discovery-bias-sensitive non-uniformity |
| Comet_JFC | Discovery-bias-sensitive non-uniformity |
| TNO | Low-N / inconclusive |

## Window C audit: 330-30 degrees

Window C currently shows stable excess behavior for MainBelt, MarsCrossing, and JupiterTrojan samples under strict and relaxed selections.

| Group | Variable | Strict fraction | Relaxed fraction | Expected fraction | Verdict |
|---|---|---:|---:|---:|---|
| MainBelt | perihelion longitude | 0.2563 | 0.2635 | 0.1667 | WINDOW_STABLE |
| MainBelt | `varpi` | 0.2562 | 0.2636 | 0.1667 | WINDOW_STABLE |
| MarsCrossing | perihelion longitude | 0.3223 | 0.3316 | 0.1667 | WINDOW_STABLE |
| MarsCrossing | `varpi` | 0.3213 | 0.3307 | 0.1667 | WINDOW_STABLE |
| JupiterTrojan | perihelion longitude | 0.2265 | 0.2284 | 0.1667 | WINDOW_STABLE |
| JupiterTrojan | `varpi` | 0.2265 | 0.2281 | 0.1667 | WINDOW_STABLE |
| NEO | perihelion longitude | 0.1828 | 0.1864 | 0.1667 | WINDOW_DISCOVERY_BIAS_SENSITIVE |
| Comet_JFC | perihelion longitude | 0.2168 | 0.2216 | 0.1667 | WINDOW_ORBIT_GEOMETRY_SENSITIVE |

Interpretation boundary: Window C is a stable audit signal for several asteroid families, but the NEO and comet rows remain bias-sensitive and should not be promoted to physical claims.

## Window A audit: 240-285 degrees

Window A currently shows stable deficit behavior for MainBelt, MarsCrossing, and JupiterTrojan perihelion-related variables, with several NEO, comet, and TNO quantities marked as bias-sensitive.

| Group | Variable | Fraction | Expected fraction | Binomial z | Verdict |
|---|---|---:|---:|---:|---|
| MainBelt | perihelion longitude | 0.1056 | 0.1250 | -26.29 | STABLE_DEFICIT |
| MainBelt | `varpi` | 0.1056 | 0.1250 | -26.29 | STABLE_DEFICIT |
| MarsCrossing | perihelion longitude | 0.07128 | 0.1250 | -23.04 | STABLE_DEFICIT |
| MarsCrossing | `varpi` | 0.07113 | 0.1250 | -23.11 | STABLE_DEFICIT |
| JupiterTrojan | perihelion longitude | 0.06786 | 0.1250 | -20.46 | STABLE_DEFICIT |
| JupiterTrojan | `varpi` | 0.06814 | 0.1250 | -20.35 | STABLE_DEFICIT |
| NEO | perihelion longitude | 0.1209 | 0.1250 | -1.295 | BIAS_SENSITIVE |
| Comet_JFC | perihelion longitude | 0.08671 | 0.1250 | -3.046 | BIAS_SENSITIVE |
| TNO | perihelion longitude | 0.1247 | 0.1250 | -0.03853 | BIAS_SENSITIVE |

Interpretation boundary: Window A supports a family-limited directional deficit candidate in robust asteroid families, but not a general solar-system alignment claim.

## Coordinate-artifact check

A longitude-rotation check was used to test coordinate sensitivity. Rayleigh resultant length should remain invariant under longitude rotation. The maximum absolute Rayleigh-R rotation difference was approximately:

```text
1.1102230246251565e-16
```

This supports the current status:

> **NO_MAJOR_ARTIFACT**

However, named LOWZ windows remain descriptive labels. Peaks near 0 degrees must still be treated as coordinate-window-sensitive where applicable.

## Family-size matched null audit

A family-size matched null audit was run with matched samples and repeated draws for several family pairs.

Representative results include:

| Pair | Variable | Matched n | Draws | Median R difference |
|---|---|---:|---:|---:|
| MainBelt vs NEO | perihelion longitude | 5,000 | 500 | 0.1615 |
| MainBelt vs MarsCrossing | perihelion longitude | 5,000 | 500 | -0.1791 |
| MainBelt vs JupiterTrojan | perihelion longitude | 5,000 | 500 | -0.1394 |
| NEO vs MarsCrossing | perihelion longitude | 5,000 | 500 | -0.3409 |
| JupiterTrojan vs MarsCrossing | perihelion longitude | 5,000 | 500 | -0.04059 |

Comet subgroup comparisons were flagged as LOW_N and should not be interpreted as stable family-level conclusions.

## Multiple-testing control

Benjamini-Hochberg FDR correction was applied to binomial window tests and Rayleigh tests. This supports internal triage discipline, but does not by itself convert the fast-pass supplement into a final bias-cleared result.

## Parser crossmatch status

The current MPCORB and CometEls crossmatch validation files were skipped in fast mode.

Therefore:

- no MPCORB science conclusion is allowed,
- no CometEls science conclusion is allowed,
- validated parser crossmatches are required before final statistical interpretation.

## Safe interpretation

The present result supports only the following restrained statement:

> The fast-pass small-body supplement identifies a family-limited near-field orbital-direction anisotropy candidate. The most robust triage signal appears in MainBelt, MarsCrossing, and JupiterTrojan families, while NEO, comet, and TNO-related interpretations remain bias-sensitive, low-N, or parser-limited.

## Forbidden interpretations

The current small-body layer must not be used to claim:

- TSAM confirmation,
- a fixed cosmic axis,
- deep-field causal linkage,
- external forcing proof,
- solar-system alignment proof,
- reuse of the frozen MPC 3.05-sigma result,
- final bias-cleared small-body anisotropy.

## Required next test

The next step is to implement validated MPCORB and CometEls / AllCometEls crossmatch parsers, then rerun only the family / variable combinations that survived this supplement.

Minimum next-test requirements:

1. validated MPCORB parser crossmatch,
2. validated CometEls parser crossmatch,
3. frozen window definitions before re-analysis,
4. retained strict / relaxed sample separation,
5. retained family-size matched null comparison,
6. retained coordinate-rotation artifact test,
7. retained FDR correction,
8. public downgrade rule if NEO / comet / TNO sensitivity dominates.

## Repository claim level

Current repository label:

```text
Solar-system small-body layer: In audit / fast-pass triage / family-limited candidate
```
