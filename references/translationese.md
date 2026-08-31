# Translationese Review Guide

Use this guide when a source text is available, the user requests a translationese check, or the German shows plausible source-language interference.

The examples use English sources because this is a common localization direction. The diagnostic method applies to interference from any source language.

## Operational definition

Translationese is source-language transfer that makes the German less idiomatic, clear, accurate, or appropriate for its context. The transfer can affect syntax, information order, collocations, discourse structure, pragmatics, or localization conventions.

Translationese is not a synonym for:

- Formal German
- Long sentences
- Passive voice
- Technical terminology
- Anglicisms
- AI-generated prose
- Any wording that resembles the source

A source-aligned translation can be completely natural. Flag translationese only when the transfer produces an observable problem in German.

## Evidence levels

### Strong evidence

- The source and target are available, and the target follows a source structure that creates awkward or incorrect German.
- A literal calque or transferred idiom is not idiomatic in the target context.
- The same source-driven pattern recurs across the passage and affects readability or register.
- Source punctuation, capitalization, labels, or UI states have been copied without German localization.

### Moderate evidence

- The source is unavailable, but several related features form a consistent source-language pattern.
- The German has foreign information order or clause architecture that is difficult to explain as an ordinary native stylistic choice.

Use the label cautiously and explain the observable German problem rather than guessing the exact source wording.

### Weak evidence

- A single word appears on an AI-writing or translationese watchlist.
- The sentence is passive, nominal, formal, long, or repetitive.
- A common Anglicism appears in a technical or business context.
- Another version sounds better to the editor, but the original is idiomatic.

Weak evidence alone does not justify a translationese finding.

## Diagnostic workflow

1. Establish the source meaning, target audience, text type, register, and protected terminology.
2. Read the complete German passage before comparing individual sentences.
3. Ask how a native German writer would express the same function in this context without looking at the source syntax.
4. Compare that formulation with the target and identify the specific transferred feature.
5. Check whether the feature is accepted or useful in the target genre.
6. Make the smallest change that removes the interference while preserving meaning and constraints.
7. Compare the revision with the source again, especially for modality, scope, negation, quantities, and claims.

Do not detach the German so far from the source that the revision becomes creative rewriting.

## Choose the most specific issue label

Source-language influence can cause several types of defect. Label the primary defect, not its historical cause, unless translationese itself best explains the pattern.

| Main observation | Primary dimension |
|---|---|
| Wrong agreement, case, word order, or required punctuation | Grammar and syntax |
| Wrong word, false friend, or non-idiomatic collocation | Word choice and collocations |
| Added, omitted, weakened, or strengthened meaning | Meaning preservation |
| Awkward German with no credible source evidence | Native naturalness |
| Heavy or repetitive prose without a source-specific pattern | Style and readability |
| Source-driven structure or discourse pattern that remains recognizably foreign | Translationese |

For example, `eine Entscheidung machen` may come from English `make a decision`, but the actionable defect is the German collocation. Classify it primarily as `Word choice and collocations`.

## Pattern library

Treat these patterns as diagnostic prompts, not automatic errors.

### 1. Source-driven clause architecture

English often packages relationships in participial phrases, gerunds, repeated subject-first clauses, or abstract `this` constructions. A literal structural match can make German unnecessarily nominal or indirect.

Context: direct product guidance.

```text
Source: By clicking Continue, you confirm that you have read the terms.
Literal: Durch das Klicken auf „Weiter“ bestätigst du, dass du die Bedingungen gelesen hast.
Idiomatic: Wenn du auf „Weiter“ klickst, bestätigst du, dass du die Bedingungen gelesen hast.
```

`Durch das Klicken` is understandable, but the finite conditional clause is more natural in this context. In another context, `Mit einem Klick auf ...` may be the better minimal solution.

Do not automatically replace every nominal phrase with a subordinate clause. German uses nominal structures naturally, especially in formal and technical writing.

### 2. Literal enablement and capability formulas

Source texts frequently use `allows`, `enables`, `makes it possible`, and `is able to`. German has direct equivalents, but repeated literal mapping often creates remote or mechanical prose.

```text
Source: This makes it possible for teams to share results faster.
Literal: Dies macht es für Teams möglich, Ergebnisse schneller zu teilen.
Idiomatic: So können Teams Ergebnisse schneller teilen.
```

The literal version is grammatically possible. Mark it only when the direct formulation better fits the text's tone and preserves the same emphasis. `ermöglichen` and `in der Lage sein` are not banned.

### 3. Source-language valency and complements

A source verb may invite a complement that its apparent German equivalent does not take in the same way.

```text
Source: Make sure to save your changes.
Literal: Stelle sicher, deine Änderungen zu speichern.
Idiomatic: Achte darauf, deine Änderungen zu speichern.
```

`Stelle sicher, dass du deine Änderungen speicherst` can also be idiomatic when actual verification or certainty is meant. Choose according to function, not by replacing `make sure` mechanically.

### 4. Modifier stacks and noun chains

English can place several nouns and modifiers before a head noun. Copying their order into German compounds or hyphen chains can obscure the relationship between concepts.

```text
Source: team meeting recording settings
Literal: Team-Meeting-Aufnahmeeinstellungen
Idiomatic: Aufnahmeeinstellungen für Teammeetings
```

German compounds are not translationese by themselves. Unpack the chain only when the compound is hard to parse, ambiguous, or inconsistent with established terminology.

### 5. Unnecessary possessives and repeated subjects

English often marks possession where German can rely on context. Literal repetition can make UI and help copy sound heavier than necessary.

