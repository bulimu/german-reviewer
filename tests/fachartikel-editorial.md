# Fachartikel Editorial Behavioral Tests

This suite evaluates the optional Fachartikel editorial profile separately from the core language benchmark. It focuses on German professional-editor judgment for B2B/SaaS articles, content marketing, product comparisons, industry guides, and editorial calls to action.

All companies, products, capabilities, metrics, and constraints in this suite are fictional. Run every case in a fresh conversation with the current German Reviewer Skill loaded. Exact wording is not required; the decisions, preservation constraints, and editorial behaviors are.

Version: `0.4`

## F01: Keep a natural analytical passage

### Test prompt

```text
Use $german-reviewer to review this German Fachartikel passage.

Context:
- Audience: Sales and operations professionals in Germany
- Address: neutral
- Tone: precise, analytical, neutral-professional

German:
Für die Auswahl einer CRM-Plattform sind vor allem die benötigten Integrationen, die Rollenverteilung und die bestehenden Vertriebsprozesse relevant. Welche Lösung passt, hängt daher vom jeweiligen Nutzungsszenario ab.
```

### Expected behavior

- Decision: `KEEP`
- Preserves the conditional assessment and neutral address
- Does not make the passage more promotional, conversational, or academic
- Does not offer synonym variants merely to demonstrate editorial activity

## F02: Replace empty praise with supported relevance

### Test prompt

```text
Use $german-reviewer to review this paragraph as a B2B SaaS Fachartikel.

Supported brief:
- PlanDesk groups open tasks by project.
- The view is intended for teams coordinating several projects.
- No comparative market claim is supported.

German:
PlanDesk ist eine großartige und führende Lösung für moderne Unternehmen. Das Tool bietet eine übersichtliche Ansicht offener Aufgaben.
```

### Expected behavior

- Decision: `EDIT` or `REWRITE`, proportionate to the final structure
- Removes or qualifies `großartige und führende` because the supplied brief does not support the evaluation or market position
- Connects the supplied function to teams coordinating several projects when doing so improves the passage
- Does not replace the praise with an equally empty phrase such as `interessante Option`
- Adds no unsupported benefit, customer type, statistic, or comparison

## F03: Resolve repeated sentence architecture

### Test prompt

```text
Use $german-reviewer for a full Fachartikel editorial review.

Context:
- Audience: German business users
- Address: Sie
- Preserve all four capabilities

German:
Mit TeamPilot können Sie Aufgaben priorisieren. Mit TeamPilot können Sie Abhängigkeiten abbilden. Mit TeamPilot können Sie Statusberichte erstellen. Mit TeamPilot können Sie Berichte exportieren.
```

### Expected behavior

- Decision: `REWRITE`
- Resolves the pervasive `Mit TeamPilot können Sie ...` pattern at passage level
- Preserves all four capabilities and the required `Sie` system
- Keeps the product name consistent without inventing synonyms for it
- Does not add a benefit, limitation, CTA, or product claim

## F04: Preserve necessary terminology repetition

### Test prompt

```text
Use $german-reviewer to review this technical Fachartikel passage.

Context:
- Approved product term: Workspace
- Workspace and Projekt are different product concepts.
- Address: neutral

German:
Für jeden Workspace gelten eigene Rollen und Berechtigungen. Ein Workspace kann mehrere Projekte enthalten. Einstellungen werden nicht automatisch von einem Workspace auf einen anderen übertragen.
```

### Expected behavior

- Decision: `KEEP`
- Preserves every use of the approved term `Workspace`
- Does not alternate among `Arbeitsbereich`, `Konto`, `Profil`, or another synonym to create variety
- Recognizes that the repetition protects a technical distinction and reference clarity

## F05: Preserve source modality and scope

### Test prompt

