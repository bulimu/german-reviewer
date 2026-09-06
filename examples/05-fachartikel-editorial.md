# Example 5: Fachartikel Editorial Review

All companies, products, capabilities, and constraints in this example are fictional.

## Context

- Text type: B2B SaaS `Fachartikel`
- Audience: Team leads and operations professionals in Germany
- Address form: Neutral where direct address is unnecessary
- Tone: Editorial, clear, reader-oriented
- Review depth: Redakteur-level editorial rewrite
- Supported brief:
  - FlowBoard groups open tasks by project.
  - It shows dependencies between tasks.
  - Teams can use it to coordinate several projects.
  - Required integrations and access controls affect product fit.
  - The existing CTA should lead to an overview of functions and integrations.
- Requested task: Review the paragraph as a Fachartikel passage and return a clean revision with findings

## Input

```text
In der heutigen dynamischen Geschäftswelt brauchen Unternehmen effiziente Lösungen für ihre Projektarbeit. FlowBoard ist eine großartige und innovative Lösung für jedes Unternehmen. Mit FlowBoard können Sie Aufgaben nach Projekten gruppieren. Mit FlowBoard können Sie Abhängigkeiten anzeigen. Mit FlowBoard können Sie mehrere Projekte koordinieren. Entdecken Sie jetzt die großartigen Möglichkeiten von FlowBoard!
```

## Expected review

```markdown
Decision: REWRITE

Revised text:
FlowBoard bündelt offene Aufgaben nach Projekten und macht Abhängigkeiten sichtbar. Das ist vor allem für Teams relevant, die mehrere Vorhaben parallel koordinieren. Ob die Plattform zum vorhandenen Arbeitsablauf passt, hängt unter anderem von den benötigten Integrationen und Zugriffsrechten ab.

Funktionen und Integrationen im Überblick

Findings:
- **Must fix · Meaning preservation**: `für jedes Unternehmen` -> a use-case-based assessment. The brief does not support universal suitability.
- **Recommended · Tone and register**: `großartige und innovative Lösung` presents unsupported praise as editorial judgment. The revision explains relevance through the supplied use case instead.
- **Recommended · Style and readability**: Three consecutive `Mit FlowBoard können Sie ...` sentences create a mechanical pattern. Combining the supported functions produces a coherent Fachartikel paragraph without varying the product term arbitrarily.
- **Recommended · Tone and register**: `Entdecken Sie jetzt die großartigen Möglichkeiten ...!` does not match the supplied destination. The revised CTA names the information readers will find next.
```

## Additional KEEP calibration: supported reader promise

### Context

- Text type: SaaS hosting comparison
- Address form: `Sie`
- The article compares the available tariffs using criteria relevant to the reader and explains which tariff fits different project requirements.

### Input

```text
Nach diesem Vergleich wissen Sie, welcher Hosting-Tarif zu den Anforderungen Ihres Projekts passt.
```

### Expected review

```markdown
Decision: KEEP

No changes needed.
```

The definite reader promise is natural and supported in this context. Replacing it with a more hesitant formulation would weaken the promise without correcting a defect.

## What this demonstrates

Redakteur-level editing is not a synonym substitution or automatic tone-reduction exercise. It can rebuild a weak paragraph around product function, use-case relevance, fit criteria, and an accurate next step. At the same time, a supported confident promise remains unchanged. The review depth permits structural work but does not authorize invented facts or a different conversion goal.
