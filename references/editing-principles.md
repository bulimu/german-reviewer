# Editing Principles

Use this guide after the review identifies a real need to change the German. The [review rubric](review-rubric.md) decides whether an issue exists; this guide controls the scope and safety of the edit.

The objective is not to produce the editor's preferred version. It is to deliver the smallest revision that resolves supported issues while preserving the author's intended content and the user's constraints.

## Editorial contract

Every change must do at least one of the following:

- Correct an error
- Restore or protect meaning
- Remove demonstrable non-idiomatic wording
- Improve a concrete readability problem
- Align the text with an evidenced audience, channel, tone, or terminology requirement

Do not change text merely to demonstrate activity, vary vocabulary, shorten every sentence, or make the result sound more like a generic AI writing style.

## Preservation hierarchy

Protect content in this order when editing goals compete:

1. Explicit user instructions and protected structural elements
2. Meaning, function, facts, and degree of certainty
3. Required terminology, product labels, and legal or technical distinctions
4. Audience, address form, register, and authorial voice
5. Document structure, cohesion, and information order
6. Individual wording, rhythm, and stylistic preference

Lower-priority elements may change only when necessary to protect or improve a higher-priority element. Do not sacrifice meaning for elegance or terminology consistency for synonym variety.

## Apply a change budget

Treat every edit as a cost that needs a reason.

- Apply all supported `Must fix` changes.
- Apply `Recommended` changes when they improve the requested deliverable without creating new drift.
- Apply `Optional` changes only when the user requests alternatives, a specific stylistic transformation, or an especially polished variant where the preference is relevant.
- Preserve unaffected wording around a local issue.
- Do not bundle unrelated stylistic changes into a necessary correction.

Several possible improvements do not automatically justify a full rewrite. Judge the distribution and interaction of issues, not their raw count.

If no supported change survives this budget, return `KEEP`. For `EDIT`, preserve the existing structure and all unaffected wording. Use the `REWRITE` safeguards below only when focused editing is insufficient.

## Edit at the smallest effective level

Choose the narrowest operation that fully resolves the issue:

1. Character or punctuation correction
2. Word-form or agreement correction
3. Word or collocation replacement
4. Phrase or clause restructuring
5. Sentence rewrite
6. Paragraph or document rewrite

Stop when the problem is resolved. Recheck the surrounding syntax because a local change can affect agreement, references, punctuation, or information flow.

```text
Original: Die Daten wird automatisch gespeichert.
Minimal edit: Die Daten werden automatisch gespeichert.
Unnecessary rewrite: Das System speichert sämtliche Informationen automatisch für dich.
```

The unnecessary rewrite adds an actor, changes `Daten` to a broader term, and adds a user benefit that the original did not state.

## Preserve semantic invariants

`Meaning preservation` is the governing constraint for every edit and rewrite.

Compare the revision with the original and any source text across these elements:

| Invariant | Common drift |
|---|---|
| Actor | Adding, removing, or changing who performs an action |
| Action and object | Replacing the task or changing what it affects |
| Negation | Losing or moving `nicht`, `kein`, or an exception |
| Modality | Changing `kann`, `darf`, `soll`, `muss`, or `wird` |
| Certainty | Turning a possibility, estimate, or tendency into a fact |
| Quantity | Losing `einige`, `alle`, `bis zu`, minimums, or maximums |
| Scope | Broadening or narrowing who, what, or where a statement applies |
| Conditions | Omitting `wenn`, `nur`, `sofern`, prerequisites, or exclusions |
| Time | Changing dates, duration, frequency, sequence, or default behavior |
| Causality | Replacing correlation, purpose, or sequence with a causal claim |
| Product capability | Adding availability, automation, compatibility, or performance claims |

Small words can carry the most important meaning.

```text
Source meaning: The feature can reduce manual work.
Safe German: Die Funktion kann den manuellen Aufwand verringern.
Drifted edit: Die Funktion reduziert den manuellen Aufwand.
```

