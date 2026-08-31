# Contributing

Thank you for helping improve German Reviewer.

## Contribution principles

Contributions should strengthen editorial judgment without turning preferences into universal rules.

- Provide the text type, audience, channel, register, and source context that make a proposed rule necessary.
- Distinguish correctness from idiom, translationese, readability, register, and personal preference.
- Preserve `KEEP > EDIT > REWRITE`.
- Prefer a narrow correction to a growing banned-phrase list.
- Do not add confidential, copyrighted, or personally identifying text as an example or test case.

## Good contributions

- A benchmark case for a demonstrated false positive or missed issue
- A clearer boundary between two review dimensions
- A realistic example that tests meaning or constraint preservation
- A correction to non-idiomatic German in an existing example
- A focused clarification that changes agent behavior for a supported reason

## Before opening a pull request

1. Read `SKILL.md` and the relevant reference file.
2. Check whether the behavior is already covered elsewhere.
3. Add or update a benchmark case when the change affects observable decisions.
4. Keep examples short, original, and self-contained.
5. Check all relative links and Markdown fences.
6. Run the Skill Creator validator against the repository root when available.
7. Run the relevant benchmark cases in a fresh context.

## Pull-request checklist

- The change has a concrete motivation and context.
- No natural sentence is treated as wrong merely because another version exists.
- Meaning, terminology, register, and protected tokens remain intact.
- New rules include boundaries or counterexamples that reduce false positives.
- `README.md` and `CHANGELOG.md` are updated when user-facing behavior changes.
- No generated artifacts, temporary dependencies, secrets, or private source text are included.

## Discussing German judgments

German usage can vary by genre, region, organization, and audience. When reviewers disagree, prefer evidence tied to the stated context. Accept multiple idiomatic solutions when the difference is editorial rather than corrective.

## License

By contributing, you agree that your contribution may be distributed under the repository's MIT License.
