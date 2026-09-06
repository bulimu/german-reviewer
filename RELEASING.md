# Releasing

Use this checklist for a public release.

## Prepare

1. Update the version in `SKILL.md` metadata.
2. Move completed entries from `Unreleased` into a dated section in `CHANGELOG.md`.
3. Confirm that `README.md`, examples, and output behavior match the release.
4. Check that no private text, credentials, generated artifacts, or temporary dependencies are present.

## Validate

1. Run the Skill Creator `quick_validate.py` script against the repository root.
2. Check all relative Markdown links and code fences.
3. Run every case in `tests/benchmark.md` at least twice with the release candidate.
4. Run the relevant specialized suites, including `tests/project-context.md` and `tests/fachartikel-editorial.md`, when their behavior changed.
5. Record the model, reasoning setting, Skill commit, scores, and reviewer notes.
6. Resolve every critical failure and rerun affected cases.

## Publish

1. Commit the release changes.
2. Create an annotated Git tag matching the version, such as `v0.1.0`.
3. Push the main branch and tag to GitHub.
4. Create a GitHub release using the matching changelog section.
5. Add repository topics such as `german`, `localization`, `lqa`, `editing`, `agent-skill`, and `translationese`.

Do not publish a release when the Skill validator fails or the benchmark contains a critical failure.
