# Example 2: Focused EDIT

## Context

- Text type: Product help article
- Audience: General users in Germany
- Address form: `du`
- Tone: Neutral-professional and direct
- Requested task: Full editorial review

## Input

```text
Mit dieser Funktion bist du in der Lage, deine Notizen schneller zu organisieren. Zusätzlich kannst du damit Entscheidungen machen. Die Änderungen wird automatisch gespeichert.
```

## Expected review

```markdown
Decision: EDIT

Revised text:
Mit dieser Funktion kannst du deine Notizen schneller organisieren. Zusätzlich kannst du damit Entscheidungen treffen. Die Änderungen werden automatisch gespeichert.

Findings:
- **Recommended · Style and readability**: `bist du in der Lage, deine Notizen schneller zu organisieren` -> `kannst du deine Notizen schneller organisieren`. The direct modal construction is clearer in a product guide and preserves the meaning.
- **Must fix · Word choice and collocations**: `Entscheidungen machen` -> `Entscheidungen treffen`. German uses `eine Entscheidung treffen` as the idiomatic collocation.
- **Must fix · Grammar and syntax**: `Die Änderungen wird` -> `Die Änderungen werden`. The plural subject requires the plural verb form.
```

## What this demonstrates

The three issues are local. The paragraph's structure and voice still work, so `EDIT` is sufficient. `Zusätzlich` and all unaffected wording remain unchanged even though other formulations would be possible.
