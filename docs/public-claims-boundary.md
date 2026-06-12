# Public Claims Boundary

This document defines how TSAM-related public claims should be separated when communicating with external readers or communities.

## Purpose

The purpose of this boundary is to prevent category errors.

A repository can contain archived papers, theoretical hypotheses, data-audit notes, reproducibility plans, and open questions. These categories must not be presented as if they carry the same evidential weight.

## Claim categories

| Category | Meaning | Public wording |
|---|---|---|
| Archive record | A public DOI or repository record exists | "This material is archived." |
| Working hypothesis | A theoretical interpretation is being explored | "This is a proposed interpretation." |
| Audit direction | A dataset or test direction has been identified | "This is under audit." |
| Fixed-rule result | Rules were defined before interpretation and applied to data | "This result follows a fixed-rule test." |
| Reproducible result | A workflow can be repeated from documented inputs | "This is reproducible under the documented procedure." |
| Strong claim | A result remains stable across independent tests | "This claim has survived defined validation checks." |
| Downgraded claim | A claim was weakened by stronger data or review | "This claim has been downgraded." |

## Current public boundary

TSAM should currently be presented as:

> A reality-constrained research framework for organizing and testing cosmological and astrophysical anomalies through observational audit, cross-dataset comparison, and explicit provisional labeling.

TSAM should not currently be presented as:

> A fully validated replacement for all existing cosmological models.

## Recommended external wording

Preferred wording:

```text
We are developing an observational-audit framework for comparing residual structures across multiple astrophysical datasets. The framework prioritizes fixed-rule validation, cross-dataset consistency, and explicit labeling of provisional assumptions.
```

Avoid wording such as:

```text
This repository proves that the standard cosmological model is false.
```

or:

```text
TSAM has already solved cosmology.
```

## Discussion rule

When discussing TSAM in external communities, each claim should be tied to one of the following:

1. a Zenodo archive record,
2. a GitHub document,
3. a dataset,
4. a fixed validation rule,
5. or an explicit open question.

If a claim cannot be tied to one of these, it should be marked as speculative.

## Red-line constraints

TSAM public communication should maintain the following constraints:

- Do not promote unverified assumptions into hard definitions.
- Do not treat a single-dataset pattern as cross-dataset validation.
- Do not imply independent acceptance where none exists.
- Do not erase negative or failed tests.
- Do not use community growth as a substitute for validation.
- Do not expand the model without a freeze-review checkpoint.

## Community posture

External community engagement should initially focus on review, criticism, reproducibility, and terminology testing rather than persuasion.

The most useful early feedback is:

- unclear terminology,
- weak claim boundaries,
- missing null tests,
- reproducibility gaps,
- dataset bias concerns,
- and alternative explanations.
