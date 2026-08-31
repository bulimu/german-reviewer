# German Reviewer Benchmark

This benchmark evaluates editorial judgment rather than exact wording. It tests whether the Skill keeps natural German, makes proportionate edits, preserves meaning and constraints, and explains real issues accurately.

Version: `0.1`

## Evaluation protocol

1. Run each case in a fresh conversation with the current `german-reviewer` Skill loaded.
2. Send only the content under `Test prompt` to the model. Do not reveal the expected behavior or scoring notes.
3. Keep the model, reasoning setting, Skill version, and system environment constant across a comparison run.
4. Save the complete response and record the model, date, and Skill commit.
5. Have a fluent German reviewer score observable behavior. A second reviewer is recommended for borderline naturalness or register judgments.
6. Do not require an exact reference sentence when several German formulations satisfy the same invariants.

For release comparisons, run every case at least twice. A single run is useful for development but does not measure consistency.

## Scoring

Score each dimension from 0 to 2:

| Dimension | 0 | 1 | 2 |
|---|---|---|---|
| Decision and intervention | Wrong decision or disproportionate rewrite | Defensible but over- or under-edited | Correct `KEEP`, `EDIT`, or `REWRITE` scope |
| Issue detection | Misses core issue or invents major issues | Finds core issue with weak classification | Finds real issues with appropriate dimension and severity |
| German quality | Introduces errors or unnatural German | Acceptable with minor weakness | Correct, idiomatic, and context-appropriate |
| Meaning preservation | Changes material meaning | Minor unsupported shift | Preserves all semantic invariants |
| Constraint preservation | Breaks required terms, tokens, locale, or format | Minor avoidable inconsistency | Preserves all supplied constraints |
| Output and reasons | Ignores requested format or gives unsupported reasons | Usable but incomplete | Follows output request and gives concise, evidence-based reasons |

Maximum score: 12 points per case, 192 points total.

### Critical failures

Any of the following fails the benchmark regardless of total score:

- Material meaning, negation, modality, quantity, condition, or product capability is changed.
- A required placeholder, identifier, URL, number, or approved term is lost or altered.
- A clear `Must fix` meaning or correctness issue is missed.
- A natural `KEEP` case is rewritten without a supported problem.
- The response invents facts, source content, legal conclusions, or product claims.

### Recommended release threshold

- No critical failures
- At least 164 of 192 points overall
- At least 8 of 12 points on every case
- Correct intervention decision on at least 15 of 16 cases in each run

Track individual dimensions as well as the total. A higher total should not hide a regression in meaning or constraint preservation.

## Test cases

### B01: Natural product guidance

Purpose: Verify that publishable German is not changed for variation.

#### Test prompt

```text
Use $german-reviewer to review this text.

Context:
- Text type: Product help
- Audience: General users in Germany
- Address: du
- Tone: Neutral-professional

German:
Wenn du deine Auswahl ändern möchtest, öffne das Menü erneut und wähle eine andere Option aus.
```

#### Expected behavior

- Decision: `KEEP`
- No rewritten alternative
- No invented optional issue

### B02: Formal German without translationese

Purpose: Prevent passive voice and formal register from becoming automatic translationese findings.

#### Test prompt

```text
Use $german-reviewer to review this text for translationese and naturalness.

Context:
- Text type: Research report
- Audience: Professional readers
- Tone: Formal
- No source text is available

German:
Im Rahmen der Untersuchung wurden 120 anonymisierte Datensätze ausgewertet. Die Ergebnisse werden im folgenden Abschnitt dargestellt.
```

#### Expected behavior

- Decision: `KEEP`
- Does not flag passive voice, nominal style, or `im Rahmen` without contextual evidence
- Does not claim a source-language error without a source or strong pattern evidence

### B03: Local agreement error

Purpose: Verify a narrow grammar correction.

#### Test prompt

```text
Use $german-reviewer to review this sentence.

German:
Die verfügbaren Optionen wird im nächsten Schritt angezeigt.
```

#### Expected behavior

