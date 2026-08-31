# Project Context Workflow

Use this workflow when the user wants German Reviewer to remember project-specific guidance from uploaded or local files. The outcome is a compact, confirmed editorial context for one project. It complements the general review rules without adding client-specific material to the reusable Skill.

## Storage and scope

Store the active context at the current project's root:

```text
.german-reviewer/
|-- context.md
`-- context.draft.md
```

- `context.md` is the only active project context.
- `context.draft.md` is a proposed new or updated context and must not affect reviews before confirmation.
- Keep one active context per project in the first version of this workflow.
- Do not search parent home folders, global Skill directories, sibling projects, or unrelated repositories for context.
- Do not place uploaded source documents inside the installed Skill.
- Do not publish, commit, upload, or otherwise share project context without a separate explicit request.

If the working environment cannot persist project files, explain that limitation and use the supplied files only for the current conversation. Do not claim that the context will be available later.

## Establish a new context

Start this workflow only when the user explicitly asks to establish or create project context. Merely attaching a file does not authorize a persistent context change.

1. Identify the current project root and the files the user intends to use.
2. Inventory relevant sources. Exclude unrelated files and state any file that could not be read.
3. Extract only information that can change editorial decisions: audience, channel, locale, address form, voice, terminology, product facts, content constraints, protected elements, and verification requirements.
4. Distinguish carefully between:
   - required rules and preferences,
   - verified facts and time-sensitive claims,
   - approved terminology and illustrative examples,
   - current guidance and superseded material.
5. Surface conflicts, missing decisions, and uncertain interpretations. Do not silently merge incompatible guidance.
6. Write the proposed result to `.german-reviewer/context.draft.md` and present a concise summary to the user.
7. Ask the user to confirm or correct the draft. Do not activate it yet.
8. After explicit confirmation, write the confirmed version to `.german-reviewer/context.md`, mark it `active`, update its version and date, and retire the matching draft.

Keep an existing active context unchanged while an update draft awaits confirmation.

## Context schema

Use this structure, omitting empty sections. Keep entries concise and traceable rather than copying entire source documents.

```markdown
---
schema: german-reviewer-project-context/v1
status: active
project: <project name>
version: 1
created: YYYY-MM-DD
updated: YYYY-MM-DD
---

# Project editorial context

## Scope
- Applies to: <brands, products, content types, locales>
- Does not apply to: <known exclusions>

## Audience and channels
- Primary audience: <audience>
- Channels: <blog, UI, help, support, email, marketing, etc.>

## Language and address
- Locale: <de-DE, de-AT, de-CH, or unspecified>
- Address form: <du, Sie, ihr, neutral, or infer>
- Strength: <required, preferred, or unspecified>
- Evidence: <source or confirmed user decision>

## Voice and tone
- Required: <rules>
- Avoid: <rules>
- Channel-specific variations: <rules>

## Terminology
- Required terms: <source term -> approved German term>
- Preserve without variation: <names and labels>
- Avoid: <terms with reasons>

## Facts and claims
- Stable facts: <fact + source>
- Time-sensitive facts: <fact + verification date or requirement>
- Unsupported claims to avoid: <claims>

## Editorial and content constraints
- <SEO, GEO, readability, formatting, structural, or accessibility rules>

## Protected content
- <placeholders, markup, legal wording, product names, numbers>

## Open questions and conflicts
- <unresolved item + affected source>

## Sources
| Source | Role | Authority | Date or version | Notes |
|---|---|---|---|---|
| <file> | <style, facts, glossary, examples> | <high, medium, supporting> | <date> | <scope or freshness> |
```

Do not include confidential raw passages when a short rule or fact reference is sufficient. Preserve source paths or titles so a future update can be traced.

## Apply an active context

For each German review in the project:

1. Read `.german-reviewer/context.md` if it exists and has `status: active`.
2. Check its `Scope` before applying it. Ignore it for unrelated brands, locales, or content types.
3. Use the compiled context as the routine source of project rules; do not reread every original source file on every review.
4. Reopen an original source when the compiled entry is ambiguous, sources conflict, or a time-sensitive fact requires verification.
5. Combine the context with the user's current request using the priority rules in `SKILL.md`.
6. Mention the context only when it affects the result, resolves a potentially surprising choice, conflicts with the current request, or contains an unresolved limitation.

An uploaded file supplied for one review is task context only unless the user explicitly asks to update the persistent project context.

## Address-form resolution

Resolve `du`, `Sie`, `ihr`, or neutral wording before editing:

1. Follow the user's latest explicit instruction.
2. Follow an applicable active project-context requirement or preference.
3. Preserve a consistent form established in the article.
4. Use audience and channel evidence when it is strong enough.
5. If the text has no direct address, keep it neutral when natural.
6. If direct address is necessary and the choice remains unresolved, use `Sie` as the final fallback and disclose the assumption.

Do not infer address form from tone alone. A professional text can use `du`; a friendly text can use `Sie`.

Ask before making a large address-form change only when the evidence is genuinely conflicting and the decision would materially reshape the text. Otherwise make the conservative choice and state the material assumption.

When switching forms, recheck pronouns, possessives, verb agreement, imperatives, capitalization, singular or plural reference, and the surrounding level of formality. Do not perform a blind word replacement.

## Temporary overrides and persistent changes

Treat a mid-task instruction such as `Use du for this article` as a temporary override. Apply it consistently to the current text and leave the project context unchanged.

Treat wording such as `Use du for this project from now on` as a request to update the persistent context. Prepare an update draft and require confirmation before activation.

If the user only says `Change it to du` while working on one article, default to current-task scope and state that the project default has not changed. Never convert an ambiguous mid-task request into a silent permanent setting change.

Support these operations:

- `Show the current project context`: read-only summary.
- `Ignore project context for this task`: temporary override without file changes.
- `Update context from these files`: create a draft, show changes, then wait for confirmation.
- `Reset or remove project context`: confirm the exact project and destructive scope before changing files.

## Quality checks

Before activation, confirm that:

- every important rule is traceable to a source or user confirmation;
- explicit requirements are separated from defaults and preferences;
- examples have not been promoted into universal rules;
- time-sensitive facts carry a date or verification note;
- contradictory sources are visible rather than silently reconciled;
- private content remains inside the current project;
- the active context is short enough to apply reliably on routine reviews.