```text
Use $german-reviewer for source-based Fachartikel QA.

Source:
For some teams, automated status reports can reduce the manual work required in project tracking.

German:
Automatisierte Statusberichte reduzieren den manuellen Aufwand in der Projektverfolgung für alle Teams.
```

### Expected behavior

- Decision: `EDIT`
- Restores both `can` and `for some teams`
- Classifies the mismatch as `Must fix · Meaning preservation`
- Does not strengthen the source into a guarantee or universal recommendation
- Produces idiomatic German suitable for a Fachartikel

## F06: Calibrate a Fachartikel CTA to its actual destination

### Test prompt

```text
Use $german-reviewer to review this CTA at the end of an informational Fachartikel.

Context:
- The link opens an overview of functions and integrations.
- It does not start a trial or create an account.
- Address: Sie

German CTA:
Starten Sie jetzt sofort kostenlos und revolutionieren Sie Ihre Projektarbeit!
```

### Expected behavior

- Decision: `EDIT`
- Replaces the false trial implication with a CTA that accurately describes the function-and-integration overview
- Removes unsupported urgency and the sweeping benefit promise
- Preserves a clear next step without adding a different conversion goal
- Does not assume that every Fachartikel CTA must be a generic `Mehr erfahren`

## F07: Preserve an approved campaign element

### Test prompt

```text
Use $german-reviewer to review this sponsored box embedded in a Fachartikel.

Context:
- The exact CTA `Jetzt 50 % sparen!` is approved campaign copy.
- The 50 % offer is verified in the supplied campaign brief.
- Preserve the CTA exactly.

German:
Aktionsangebot: Jetzt 50 % sparen!
```

### Expected behavior

- Decision: `KEEP`
- Preserves `Jetzt 50 % sparen!` exactly
- Does not weaken the CTA merely because the surrounding article uses an analytical tone
- Recognizes the explicit campaign boundary and supported offer

## F08: Do not introduce direct address into neutral Fachartikel prose

### Test prompt

```text
Use $german-reviewer to review this German Fachartikel passage. No address form has been specified.

German:
Bei der Auswahl sind neben dem Funktionsumfang auch bestehende Arbeitsabläufe und Zugriffsanforderungen zu berücksichtigen.
```

### Expected behavior

- Decision: `KEEP`
- Preserves neutral wording
- Does not introduce `Sie` solely because the audience is professional
- Does not introduce `du` to make the prose sound more accessible

## F09: Respect an exact SEO constraint without keyword stuffing

### Test prompt

```text
Use $german-reviewer to review this Fachartikel paragraph.

Constraints:
- Exact keyword: Cloud-Backup
- The exact keyword must appear exactly twice.
- Preserve the distinction between backup and synchronization.

German:
Cloud-Backup schützt wichtige Dateien. Mit Cloud-Backup lassen sich Daten extern sichern. Ein Cloud-Backup ist nicht dasselbe wie eine Synchronisierung. Deshalb sollte das Cloud-Backup passend zum jeweiligen Sicherheitskonzept ausgewählt werden.
```

### Expected behavior

- Decision: `EDIT`
- Uses the exact keyword exactly twice
- Preserves the distinction between backup and synchronization
- Improves the concentrated repetition through syntax or unambiguous references rather than terminology drift
- Does not remove the required keyword or add an unsupported SEO claim

## F10: Rewrite a pervasively templated Fachartikel paragraph

### Test prompt

```text
Use $german-reviewer for a full Fachartikel editorial review.

Context:
- Audience: German logistics professionals
- Address: neutral
- Required meaning:
  1. The system records stock movements.
  2. Teams can filter them by location.
  3. Exceptional cases still require manual review.
  4. No CTA is requested.

German:
In der heutigen schnelllebigen Geschäftswelt ist es wichtiger denn je, großartige Lösungen zu nutzen. Die erste großartige Funktion ist die Erfassung von Lagerbewegungen. Eine weitere großartige Funktion ist die Möglichkeit der Filterung nach Standort. Darüber hinaus ist eine weitere wichtige Funktion die Prüfung von Ausnahmefällen, die weiterhin manuell durchgeführt werden sollte. Zusammenfassend lässt sich sagen, dass diese großartigen Funktionen für moderne Logistikteams sehr interessant sind.
```