- Decision: `EDIT`
- Changes `wird` to `werden`
- Classifies the issue as `Must fix · Grammar and syntax`
- Preserves the rest of the sentence

### B04: Non-idiomatic collocation

Purpose: Verify lexical diagnosis without rewriting unaffected content.

#### Test prompt

```text
Use $german-reviewer to review this sentence.

German:
Das Team hat gestern eine Entscheidung gemacht und den nächsten Schritt festgelegt.
```

#### Expected behavior

- Decision: `EDIT`
- Changes `eine Entscheidung gemacht` to `eine Entscheidung getroffen`
- Classifies the core issue as `Must fix · Word choice and collocations`
- Keeps `und den nächsten Schritt festgelegt`

### B05: Source-driven gerund construction

Purpose: Verify a supported translationese finding.

#### Test prompt

```text
Use $german-reviewer for localization QA.

Context:
- Text type: Product settings
- Address: du
- Exact UI label: „Automatisch speichern“

Source:
By selecting Auto-save, you enable automatic backups.

German:
Durch das Auswählen von „Automatisch speichern“ aktivierst du automatische Backups.
```

#### Expected behavior

- Decision: `EDIT`
- Uses a natural construction such as `Wenn du „Automatisch speichern“ auswählst, ...`
- Classifies the issue as `Recommended · Translationese`
- Preserves the exact UI label and the meaning of enablement

### B06: Modality and maximum duration

Purpose: Verify meaning preservation against a source.

#### Test prompt

```text
Use $german-reviewer for localization QA.

Source:
Processing may take up to 24 hours.

German:
Die Verarbeitung dauert 24 Stunden.
```

#### Expected behavior

- Decision: `EDIT`
- Produces wording equivalent to `Die Verarbeitung kann bis zu 24 Stunden dauern.`
- Classifies the issue as `Must fix · Meaning preservation`
- Preserves both possibility and maximum duration

### B07: Mixed address forms

Purpose: Verify `du` consistency across pronouns and verb forms.

#### Test prompt

```text
Use $german-reviewer to review this onboarding copy.

Context:
- Required address: du
- Tone: Friendly and professional

German:
Geben Sie Ihre E-Mail-Adresse ein. Danach kannst du ein Passwort festlegen.
```

#### Expected behavior

- Decision: `EDIT`
- Changes the first sentence to `Gib deine E-Mail-Adresse ein.` or an equivalent `du` formulation
- Classifies the mismatch as `Must fix · Tone and register`
- Keeps the already consistent second sentence

### B08: Approved terminology

Purpose: Prevent synonym variation and unnecessary Germanization.

#### Test prompt

```text
Use $german-reviewer to review this sentence.

Context:
- Approved terms: Workspace, Projekt
- Address: du

German:
Öffne deinen Workspace und wähle das gewünschte Projekt aus.
```

#### Expected behavior

- Decision: `KEEP`
- Preserves `Workspace` and `Projekt`
- Does not replace `Workspace` with `Arbeitsbereich`

### B09: Protected placeholders

Purpose: Verify a local edit without token loss.

#### Test prompt

```text
Use $german-reviewer to review this message.

Protected tokens:
- {{first_name}}
- {{report_url}}

German:
Hallo {{first_name}}, dein Bericht sind bereit. Öffne ihn hier: {{report_url}}
```

#### Expected behavior

- Decision: `EDIT`
- Changes `dein Bericht sind` to `dein Bericht ist`
- Preserves both protected tokens exactly once
- Does not change the URL placeholder or add content

### B10: Clean-copy-only request

Purpose: Verify that the user's output format overrides the default review layout.

#### Test prompt

```text
Use $german-reviewer to correct this sentence. Return only the corrected German text, with no label or explanation.

Die Daten wird jeden Abend gesichert.
```

#### Expected behavior

- Returns only `Die Daten werden jeden Abend gesichert.`
- Does not include `Decision`, `Findings`, commentary, or alternatives

### B11: Ambiguous UI state

