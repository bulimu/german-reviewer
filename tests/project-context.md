# Project Context Behavioral Tests

This suite tests persistent project-context behavior separately from the core language benchmark. Run each case in an isolated temporary project with the current German Reviewer Skill loaded. Do not reuse `.german-reviewer/` files between cases unless a case explicitly depends on an earlier step.

The evaluator should inspect both the response and any project files created or changed. Exact wording is not required; the behavioral invariants are.

## C01: Establish a context as a draft

### Setup

Provide two project files:

`brand-guide.md`

```text
Address customers with du. Keep the tone clear and professional. Do not use superlatives.
```

`glossary.md`

```text
Keep the product term Workspace in English.
```

### Test prompt

```text
Use $german-reviewer to establish a project context from the two files I provided.
```

### Expected behavior

- Inventories both relevant sources
- Creates `.german-reviewer/context.draft.md`
- Does not create or replace an active `.german-reviewer/context.md`
- Extracts `du`, clear-professional tone, the superlative constraint, and `Workspace`
- Presents the proposed context and asks for confirmation

## C02: Activate only after confirmation

### Setup

Continue from C01 with the draft present and no active context.

### Test prompt

```text
The draft is correct. Confirm and activate it.
```

### Expected behavior

- Writes `.german-reviewer/context.md`
- Marks the context `status: active`
- Includes schema, version, dates, scope, extracted guidance, and sources
- Retires the matching draft
- Does not copy source content into the installed Skill

## C03: Apply active context automatically

### Setup

Start a fresh conversation in a project containing the active context from C02.

### Test prompt

```text
Review this German UI text:

Öffnen Sie Ihren Arbeitsbereich und wählen Sie ein Projekt aus.
```

### Expected behavior

- Reads and applies the active context without requiring an explicit context reminder
- Uses the required `du` address system consistently
- Preserves the approved term `Workspace`
- Produces wording equivalent to `Öffne deinen Workspace und wähle ein Projekt aus.`
- Does not reread all original source files without a reason

## C04: Infer an established address form

### Setup

No active project context and no explicit address instruction.

### Test prompt

```text
Use $german-reviewer to review this text:

Wenn du die Datei später bearbeiten möchtest, öffne sie erneut und wähle deine bevorzugte Option aus.
```

### Expected behavior

- Detects the consistent `du` system from the article
- Does not change it to `Sie`
- Does not ask the user to choose an address form
- Returns `KEEP` if no other issue is found

## C05: Use Sie only as the final fallback

### Setup

No active context, no existing copy, and no audience evidence beyond an unknown external recipient.

### Test prompt

```text
Write one concise German sentence asking an unknown customer to confirm the email address. No address form has been specified.
```

### Expected behavior

- Uses `Sie` because direct address is required and evidence is unresolved
- States the material assumption unless the user requested clean copy only
- Does not claim that all professional or friendly German must use `Sie`

## C06: Preserve neutral wording

### Setup

No active context and no explicit address instruction.

### Test prompt

```text
Use $german-reviewer to review this button label:

E-Mail-Adresse bestätigen
```

### Expected behavior

- Keeps the neutral label
- Does not introduce either `du` or `Sie`
- Does not ask an unnecessary clarification question

## C07: Treat a mid-task change as temporary

### Setup

An active project context requires `Sie`. The current article has already been reviewed using `Sie`.

### Test prompt

```text
Change this article to du.
```

### Expected behavior

- Converts the complete current article consistently, including pronouns, possessives, verbs, imperatives, capitalization, and register
- States that the change applies to the current article
- Leaves `.german-reviewer/context.md` unchanged
- Does not perform blind word replacement

## C08: Require confirmation for a persistent update

### Setup

An active project context currently requires `Sie`.

### Test prompt

```text
Use du for this project from now on.
```

### Expected behavior

- Treats the request as a persistent context update
- Prepares an updated draft and shows the change from `Sie` to `du`
- Keeps the active context unchanged until confirmation
- Activates the new default only after explicit confirmation

## C09: Do not absorb a one-off attachment silently

### Setup

An active context exists. Attach a campaign brief that applies only to one article.

### Test prompt

```text
Review this article using the attached campaign brief.
```

### Expected behavior

- Uses the brief for the current review
- Does not update `.german-reviewer/context.md`
- Does not claim that campaign-specific wording is now a permanent project rule

## C10: Keep project contexts isolated

### Setup

Project A has an active `du` context. Project B has no context.

### Test prompt in Project B

```text
Review this German support message. No address form is specified.
```

### Expected behavior

- Does not search for or apply Project A's context
- Resolves address form only from Project B's current evidence
- Does not claim that a project context exists when none is present

## Pass criteria

- All ten cases satisfy their expected behavior.
- No persistent context is activated or changed without confirmation.
- No context crosses a project boundary.
- No private source material is copied into the reusable Skill.
- No consistent `du`, `Sie`, `ihr`, or neutral system is changed solely because another form is possible.
