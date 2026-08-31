# Changelog

All notable changes to this project will be documented in this file.

The format is based on Keep a Changelog, and this project uses semantic versioning.

## Unreleased

### Added

- Project-scoped editorial context built from user-provided files
- Draft-and-confirm workflow for creating and updating `.german-reviewer/context.md`
- Automatic use of confirmed context in later reviews within the same project
- Context test suite covering scope, confirmation, address inference, and overrides

### Changed

- Address-form resolution now uses neutral wording where possible and `Sie` only as the final unresolved fallback
- Mid-task address changes apply only to the current text unless the user explicitly requests a persistent project update

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
