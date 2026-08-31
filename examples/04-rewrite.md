# Example 4: Justified REWRITE

## Context

- Text type: Explanatory blog paragraph
- Audience: German professionals
- Address form: `du`
- Tone: Neutral-professional
- Required meaning:
  - A tool summarizes meeting transcripts.
  - This can save the user time.
  - The summaries are searchable.
  - The user should still review important decisions.
- Requested task: Review AI-generated German and return a clean, natural version with findings

## Input

```text
Wenn es um die Verbesserung der Produktivität in der heutigen schnelllebigen Arbeitswelt geht, ist es wichtig zu beachten, dass die Nutzung eines Tools für die Zusammenfassung von Meeting-Transkripten eine Lösung darstellt, die es dir ermöglicht, Zeit zu sparen. Darüber hinaus wird es dir durch die Suchfunktion ermöglicht, die Zusammenfassungen zu durchsuchen. Es sollte jedoch im Hinterkopf behalten werden, dass wichtige Entscheidungen weiterhin durch dich überprüft werden sollten.
```

## Expected review

```markdown
Decision: REWRITE

Revised text:
Ein Tool zur Zusammenfassung von Meeting-Transkripten kann dir Zeit sparen. Mit der Suchfunktion durchsuchst du die Zusammenfassungen gezielt. Wichtige Entscheidungen solltest du trotzdem selbst prüfen.

Findings:
- **Recommended · Style and readability**: The paragraph relies on an inflated introduction, repeated enablement formulas, nominalization, and long clause chains. Focused substitutions would not resolve the text-level readability problem.
- **Recommended · Native naturalness**: `wird es dir ... ermöglicht` and `durch dich überprüft werden sollten` are grammatically possible but markedly indirect in this neutral-professional blog context. Direct active formulations are more idiomatic.
```

## What this demonstrates

Pervasive `Recommended` issues can justify `REWRITE` even when no single sentence contains a critical factual error. The revision retains all four required meaning units, preserves `kann` and `solltest`, and does not add claims, examples, or promotional language.