Purpose: Prevent silent guessing when a short source string has different translations by function.

#### Test prompt

```text
Use $german-reviewer for localization QA.

Source:
Saving...

German:
Speichern ...

No UI context is available.
```

#### Expected behavior

- States that the correct German depends on whether the string is an action label or progress state
- Distinguishes `Speichern` from a status such as `Wird gespeichert ...`
- Does not silently declare one version universally correct
- Does not invent interface context

### B12: Swiss standard German

Purpose: Verify locale preservation.

#### Test prompt

```text
Use $german-reviewer to review this text.

Context:
- Locale: de-CH
- Address: Sie

German:
Die Datei ist grösser als 10 MB. Sie können sie später schliessen.
```

#### Expected behavior

- Decision: `KEEP`
- Preserves Swiss `ss`
- Does not change `grösser` to `größer` or `schliessen` to `schließen`

### B13: One defect in a sound paragraph

Purpose: Prevent paragraph rewriting for a single local issue.

#### Test prompt

```text
Use $german-reviewer for a full editorial review.

Context:
- Text type: Product documentation
- Address: du

German:
Im Dashboard siehst du alle offenen Aufgaben. Jede Aufgabe enthält einen Titel, eine Frist und den aktuellen Status. Die Statusangaben wird automatisch aktualisiert.
```

#### Expected behavior

- Decision: `EDIT`, not `REWRITE`
- Changes only `wird` to `werden`
- Keeps the first two sentences and all other wording

### B14: Pervasive structure problems

Purpose: Verify a justified rewrite without content drift.

#### Test prompt

```text
Use $german-reviewer to review this AI-generated paragraph.

Context:
- Text type: Product blog
- Audience: German professionals
- Address: neutral
- Required meaning:
  1. Summaries are created automatically.
  2. Teams can find information faster.
  3. Users can filter by speaker.
  4. Users should still verify names.

German:
Die Durchführung der automatischen Erstellung von Zusammenfassungen stellt eine Funktion dar, durch deren Nutzung Teams in die Lage versetzt werden, Informationen schneller zu finden. Darüber hinaus wird eine Filterung nach Sprecher ermöglicht. Es sollte beachtet werden, dass Namen weiterhin einer Überprüfung durch die Nutzer unterzogen werden sollten.
```

#### Expected behavior

- Decision: `REWRITE`
- Produces substantially more direct, idiomatic German
- Preserves all four required meaning units
- Preserves capability and recommendation rather than turning them into guarantees or obligations
- Adds no claim, example, address form, or promotional language

### B15: Watchlist phrase without a defect

Purpose: Prevent phrase-list editing.

#### Test prompt

```text
Use $german-reviewer to review this sentence for AI style and translationese.

Context:
- Text type: Neutral-professional product article
- Address: du

German:
Darüber hinaus kannst du den Bericht als PDF exportieren.
```

#### Expected behavior

- Decision: `KEEP`
- Does not flag `Darüber hinaus` merely because it is common in translated or AI-generated prose
- Does not offer synonym variation without a contextual problem

### B16: High-stakes scope boundary

Purpose: Keep linguistic review separate from legal interpretation.

#### Test prompt

```text
Use $german-reviewer for linguistic review only. Do not provide legal advice.

Context:
- Text type: Contract clause
- Tone: Formal
- No authoritative source text is available

German:
Die Kündigung muss spätestens 30 Tage vor Ablauf der Vertragslaufzeit schriftlich eingehen.
```

#### Expected behavior

- Decision: `KEEP`
- Preserves `muss`, the 30-day condition, and the formal register
- Does not speculate about legal validity or reinterpret the clause

## Result record

Use this table for each run:

| Field | Value |
|---|---|
| Date | |
| Model and reasoning setting | |
| Skill commit | |
| Run number | |
| Total score | /192 |
| Critical failures | |
| Cases below 8/12 | |
| Wrong intervention decisions | |
| Reviewer notes | |

Record per-case dimension scores separately so regressions can be traced to a specific behavior.
