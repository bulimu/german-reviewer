# Review Rubric

Use this rubric for a full German editorial review or localization QA pass. It turns the seven review dimensions into consistent editorial decisions.

Examples in this document illustrate judgments in a stated context. They are not universal replacement rules. The same wording can be appropriate in another genre, audience, or register.

## Evidence threshold

A different formulation is not automatically a better formulation. Record an issue only when all of the following are true:

1. The original has an identifiable problem in its actual context.
2. The problem belongs to one of the seven review dimensions.
3. The suggested change resolves that problem without changing the intended meaning or violating a constraint.

Prefer no finding when the evidence supports only personal taste. Do not create an issue merely because a sentence could be shorter, more varied, or phrased with different synonyms.

Assign one primary dimension to each issue. Mention a secondary effect in the reason only when it helps the user understand the problem. Do not duplicate one observation across several dimensions to make the review appear more comprehensive.

## Review order

Review in this order when dimensions compete:

1. User instructions, approved terminology, and structural constraints
2. Meaning preservation against the source or brief
3. Grammar and syntax
4. Word choice, collocations, and idiomatic naturalness
5. Translationese
6. Tone, register, style, and readability

This order resolves conflicts. It does not mean that later dimensions are unimportant. For example, a consistent `du` or `Sie` requirement can be a `Must fix` even though tone and register appear later in the sequence.

## Dimension rubric

### 1. Native naturalness

**Governing question:** Would a proficient native German writer be likely to use this wording in this context without the sentence feeling translated, marked, or unintentionally awkward?

Flag this dimension when the text is formally possible but its information flow, pragmatic emphasis, or overall formulation sounds unnatural. Use it when no more specific grammar, collocation, translationese, or register label explains the main problem.

Do not flag a sentence solely because it is uncommon, specialized, formal, or not the editor's preferred wording. A technical term or deliberate stylistic choice can still be natural in its genre.

Typical severity:

- `Recommended` for clearly awkward but understandable wording
- `Must fix` only when the phrasing is so unidiomatic that comprehension or credibility is materially affected
- `Optional` when the original is natural and the suggestion only changes cadence

Context: a direct product guide using `du`.

```text
Original: Im Folgenden wird ein Blick darauf geworfen, wie die Funktion verwendet werden kann.
Suggested: Im Folgenden zeigen wir dir, wie du die Funktion verwendest.
Judgment: Recommended · Native naturalness
```

The original may be acceptable in a deliberately impersonal report. The context makes the difference.

### 2. Translationese

**Governing question:** Does the German reproduce source-language wording or structure in a way that a native German text would normally avoid?

Flag translationese only when there is positive evidence of source-language interference. Useful evidence includes a source text, a recognizable calque, foreign information order, repeated literal constructions, or a pattern that becomes awkward across several sentences.

Do not reverse-engineer an English source from any polished corporate phrase. Many structures exist naturally in both languages. If no source is available and the only evidence is general awkwardness, prefer `Native naturalness`, `Word choice and collocations`, or `Style and readability`.

Typical severity:

- `Recommended` when the result is clear but noticeably source-bound
- `Must fix` when the literal transfer creates an error, ambiguity, or wrong meaning
- `Optional` only when both source-oriented and idiomatic versions are acceptable

Context: English source text says "Make sure to save your changes."

```text
Original: Stelle sicher, deine Änderungen zu speichern.
Suggested: Achte darauf, deine Änderungen zu speichern.
Judgment: Recommended · Translationese
```

### 3. Grammar and syntax

**Governing question:** Is the sentence structurally correct according to standard German usage in the target locale?

Check agreement, case, verb forms, word order, clause structure, articles, prepositions, negation, punctuation, capitalization, and spelling. Use this dimension for rule-based correctness, not for a sentence that is grammatical but stylistically heavy.

Typical severity:

- `Must fix` for a demonstrable error
- `Recommended` for a defensible construction that creates avoidable parsing difficulty
- `Optional` only where accepted conventions allow more than one form

```text
Original: Die Daten wird automatisch gelöscht.
Suggested: Die Daten werden automatisch gelöscht.
Judgment: Must fix · Grammar and syntax
```

### 4. Word choice and collocations

**Governing question:** Are individual words precise, and do they combine in the way German speakers normally combine them?

Flag false friends, wrong semantic selection, non-idiomatic verb-noun pairs, unsuitable prepositions, ambiguous references, or terminology that conflicts with the supplied glossary. Prefer this dimension over native naturalness when a specific lexical choice or combination is the cause.

Do not replace established technical terms or common Anglicisms simply because a German alternative exists. Do not vary approved terminology for stylistic variety.

Typical severity:

- `Must fix` when the word or collocation is wrong or misleading
- `Recommended` when it is understandable but noticeably non-idiomatic or imprecise
- `Optional` when two choices are equally accurate and conventional

```text
Original: Du kannst damit viel Zeit einsparen und eine bessere Entscheidung machen.
Suggested: Du kannst damit viel Zeit sparen und eine bessere Entscheidung treffen.
Judgment: Must fix · Word choice and collocations
```

### 5. Style and readability

**Governing question:** Can the intended audience understand the text efficiently, and does the structure serve the genre?

Check excessive nominalization, avoidable repetition, overloaded sentences, unclear references, weak paragraph flow, monotonous sentence patterns, and information that arrives in an unhelpful order. Evaluate the passage as a whole, not only sentence by sentence.

Do not assume that shorter is always better. Legal, academic, technical, and accessibility contexts can require repetition, precision, or explicit structure. Do not remove useful detail merely to make the text sound lighter.

