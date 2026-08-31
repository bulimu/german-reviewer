# German Reviewer

An open-source editorial Skill for reviewing translated, localized, and AI-generated German.

German Reviewer goes beyond formal grammar. It asks whether a text reads like natural German written for its actual audience, channel, and purpose, and whether editing is necessary at all.

Version: `0.2.0`

## Core principle

```text
KEEP > EDIT > REWRITE
```

- `KEEP`: The text is already correct, idiomatic, and appropriate.
- `EDIT`: A focused change resolves a real issue.
- `REWRITE`: The wording or structure is substantially unsuitable and local edits are insufficient.

Natural text stays unchanged. A possible alternative is not automatically an improvement.

## What it reviews

| Dimension | Main question |
|---|---|
| Native naturalness | Would a native German writer plausibly formulate it this way here? |
| Translationese | Does source-language transfer make the German less idiomatic or clear? |
| Grammar and syntax | Is the German formally correct? |
| Word choice and collocations | Are words precise and combinations idiomatic? |
| Style and readability | Is the text clear, coherent, and suitable for its genre? |
| Tone and register | Does the language fit the audience, channel, and address form? |
| Meaning preservation | Does the German preserve claims, scope, conditions, and certainty? |

Issues are classified as `Must fix`, `Recommended`, or `Optional`.

## Suitable tasks

- German native-language editorial review
- Localization QA with or without a source text
- Review of AI-generated German
- Blog, documentation, UI, support, email, marketing, and business copy
- `du`, `Sie`, `ihr`, and neutral-address consistency
- Meaning, terminology, placeholder, and formatting preservation

The Skill is not a generic synonym generator, automatic humanizer, source-text fact checker, or substitute for legal, medical, financial, or regulatory experts.

## Quick start

1. Download or clone this repository.
2. Make the `german-reviewer` folder available to an agent that supports `SKILL.md`-style skills.
3. Invoke the Skill and provide the German text plus any useful context.

```text
Use $german-reviewer to review this German text.

Text type: Product help article
Audience: General users in Germany
Address: du
Tone: Neutral-professional
Source text: Optional
Glossary or constraints: Optional

German:
<your German text>
```

## Direct source review without a context file

German Reviewer can review against uploaded or local project reference files without compiling them into `.german-reviewer/context.md`. This mode is useful when source documents change frequently, apply only to one deliverable, or should remain the direct source of truth.

For a one-off review, attach the relevant files and make the scope explicit:

```text
Use $german-reviewer to review this German text against the reference files I provided.

Use the files for this review only. Do not create or update .german-reviewer/context.md.
```

For repeated reviews in one local project, keep the source documents in a project folder such as `context-sources/`, or add them to the project's shared Sources. Add a durable project instruction such as:

```text
For German reviews, read the files relevant to the current task from context-sources.
Treat them as the source of truth for brand voice, terminology, and product facts.
Do not create or update .german-reviewer/context.md unless the user explicitly asks.
```

After that, a normal review request can be short:

```text
Use $german-reviewer to review this German article using the relevant project sources.
```

In direct source mode:

- No project context file is created or changed.
- A file attached to one chat applies only to that task unless it is also available as a shared project source or local project file.
- The reviewer reads the sources relevant to the current decision rather than treating every example as a universal rule.
- Conflicts, unreadable files, and time-sensitive facts are surfaced instead of silently resolved or assumed current.

Direct source review favors the latest original documents but may require more source reading on each task. A compiled project context is faster and more consistent for stable, repeated rules, but it must be maintained when the underlying sources change.

## Reusable project context

German Reviewer can compile uploaded style guides, glossaries, product facts, approved examples, and content requirements into one confirmed context for the current project.

Start once with:

```text
Use $german-reviewer to establish a project context from the files I uploaded.
```

The Skill inventories the relevant files, extracts editorially actionable guidance, reports conflicts and time-sensitive facts, and prepares a draft. The draft becomes active only after the user confirms it. The confirmed context is stored at:

