# SIE01: Required Sie address with a mixed-form defect

Status: `PASS`

This case was created after the original benchmark run and does not appear in the benchmark or example files.

## Run metadata

- Date: 2026-08-30
- Skill version: `0.1.0`
- Model and reasoning: Codex configured defaults, not pinned
- Fresh task: `01a05161-9313-7c51-b59e-2ec7ef610402`

## Test prompt

```text
Use $german-native-editor to review this text.

Context:
- Text type: Customer support email
- Audience: Business customers in Germany
- Required address: Sie
- Tone: Friendly and professional
- Exact UI label: „Benachrichtigungen“

German:
Bitte öffnen Sie die Einstellungen und wählen Sie „Benachrichtigungen“ aus. Dort kannst du festlegen, welche Meldungen Sie erhalten möchten.
```

## Raw final response

```text
Decision: EDIT

Revised text:  
Bitte öffnen Sie die Einstellungen und wählen Sie „Benachrichtigungen“ aus. Dort können Sie festlegen, welche Meldungen Sie erhalten möchten.

Findings:

- **Must fix · Tone and register**: `kannst du` → `können Sie`. Die Anrede wechselt unzulässig von „Sie“ zu „du“. Die UI-Bezeichnung „Benachrichtigungen“ bleibt unverändert.
```

## Expected behavior

- Decision: `EDIT`
- Changes only `kannst du` to `können Sie`
- Classifies the mixed address as `Must fix · Tone and register`
- Preserves the first sentence and the exact UI label `„Benachrichtigungen“`

## Provisional scoring

| Dimension | Score |
|---|---:|
| Decision and intervention | 2/2 |
| Issue detection | 2/2 |
| German quality | 2/2 |
| Meaning preservation | 2/2 |
| Constraint preservation | 2/2 |
| Output and reasons | 2/2 |
| **Total** | **12/12** |

Critical failures: none.

Reviewer: AI-assisted provisional evaluation.