Typical severity:

- `Recommended` for clear but needlessly difficult or mechanical prose
- `Must fix` when structure blocks comprehension or task completion
- `Optional` for minor rhythm or concision preferences

Context: a short product help article.

```text
Original: Die Durchführung der Konfiguration der Einstellungen erfolgt über das Menü.
Suggested: Du konfigurierst die Einstellungen im Menü.
Judgment: Recommended · Style and readability
```

### 6. Tone and register

**Governing question:** Does the language fit the audience, relationship, channel, and requested level of formality?

Check `du` and `Sie`, imperative forms, politeness, emotional intensity, promotional pressure, professional distance, and consistency across the text. Treat an explicit style guide as evidence, not as a suggestion.

Do not impose a friendly, informal, formal, gender-inclusive, or sales-oriented style without contextual support. If the user gives no preference, preserve a consistent existing register unless it clearly conflicts with the text type.

Typical severity:

- `Must fix` for an explicit brief violation or a disruptive register switch
- `Recommended` for a consistent but poorly matched tone
- `Optional` when both registers are suitable and the choice is editorial

Context: the surrounding UI consistently addresses the user with `du`.

```text
Original: Klicken Sie auf Speichern.
Suggested: Klicke auf Speichern.
Judgment: Must fix · Tone and register
```

### 7. Meaning preservation

**Governing question:** Does the German preserve the source or brief without adding, omitting, weakening, strengthening, or reinterpreting information?

Compare actors, actions, objects, conditions, negation, modality, quantity, time, causality, scope, and degree of certainty. Pay particular attention to words such as `may`, `must`, `usually`, `only`, and `up to`, as well as numbers, dates, and product capabilities.

When no source or authoritative brief is available, do not claim a source mismatch. You may flag an internal contradiction or ambiguity under the most appropriate other dimension and state the uncertainty.

Typical severity:

- `Must fix` for a supported meaning mismatch
- `Recommended` only when the meaning is technically recoverable but the German creates avoidable ambiguity
- `Optional` does not normally apply to meaning preservation

Context: the source says "The setting may delete older recordings."

```text
Original: Die Einstellung löscht ältere Aufnahmen.
Suggested: Die Einstellung kann ältere Aufnahmen löschen.
Judgment: Must fix · Meaning preservation
```

## Severity calibration

### Must fix

Use `Must fix` when publication without the change would leave a demonstrable correctness, meaning, idiom, terminology, or explicit-context problem. The finding should be supportable without relying mainly on personal preference.

Typical cases include:

- Grammar or spelling errors
- Wrong meaning, omission, addition, polarity, or modality
- Incorrect or misleading word choice
- Clearly non-idiomatic collocations
- Violation of an explicit glossary, address form, character limit, or protected token
- Wording that prevents the reader from understanding or completing the intended task

### Recommended

Use `Recommended` when the text is understandable and not strictly wrong, but a native editor would normally improve it for the stated context. The reason must identify a concrete benefit such as more idiomatic wording, clearer information flow, or better register alignment.

Typical cases include:

- Noticeable translationese
- Grammatically correct but markedly awkward phrasing
- Excessive nominalization or sentence load
- Mild register mismatch
- Repetition or organization that impairs the reading experience

### Optional

Use `Optional` only when the original is already publishable and the suggestion reflects a legitimate preference. Explicitly state that the original can remain.

Do not fill a review with optional variants unless the user asks for alternatives. Several optional suggestions do not turn a passage into `EDIT` or `REWRITE`.

When uncertain between `Recommended` and `Optional`, ask: Would a competent native editor consider the original professionally weak in this context, or merely different from their own preference? If it is merely different, choose `Optional` or record no issue.

## Choosing KEEP, EDIT, or REWRITE

Choose the intervention independently from severity. A `Must fix` can require only a one-word `EDIT`, while pervasive `Recommended` issues can justify a `REWRITE`.

### KEEP

Choose `KEEP` when the text is correct, idiomatic, context-appropriate, and faithful to the available source or brief. A possible alternative is not a reason to edit. If only optional preferences exist and the user did not request variants, keep the text.

### EDIT

Choose `EDIT` when the text's structure and voice work, and each real issue can be resolved with focused changes. Preserve all unaffected wording.

### REWRITE

Choose `REWRITE` only when local edits would leave the text substantially source-bound, incoherent, misleading, or unsuitable for its purpose. Preserve usable wording where practical and verify the rewrite against the source or brief.

Do not choose by counting issues. Consider their distribution and whether the original structure can support a natural correction.

## Calibration cases

| Observation | Severity | Intervention | Reason |
|---|---|---|---|
| A natural sentence has an equally natural synonym | No issue or Optional | KEEP | Difference without a defect |
| One verb has the wrong agreement | Must fix | EDIT | Local correctness error |
| A literal construction is clear but repeatedly sounds source-bound | Recommended | EDIT or REWRITE | Depends on how widely the pattern affects the text |
| The German strengthens `may` to a definite claim | Must fix | EDIT | Meaning mismatch, unless the problem is pervasive |
| A long text consistently uses the wrong register for its audience | Recommended or Must fix | REWRITE may be justified | Severity depends on whether the register was explicitly required |

## Issue-quality check

Before recording an issue, confirm:

- The context supports the judgment.
- The primary dimension identifies the cause, not merely a symptom.
- The severity matches the evidence.
- The suggestion is the smallest effective correction.
- The correction introduces no new meaning, terminology, grammar, tone, or formatting problem.
