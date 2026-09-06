# Changelog

All notable changes to this project will be documented in this file.

The format is based on Keep a Changelog, and this project uses semantic versioning.

## Unreleased

### Added

- Project-scoped editorial context built from user-provided files
- Draft-and-confirm workflow for creating and updating `.german-reviewer/context.md`
- Automatic use of confirmed context in later reviews within the same project
- Context test suite covering scope, confirmation, address inference, and overrides
- Optional Fachartikel editorial profile for B2B/SaaS articles, product comparisons, industry guides, and professional content marketing
- Article-level guidance for use-case-based judgment, evidence-based promotional calibration, lexical and syntactic repetition, SEO constraints, and editorial CTAs
- KEEP calibration for supported, confident reader promises and explicit protection against automatic hedging
- Distinct language-QA, editorial-polish, and Redakteur-level rewrite depths
- Claim-status rules separating private material, supplied facts, source claims, and approved campaign wording
- Paragraph-function guidance and compact coordination for repeated parallel labels
- Article-level calibration for lexical range, syntactic variety, sentence length, and paragraph rhythm without synonym churn
- Fachartikel calibration example and independent sixteen-case behavioral test suite

### Changed

- Address-form resolution now uses neutral wording where possible and `Sie` only as the final unresolved fallback
- Mid-task address changes apply only to the current text unless the user explicitly requests a persistent project update
- Skill discovery and routing now identify Fachartikel and B2B/SaaS editorial review while keeping the profile context-dependent

## 0.1.0 - 2026-08-30

### Added

- Initial `SKILL.md` workflow and output contract
- `KEEP > EDIT > REWRITE` intervention model
- Seven review dimensions and three severity levels
- Review rubric with calibration examples
- Translationese diagnostic guide and false-positive boundaries
- Tone and register guide covering address forms, channels, and locale
- Editing principles for meaning, terminology, token, and format preservation
- Four representative review examples
- Sixteen-case behavioral benchmark
- Codex UI metadata and GitHub contribution templates
