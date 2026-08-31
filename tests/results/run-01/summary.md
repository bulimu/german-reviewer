# German Native Editor Benchmark: Run 01

Result: **PROVISIONAL PASS**

| Metric | Result | Threshold |
|---|---:|---:|
| Cases completed | 16/16 | 16/16 |
| Total score | 192/192 | At least 164/192 |
| Critical failures | 0 | 0 |
| Cases below 8/12 | 0 | 0 |
| Correct intervention decisions | 16/16 | At least 15/16 |

## Dimension totals

| Dimension | Score |
|---|---:|
| Decision and intervention | 32/32 |
| Issue detection | 32/32 |
| German quality | 32/32 |
| Meaning preservation | 32/32 |
| Constraint preservation | 32/32 |
| Output and reasons | 32/32 |

## What passed

- Natural `KEEP` cases remained unchanged.
- Local defects received proportionate `EDIT` decisions.
- The structurally weak paragraph received a justified `REWRITE`.
- Meaning, modality, approved terminology, locale, and protected placeholders were preserved.
- The ambiguous UI case stated its assumption and presented both relevant interpretations.
- The legal-language case stayed within linguistic review.

## Interpretation limits

This is a valid development run but not yet strong release evidence:

- The model and reasoning setting used the Codex configured defaults and were not pinned in task metadata.
- One run does not measure consistency; the benchmark protocol requires at least two runs for release comparisons.
- Scoring is AI-assisted and should be confirmed by a fluent German reviewer.
- Several benchmark phenomena resemble the Skill's calibration examples, so a separate unseen-text benchmark is still needed to test generalization.

## Next release gate

Repeat all 16 cases with an explicitly fixed model and reasoning setting, then compare decisions, dimension scores, and critical failures with this run.