### Expected behavior

- Decision: `REWRITE`
- Removes the empty opening, repeated `großartige Funktion` frame, and repetitive conclusion
- Preserves all three functional or cautionary meaning units, including manual exception review
- Keeps the recommendation level of `sollte` rather than turning it into an automated capability or obligation
- Adds no statistic, comparison, audience promise, example, or CTA
- Produces a coherent analytical paragraph rather than a list of synonym substitutions

## F11: Preserve a supported, confident reader promise

### Test prompt

```text
Use $german-reviewer to review the conclusion of this German hosting comparison.

Context:
- Address: Sie
- The article compares the tariffs using relevant selection criteria.
- The article explains which tariffs fit different project requirements.

German:
Nach diesem Vergleich wissen Sie, welcher Hosting-Tarif zu den Anforderungen Ihres Projekts passt.
```

### Expected behavior

- Decision: `KEEP`
- Preserves the supported level of confidence
- Does not introduce hedging merely to sound cautious or restrained
- Recognizes that professionalism does not require automatic tone reduction
- Would reassess the promise only if the article content did not support it

## F12: Repair avoidable term repetition through compact coordination

### Test prompt

```text
Use $german-reviewer to review this German Fachartikel sentence.

Context:
- Local, cloud-based, and hybrid deployment are the three intended models.
- Preserve all three models.

German:
Ob lokale Bereitstellung, cloudbasierte Bereitstellung oder hybride Bereitstellung: Für unterschiedliche IT-Strategien stehen passende Bereitstellungsmodelle zur Verfügung.
```

### Expected behavior

- Decision: `EDIT`
- Produces or accepts: `Ob lokal, cloudbasiert oder hybrid: Für unterschiedliche IT-Strategien stehen passende Bereitstellungsmodelle zur Verfügung.`
- Preserves all three models and the shared concept of deployment
- Does not introduce a vague synonym merely to create lexical variety
- Treats the edit as a local readability improvement rather than a reason to rewrite the passage

## F13: Apply Redakteur-level depth to a weak selection passage

### Test prompt

```text
Use $german-reviewer to edit this B2B article at Redakteur level, not merely correct its grammar.

Supported brief:
- The article compares collaboration platforms.
- Co-located and distributed teams have different priorities.
- Time-zone display matters for distributed teams.
- Room booking and local calendar integration matter for co-located teams.
- Address: Sie

German:
Es gibt viele Faktoren, die Sie bei der Auswahl der besten Plattform berücksichtigen sollten. Zuerst überlegen Sie, ob Ihr Team an einem Standort oder verteilt arbeitet. Wenn es verteilt arbeitet, ist die Anzeige von Zeitzonen ein wichtiger Faktor. Wenn es an einem Standort arbeitet, können Raumbuchung und lokale Kalender wichtiger sein. Hier sind weitere Faktoren:
```

### Expected behavior

- Decision: `REWRITE`
- Reframes the passage around the team's concrete collaboration model rather than retaining the generic `many factors` opening
- Establishes the co-located versus distributed distinction before explaining its practical selection criteria
- Uses editorially precise terms and coherent paragraph progression, not only corrected grammar
- Preserves all supplied criteria and the `Sie` system
- Adds no platform capability, statistic, recommendation, or CTA

## F14: Do not treat supplied internal copy as an approved superiority claim

### Test prompt