```text
.german-reviewer/context.md
```

Future German reviews in the same project automatically apply that active context. Original source files do not need to be reread on every routine review. A newly attached file affects only the current task unless the user explicitly asks to update the persistent context.

Useful follow-up requests include:

- `Show the current project context.`
- `Update the project context from these new files.`
- `Ignore the project context for this review.`
- `Use du for this article.` This is a temporary override.
- `Use du for this project from now on.` This proposes a persistent update and requires confirmation.

Project contexts remain separate from the public Skill. German Reviewer does not publish or commit private project material automatically.

For Codex environments with local skills, place the repository folder in the configured skills directory. The [OpenAI Skills API](https://developers.openai.com/api/reference/python/resources/skills/methods/create) also supports uploading skill files as a directory or ZIP archive.

## Default output

For natural text:

```text
Decision: KEEP

No changes needed.
```

For an edit or rewrite, the default response contains:

- The `EDIT` or `REWRITE` decision
- A clean revised German text
- Findings with severity, primary review dimension, suggestion, and concise reason
- Material assumptions only when needed

When the user asks for a clean copy only, the Skill returns only the revised German.

## Examples

- [KEEP natural German](examples/01-keep.md)
- [Focused EDIT](examples/02-focused-edit.md)
- [Source-based localization QA](examples/03-localization-qa.md)
- [Justified REWRITE](examples/04-rewrite.md)

These examples calibrate judgment. They are not universal wording templates.

## Repository structure

```text
german-reviewer/
|-- README.md
|-- SKILL.md
|-- LICENSE
|-- CHANGELOG.md
|-- CONTRIBUTING.md
|-- RELEASING.md
|-- agents/
|   `-- openai.yaml
|-- references/
|   |-- project-context.md
|   |-- review-rubric.md
|   |-- translationese.md
|   |-- tone-and-register.md
|   `-- editing-principles.md
|-- examples/
|   |-- README.md
|   |-- 01-keep.md
|   |-- 02-focused-edit.md
|   |-- 03-localization-qa.md
|   `-- 04-rewrite.md
|-- tests/
|   |-- benchmark.md
|   `-- project-context.md
`-- .github/
    |-- ISSUE_TEMPLATE/
    `-- pull_request_template.md
```

## Testing

The [v0.1 benchmark](tests/benchmark.md) contains 16 cases covering:

- Correct `KEEP`, `EDIT`, and `REWRITE` decisions
- Grammar and collocations
- Translationese and false-positive resistance
- Source-based meaning preservation
- Address form and locale
- Approved terminology and protected placeholders
- Clean-copy output
- UI ambiguity and high-stakes scope boundaries

The benchmark scores observable behavior rather than exact wording. Release candidates should have no critical failures and meet the threshold defined in the benchmark.

The separate [project-context suite](tests/project-context.md) tests context creation, confirmation, automatic application, address-form inference, and temporary versus persistent overrides.

## Design principles

- Preserve meaning, facts, terminology, uncertainty, and structural tokens.
- Prefer the smallest effective intervention.
- Do not treat watchlist phrases as banned words.
- Do not make all German casual, short, active, or promotional.
- Separate language editing from factual or professional-domain verification.
- State an assumption only when it materially affects the result.
- Keep client and project context outside the reusable Skill and activate changes only after confirmation.

## Limitations

- Native naturalness remains context-dependent and benefits from human review before publication.
- A source text improves meaning-preservation checks but does not prove factual accuracy.
- Legal, medical, financial, safety, and regulatory content still requires qualified domain review.
- Model behavior can vary across versions and runs; use the benchmark for regression testing.

## Contributing

Contributions are welcome. Read [CONTRIBUTING.md](CONTRIBUTING.md) before proposing a new rule, example, or benchmark case. New guidance should be supported by a concrete context and demonstrated failure, not only by personal preference or a phrase blacklist.

## License

Released under the [MIT License](LICENSE).
