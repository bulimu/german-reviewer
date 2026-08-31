# Example 3: Source-based localization QA

## Context

- Text type: Confirmation dialog
- Audience: General users in Germany
- Address form: `du`
- Tone: Neutral-professional
- Source note: `may` expresses possibility, not permission
- Protected token: `{{ticket_id}}`
- Requested task: Compare the German with the English source and review localization quality

## Source

```text
By clicking Continue, you confirm that the app may delete recordings older than 30 days. Your files remain available to administrators.
Reference: {{ticket_id}}
```

## German target

```text
Durch das Klicken auf „Weiter“ bestätigen Sie, dass die App Aufnahmen, die älter als 30 Tage sind, löscht. Deine Dateien bleiben für Administratoren verfügbar.
Referenz: {{ticket_id}}
```

## Expected review

```markdown
Decision: EDIT

Revised text:
Wenn du auf „Weiter“ klickst, bestätigst du, dass die App mehr als 30 Tage alte Aufnahmen löschen kann. Deine Dateien bleiben für Administratoren verfügbar.
Referenz: {{ticket_id}}

Findings:
- **Must fix · Meaning preservation**: `löscht` -> `löschen kann`. The target turns a stated possibility into a definite action.
- **Must fix · Tone and register**: `bestätigen Sie` -> `bestätigst du`. The brief requires `du`, and the target mixes formal and informal address.
- **Recommended · Translationese**: `Durch das Klicken auf „Weiter“` -> `Wenn du auf „Weiter“ klickst`. The target copies the English gerund structure; the finite conditional clause is more idiomatic in this dialog.
```

## What this demonstrates

The source determines meaning but not German syntax. The edit restores modality, fixes the address system, removes a source-driven construction, and preserves `{{ticket_id}}` exactly once. The already natural second sentence remains unchanged.