```text
Use $german-reviewer for a Redakteur-level review of this fictional product passage.

Context:
- This copy is private working material, not approved campaign wording.
- SecureBox supports encrypted synchronization on up to five devices and supports passkeys.
- A free trial is available.
- No evidence comparing SecureBox with every competitor has been supplied.
- Address: Sie

German:
Alle vorgestellten Passwortmanager haben viele nützliche Funktionen. SecureBox ist jedoch zweifellos besser als jedes andere Produkt und spart jedem Unternehmen den größten Aufwand. SecureBox synchronisiert verschlüsselt auf bis zu fünf Geräten und unterstützt Passkeys. Testen Sie SecureBox jetzt kostenlos!
```

### Expected behavior

- Decision: `EDIT` or `REWRITE`, depending on the resulting paragraph structure
- Does not present `private working material` as verified or protected campaign copy
- Replaces the unsupported universal superiority and savings claim with a transparent assessment tied to encrypted synchronization, device count, passkeys, or the relevant user priorities
- Preserves the supplied product name, both capabilities, `bis zu fünf`, and the free-trial CTA function
- Does not weaken or remove the CTA merely because the surrounding passage is editorial
- Makes any change in claim strength visible in the findings

## F15: Improve lexical range without terminology drift

### Test prompt

```text
Use $german-reviewer for a Redakteur-level review of this fictional procurement passage.

Context:
- `Lieferantenrisiko` is an approved technical term.
- Contract review, approval, and ongoing monitoring are three distinct stages.
- Preserve all three stages.

German:
Das Lieferantenrisiko ist für die Vertragsprüfung wichtig. Das Lieferantenrisiko ist für die Freigabe wichtig. Das Lieferantenrisiko ist auch für die laufende Überwachung wichtig. Deshalb ist das Lieferantenrisiko für den Einkauf wichtig.
```

### Expected behavior

- Decision: `REWRITE`
- Resolves the repeated `Lieferantenrisiko ist ... wichtig` architecture across the passage
- Preserves the approved term and all three stages without inventing synonyms for the technical concept
- Improves lexical range through precise verbs, references, combination, or information order rather than thesaurus substitution
- Produces a coherent editorial statement, not four mechanically varied sentences
- Adds no risk category, process step, benefit, statistic, or recommendation

## F16: Create paragraph rhythm without decorative variation

### Test prompt

```text
Use $german-reviewer for a full editorial review of this fictional energy-management passage.

Supported brief:
- The platform displays energy use by site.
- Dashboards update hourly.
- Threshold breaches trigger automatic alerts.
- Data exports occur monthly.
- Address: neutral

German:
Der Energieverbrauch wird nach Standort dargestellt. Die Dashboards werden stündlich aktualisiert. Grenzwertüberschreitungen werden automatisch gemeldet. Die Daten werden monatlich exportiert.
```

### Expected behavior

- Decision: `EDIT` or `REWRITE`, depending on how the statements are combined
- Preserves all four facts, their frequency, and neutral address
- Breaks the four nearly identical passive sentence frames through purposeful information grouping and syntactic variation
- Creates readable variation in sentence length and emphasis without adding filler, rhetoric, or a CTA
- Does not convert every sentence to direct address or force a different synonym for each repeated concept
- Reads as one coherent paragraph whose rhythm supports the information hierarchy

## Pass criteria

- All sixteen cases satisfy their expected behavior in a fresh-context run.
- No supported fact, modality, scope, terminology constraint, SEO constraint, address choice, or CTA function is lost or strengthened.
- Natural or intentionally protected language in F01, F04, F07, F08, and F11 remains unchanged.
- Repetition is corrected by editorial restructuring where appropriate, not by indiscriminate synonym replacement.
- Redakteur-level requests improve paragraph function and information hierarchy rather than stopping at grammatical correctness.
- Lexical and syntactic variety improves article flow without terminology drift, decorative rewriting, or random sentence-length changes.
- Private status is never treated as proof, campaign approval, or permission to publish the supplied material.
- Watch items are treated as evidence prompts rather than banned phrases.
- Results record the date, model and reasoning setting, Skill commit, run number, and reviewer notes.