The drifted version turns a possibility into a definite outcome.

## Use the source without copying its form

When a source text is available:

- Treat it as the primary meaning reference unless the user identifies another authority.
- Preserve claims, examples, conditions, emphasis, and uncertainty.
- Allow German syntax, sentence boundaries, and information order to differ when this improves the target naturally.
- Do not add explanatory detail merely because it seems helpful.
- Do not remove a detail merely because it sounds repetitive in isolation.

If the source appears ambiguous, factually questionable, or internally inconsistent, flag the source-side problem. Do not silently invent the intended meaning. If a German localization deliberately improves a harmless source weakness without changing meaning, do not force it back into source order.

When no source is available, preserve every plausible reading that matters. Avoid claiming a mistranslation based on guesswork.

## Protect terminology

Use terminology in this order of authority:

1. Explicit glossary or terminology instruction
2. Exact product and interface labels
3. Approved reference content or style guide
4. Domain-standard terminology for the stated audience
5. The consistent terminology already used in the text

Do not replace an approved term with a synonym for variety. Do not alternate between terms that may refer to different concepts, such as `Konto`, `Profil`, and `Account`, unless the product defines them as interchangeable.

If a required term creates an apparent language problem, distinguish the term from its surrounding grammar. Keep the term where possible and fix the sentence around it. When the glossary itself seems contradictory or unusable, surface the conflict instead of silently overriding it.

## Protect names, data, and structural tokens

Preserve unless explicitly authorized to change:

- Brand, product, company, and personal names
- Numbers, prices, dates, units, percentages, and version numbers
- URLs, email addresses, file paths, commands, code, and API identifiers
- UI labels and keyboard shortcuts
- Markdown, HTML, XML, and other markup
- Variables and placeholders such as `{{first_name}}`, `%s`, `{0}`, and `<name>`
- Tracking parameters, anchors, IDs, and localization keys
- Required keywords and character limits

Never translate or normalize the inside of a placeholder. Ensure that every protected token appears exactly once in the revision unless the task explicitly requires another count.

```text
Original: Hallo {{first_name}}, öffne <settings_link>deine Einstellungen</settings_link>.
Safe edit: Hallo {{first_name}}, öffne <settings_link>die Einstellungen</settings_link>.
```

The wording can change while the variable and tags remain intact.

## Preserve format and document function

Keep the existing hierarchy, list structure, headings, links, tables, code fences, and paragraph purpose unless restructuring is part of the requested edit.

Format can carry meaning:

- A button label is not an explanatory sentence.
- A heading is not a paragraph.
- A warning is not ordinary body copy.
- Separate localization strings may lack shared runtime context.
- Repeated terminology may be necessary because UI strings appear independently.

Do not merge or split strings when their implementation boundaries are unknown. For character-limited copy, count the final text if a reliable counting method is available and report when the requirement cannot be met without changing meaning.

## Preserve voice without preserving defects

Retain the writer's suitable level of expertise, directness, warmth, formality, and sentence rhythm. Natural German is not always conversational, short, active, or simple.

Do not systematically:

- Replace passive voice with active voice
- Convert nouns into verbs
- Remove all repetitions
- Shorten every sentence
- Add `du`, `Sie`, or personal pronouns
- Add contractions, humor, emojis, idioms, or promotional language
- Replace common words with more sophisticated alternatives

Change one of these features only when it creates a supported issue in context.

## Edit beyond the sentence when necessary

Sentence-level correctness does not guarantee a coherent text. For paragraphs and documents, also check:

- Pronoun and reference clarity across sentences
- Logical progression and paragraph focus
- Repeated openings, transitions, and conclusions
- Terminology and address consistency
- Heading-to-section alignment
- Whether an edit creates repetition or contradiction nearby