```text
Source: Open your settings and change your language.
Literal: Öffne deine Einstellungen und ändere deine Sprache.
Idiomatic: Öffne die Einstellungen und ändere die Sprache.
```

Keep the possessive when it distinguishes the user's data from another person's data or has a real contrastive function.

### 6. Copied discourse markers

Sentence-by-sentence translation can reproduce every `additionally`, `furthermore`, `however`, and `therefore`. The individual German connectors may be correct while the passage as a whole sounds mechanical.

Check whether the logical relationship is already clear. Depending on the passage, vary the connector, move it, combine sentences, or omit it. Never remove a connector when doing so changes contrast, consequence, or argumentative structure.

Words such as `außerdem`, `darüber hinaus`, `allerdings`, and `daher` are not warning signs on their own.

### 7. Copied metadiscourse

Source prose may announce information instead of stating it directly. Literal transfer is common in introductions, help content, and AI-generated drafts.

Context: a concise help article.

```text
Source: It is important to note that recordings are deleted after 30 days.
Literal: Es ist wichtig zu beachten, dass Aufnahmen nach 30 Tagen gelöscht werden.
Idiomatic: Beachte: Aufnahmen werden nach 30 Tagen gelöscht.
```

The emphasis may be meaningful. Do not reduce it to a neutral statement if the source marks a warning, risk, or legal consequence.

### 8. Literal idioms and marketing metaphors

An image that works in the source language can become a calque, a cliché, or an unintended claim in German.

```text
Source: Take your productivity to the next level.
Literal: Bringe deine Produktivität auf die nächste Stufe.
Contextual alternative: Arbeite produktiver.
```

The literal version is widespread in German marketing and may be acceptable for that brand voice. Treat it as `Recommended` only when the context calls for more direct, less promotional language. Familiarity does not make every calque wrong, and source origin alone is not a defect.

### 9. Source-shaped information order

German information structure may place known context, contrast, time, condition, or the most useful action differently from the source. A clause-by-clause translation can be grammatical but hard to follow.

Review what each sentence treats as given and new information. Move elements only when the new order improves comprehension or emphasis for the target reader. Do not apply a universal rule such as always placing time before place or always starting with the subject.

### 10. Over-explicit repetition

A source may repeat product names, full noun phrases, or instructions for clarity. German may prefer a pronoun, an ellipsis, a compound, or a merged sentence. However, repetition can be required for accessibility, legal precision, search visibility, or standalone UI strings.

Remove repetition only when the referent remains unambiguous and no external constraint requires it.

### 11. UI states translated as ordinary sentences

Short source strings are often ambiguous without interface context. Translate their function, not only their words.

```text
Source: Saving...
Action label: Speichern
Progress state: Wird gespeichert ...
```

Do not decide between these versions without knowing whether the string is a button, menu command, status message, or accessibility label. When context is missing and the choice affects meaning, state the ambiguity rather than guessing silently.

### 12. Source capitalization and punctuation

Copied English title case, quotation marks, spacing, number formats, or sentence fragments can reveal incomplete localization. Classify the concrete defect under `Grammar and syntax`, `Style and readability`, or the applicable localization convention. Use `Translationese` for a repeated source-formatting pattern, not for a single capitalization error.

## Common false positives

Do not flag the following without contextual evidence:

- `um ... zu`, `sowohl ... als auch`, or other structures that are fully native German
- Passive voice in processes, research, legal text, or situations where the actor is irrelevant
- Nominalization in headings, labels, formal documents, or terminology
- Established Anglicisms such as `Meeting`, `Software`, or `Feedback` when they fit the audience and glossary
- Repeated product terms required for consistency
- A German sentence that mirrors the source but remains idiomatic
- Phrases such as `darüber hinaus`, `im Hinblick auf`, `in der Lage sein`, `nahtlos`, or `robust` based only on their frequency in AI or translated prose

A watchlist can prompt a closer look. It cannot make the decision.

## Translationese versus AI-style prose

AI-generated German can contain generic openings, inflated claims, empty transitions, symmetrical lists, repetitive conclusions, and unnecessary summaries. These features may occur without any source text.

Use `Translationese` only when source-language transfer is supported. Otherwise classify the concrete problem as `Style and readability`, `Tone and register`, `Native naturalness`, or no issue. Do not use translationese as a broad label for prose that merely feels artificial.

## Correction strategies

- Translate the communicative function, not the surface structure.
- Rebuild clause architecture when the source order obstructs natural German.
- Use German valency and established collocations.
- Turn modifier stacks into clear compounds, prepositional phrases, or clauses as appropriate.
- Remove source-explicit pronouns, connectors, or repetitions only when meaning and cohesion remain intact.
- Adapt UI strings to their actual function and state.
- Keep claims, modality, scope, quantities, terminology, markup, and placeholders unchanged.
- Preserve deliberate source emphasis when it matters to safety, legality, persuasion, or task completion.

Avoid overcorrection. Do not add idioms, colloquialisms, promotional energy, or stylistic variation that the target context does not require.

## Writing a useful finding

Weak reason:

```text
Sounds translated.
```

Useful reason:

```text
The target copies the English gerund structure as „durch das Klicken“. A finite wenn-clause is more idiomatic in this direct instruction and preserves the condition.
```

A useful translationese finding identifies:

1. The transferred source feature
2. Its observable effect in German
3. Why the suggestion fits the target context
4. Any meaning or terminology constraint that must remain

## Final check

Before confirming a translationese edit, ask:

- Is there real evidence of source-language interference?
- Would the original still sound natural if no source text existed?
- Does a more specific review dimension describe the defect better?
- Does the revision preserve meaning, emphasis, register, and structural tokens?
- Did the edit remove an actual problem rather than only make the wording different?