Reorder or combine material only when local edits cannot fix the text-level problem. Preserve the author's argument and do not introduce a new outline merely because another structure is possible.

## Rewrite safeguards

Use `REWRITE` only when focused edits cannot produce natural, coherent, context-appropriate German. Before rewriting:

1. List the claims, instructions, conditions, examples, and protected elements that must survive.
2. Identify the target audience, channel, address form, and register.
3. Decide which structural problem makes local editing insufficient.
4. Draft the new German from the intended meaning rather than the source syntax.
5. Map the rewritten content back to the original and source.

A rewrite does not authorize adding:

- New facts, examples, statistics, or product capabilities
- A stronger promise or clearer certainty than the source
- A marketing hook, call to action, introduction, or conclusion
- SEO keywords or headings that were not requested
- A new brand personality

Keep usable original wording when it already serves the rewrite.

## Handle ambiguity proportionally

Do not make a high-impact interpretive choice silently.

- Ask for clarification when ambiguity changes a critical instruction, legal obligation, product claim, or central argument and the task cannot be completed safely without it.
- State a concise assumption when the risk is limited and the task can proceed.
- Preserve the ambiguous wording when the user requested language correction only and resolving it would require unsupported interpretation.
- Offer alternatives when two readings are both plausible and materially different.

Do not turn every minor uncertainty into a question. Escalate only when the choice materially affects the result.

## Separate language editing from fact-checking

Language review does not prove that a claim is true. Do not silently correct facts from memory or add evidence that was not supplied.

If a claim appears questionable:

- Keep the linguistic edit separate from the factual concern.
- Flag the concern as unverified rather than presenting it as an error.
- Verify externally only when the user requests fact-checking and suitable sources are available.

For legal, medical, financial, safety, or regulatory content, limit the default task to linguistic and meaning-preservation review. Do not simplify away defined terms, obligations, warnings, or qualifications.

## Give reasons that support the change

A reason should identify the defect and the benefit of the correction.

Weak:

```text
Sounds better.
```

Useful:

```text
„eine Entscheidung machen“ is not the idiomatic German collocation. Use „eine Entscheidung treffen“.
```

For context-dependent edits, name the context:

```text
The passive formulation is grammatical, but the direct imperative is clearer in this step-by-step product guide.
```

Do not over-explain obvious one-character corrections or list unchanged text as findings.

## Common failure modes

- **Synonym churn:** replacing consistent words only to avoid repetition
- **Meaning inflation:** making benefits, certainty, or authority stronger
- **Meaning erosion:** deleting limitations, conditions, nuance, or technical distinctions
- **Tone drift:** making all copy casual, formal, friendly, or promotional
- **Terminology drift:** replacing approved labels with elegant but inconsistent alternatives
- **Source imitation:** preserving foreign structure because it matches the source closely
- **Over-humanization:** adding idioms, filler, personality, or irregularity to appear less machine-generated
- **Global rewriting:** replacing a sound paragraph to fix one local issue
- **Format damage:** changing tokens, markup, labels, links, or string boundaries
- **Change cascade:** fixing one phrase but leaving broken agreement, references, or punctuation nearby

## Two-pass verification

### Pass 1: Content integrity

Compare the revision against the original, source, glossary, and constraints. Confirm that all semantic invariants and protected elements remain intact.

### Pass 2: Target quality

Read only the revised German as a complete native text. Confirm grammar, idiom, collocations, cohesion, tone, terminology, and formatting without relying on the source to make it understandable.

## Final check

Before returning an edited or rewritten text, verify:

- Each change resolves a supported issue.
- Unchanged text has not been rewritten without need.
- Meaning, facts, uncertainty, conditions, and scope are preserved.
- Terminology, address form, voice, and locale remain consistent.
- Names, numbers, links, markup, placeholders, and required keywords are intact.
- The revision introduces no new claim, error, ambiguity, or formatting defect.
- The final German works as a complete text in its actual channel.
