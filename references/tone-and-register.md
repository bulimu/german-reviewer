# Tone and Register Guide

Use this guide when the review depends on audience fit, address form, formality, channel, brand voice, empathy, promotional intensity, or register consistency.

The goal is contextual fit, not maximum friendliness or informality. Preserve a suitable, consistent register and change it only when there is evidence that it conflicts with the brief or the surrounding text.

## Distinguish the concepts

- **Address form** determines how the text addresses readers: `du`, `Sie`, `ihr`, or neutral wording.
- **Register** reflects the social and situational level of language, from conversational to institutional.
- **Tone** expresses attitude, such as warm, direct, reassuring, urgent, restrained, or promotional.
- **Voice** is the more stable personality of a writer or brand across texts.

These dimensions interact but are not interchangeable. A text can use `du` and remain precise and professionally restrained. A `Sie` text can sound warm and approachable.

## Evidence priority

Use evidence in this order:

1. Explicit user instructions and approved style guides
2. Glossaries, existing product terminology, and validated reference copy
3. The surrounding document, interface, campaign, or conversation
4. Audience, relationship, channel, purpose, and German locale
5. The existing target text, when it is internally consistent and contextually plausible

Do not replace a consistent choice with a personal preference. If two choices are equally suitable, preserve the original or classify the alternative as `Optional`.

## Build a minimal tone brief

Before evaluating tone, identify as many of these fields as the context supports:

| Field | Examples |
|---|---|
| Audience | Consumers, administrators, developers, applicants, patients |
| Relationship | Peer-to-peer, service-to-customer, institution-to-public |
| Channel | UI, help article, support email, landing page, legal notice |
| Address | `du`, `Sie`, `ihr`, neutral |
| Formality | Conversational, neutral-professional, formal, institutional |
| Warmth | Restrained, friendly, empathetic |
| Directness | Instructional, consultative, diplomatic |
| Promotion | None, moderate, campaign-led |
| Locale | Germany, Austria, Switzerland, or unspecified standard German |

Do not invent detailed brand attributes when only the text is available. State an assumption only if it materially changes the edit.

## Address forms

### du

Use singular `du` when required by the brief or established by surrounding copy. Keep all related forms consistent, including `dich`, `dir`, `dein`, verb forms, and imperatives.

```text
Du kannst die Datei später löschen.
Klicke auf „Speichern“.
```

`Klick` and `Klicke` can both be correct. Follow the style guide and surrounding instructions rather than changing one mechanically.

### Sie

Use formal `Sie` with the corresponding capitalized forms `Ihnen` and `Ihr` and the third-person plural verb form.

```text
Sie können die Datei später löschen.
Klicken Sie auf „Speichern“.
```

Do not assume that `Sie` requires bureaucratic syntax or distant vocabulary. It can remain direct, clear, and friendly.

### ihr

Use plural informal `ihr` only when the text addresses a known group informally. Keep `euch`, `euer`, verb forms, and plural imperatives consistent.

```text
Ihr könnt die Datei später löschen.
Klickt auf „Speichern“.
```

Do not substitute `ihr` for inclusive singular `du` unless the audience is genuinely addressed as a group.

### Neutral wording

Neutral wording can work for compact labels, procedural headings, public information, or content that must avoid choosing an address form.

```text
Datei auswählen
Auf „Speichern“ klicken
E-Mail-Adresse bestätigen
```

Do not force neutral infinitive constructions through an entire article if they make the prose impersonal or difficult to follow.

### Capitalization

Capitalize formal `Sie`, `Ihnen`, and possessive `Ihr` as required. Lowercase `du`, `dir`, `dich`, and `dein` in ordinary running text unless a house style or direct-correspondence convention specifies capitalization. Treat a simple capitalization defect primarily as `Grammar and syntax`; use `Tone and register` when it reflects a broader address-system inconsistency.

## Consistency rules

Check address consistency across:

- Personal and possessive pronouns
- Verb agreement
- Imperatives
- Greetings and closings
- Buttons, instructions, helper text, and error messages
- Headings, captions, and calls to action

A change of address form is not automatically an error. Quoted speech, testimonials, legal excerpts, embedded third-party text, and sections for different audiences can intentionally use different forms. Judge whether the change belongs to the communication structure.

Context: a product flow with an explicit `du` style.

```text
Original: Erstelle dein Konto. Bestätigen Sie anschließend Ihre E-Mail-Adresse.
Suggested: Erstelle dein Konto. Bestätige anschließend deine E-Mail-Adresse.
Judgment: Must fix · Tone and register
```

## Register spectrum

### Conversational

Suitable for some onboarding flows, communities, lifestyle products, and informal campaigns. It can use contractions such as `geht's`, short sentences, and a more personal rhythm.

Do not add slang, emojis, exclamation marks, or filler words such as `mal` without brand evidence. Conversational language still needs precision.

### Neutral-professional

Suitable for many product interfaces, help centers, business blogs, and general service communication. Prefer clear verbs, direct structure, restrained warmth, and terminology consistency.

Neutral-professional is not the same as bland. It can use either `du` or `Sie`.

### Formal-professional

Suitable for business correspondence, formal reports, some regulated domains, and communication where social distance matters. Use complete, precise formulations without unnecessary bureaucracy.

Do not add nominal chains or passive voice merely to make a text sound formal.

### Institutional or regulatory

Suitable for legal notices, official procedures, policies, and high-stakes instructions. Precision, scope, traceability, and required terminology take priority over warmth or brevity.

Do not simplify away conditions, obligations, exceptions, or legal distinctions. A language review does not authorize legal reinterpretation.

## Tone dimensions

Assess tone on separate axes rather than assigning one vague label.

### Directness

Direct instructions are often useful in UI and help content. Diplomatic or consultative wording may be better for refusals, sensitive support cases, or recommendations.

Do not weaken a requirement by changing `muss` to `sollte`, or strengthen advice in the opposite direction, merely to alter tone.

### Warmth and empathy

Warmth can come from helpful wording, acknowledgment, and a clear next step. It does not require jokes, emojis, apologies, or emotional language.

Context: a neutral-professional upload error.

```text
Overly vague: Hoppla! Da ist wohl etwas schiefgelaufen 😅
Better fit: Die Datei konnte nicht hochgeladen werden. Versuche es erneut.
```

The better version names the problem and gives a recovery step. A playful original may still fit a brand with an explicitly casual voice.

### Authority and certainty

Warnings, policies, and expert guidance can require confident language. Preserve the source's degree of certainty and the speaker's actual authority.

Do not turn `kann` into `wird`, `empfohlen` into `erforderlich`, or a possibility into a guarantee. Classify such changes primarily as `Meaning preservation`.

### Promotional intensity

Marketing can legitimately use energy and benefit-led language. Product documentation, support, and transactional UI usually need more restraint.

Context: a factual help article.

```text
Original: Nutze unsere revolutionäre Funktion, um Besprechungen automatisch zu transkribieren!
Suggested: Mit der Funktion transkribierst du Besprechungen automatisch.
Judgment: Recommended · Tone and register
```

Do not remove approved campaign language from marketing solely because it sounds promotional. Flag unsupported or strengthened claims under `Meaning preservation` when source evidence is available.

### Urgency

Urgency should correspond to a real deadline, risk, or blocked task. Do not create pressure with `sofort`, repeated exclamation marks, or vague scarcity unless the brief supports it.

Preserve urgency when delay has a genuine consequence. State the required action and timing clearly.

## Channel calibration

| Channel | Typical priority | Common mismatch |
|---|---|---|
| Button or menu label | Brevity, action clarity, UI convention | Full promotional sentence instead of a functional label |
| Helper text | Immediate comprehension, local context | Explaining information already visible |
| Error message | Specific problem and recovery | Blame, vague apology, or playful wording that hides the action |
| Onboarding | Momentum, reassurance, task clarity | Excessive hype or unexplained technical language |
| Help article | Scanability, precision, consistent instruction style | Marketing voice inside procedural content |
| Support message | Accuracy, empathy, ownership, next step | Scripted friendliness or defensive language |
| B2B content | Audience expertise, credibility, terminology | Assuming all business audiences require `Sie` and nominal style |
| Marketing page | Differentiation, benefits, brand voice | Unsupported superlatives or generic hype |
| Legal or policy text | Exact scope, obligations, defined terms | Simplification that changes legal meaning |

Channel conventions guide judgment but do not override an explicit style guide.

## Blame, politeness, and reader agency

Avoid wording that assigns blame when the system state can be described neutrally.

```text
Blaming: Du hast ein falsches Passwort eingegeben.
Neutral: Das Passwort ist nicht korrekt.
```

Keep the more direct version when identifying the user's action is necessary for recovery or security. Do not obscure responsibility where it matters.

Use `bitte` where it genuinely adds politeness or softens a request. Do not insert it into every instruction, and do not let politeness hide whether an action is optional or required.

## Inclusive language

Follow the supplied inclusive-language policy and maintain it consistently. Possible strategies include neutral forms, paired forms, typographic markers, or conventional generics, but their suitability depends on the organization, audience, accessibility requirements, and locale.

If no policy is supplied, preserve a consistent, contextually plausible strategy. Do not impose or remove gender-inclusive language as an unrequested ideological or stylistic preference. Flag a form when it is grammatically broken, internally inconsistent, inaccessible under an explicit requirement, or contrary to the brief.

## Locale and regional conventions

Preserve the requested German locale. Germany, Austria, and Switzerland can differ in spelling, vocabulary, punctuation, institutional terms, and expectations of formality. For example, Swiss standard German uses `ss` instead of `ß`.

Do not convert a consistent regional variant to another locale without instruction. If no locale is given, accept standard variants that are natural and internally consistent rather than treating difference as error.

## Choose the most specific issue label

| Main observation | Primary dimension |
|---|---|
| `du`, `Sie`, or `ihr` conflicts with the brief or surrounding text | Tone and register |
| Formal pronoun is incorrectly capitalized | Grammar and syntax |
| A word is semantically wrong for the audience or task | Word choice and collocations |
| Prose is dense regardless of audience relationship | Style and readability |
| Promotional wording adds or strengthens a factual claim | Meaning preservation |
| Wording is accurate but too promotional, distant, playful, or blunt for the channel | Tone and register |

Choose one primary dimension and explain secondary effects only when useful.

## Severity calibration

### Must fix

- Explicit address-form or brand-voice requirement is violated.
- Address forms, pronouns, verbs, or imperatives switch disruptively.
- Tone makes a critical instruction misleading, disrespectful, or unusable.
- A required institutional, legal, accessibility, or locale convention is violated.

### Recommended

- Register is consistent but noticeably mismatched to the audience or channel.
- The text is unnecessarily distant, promotional, playful, abrupt, or apologetic.
- A message is accurate but handles error, refusal, urgency, or empathy poorly.

### Optional

- Both versions fit the brief and differ mainly in warmth, rhythm, or personal preference.
- The style guide permits more than one imperative, greeting, or degree of formality.

Several optional preferences do not justify changing an otherwise suitable voice.

## Missing or conflicting context

When context is missing:

1. Follow an applicable active project context before inferring from the text.
2. Preserve a consistent existing address form and register when no stronger guidance exists.
3. Infer from adjacent strings or paragraphs before judging an isolated sentence.
4. Keep wording neutral when no direct address is needed.
5. If direct address is required and no evidence resolves the choice, use `Sie` as the final fallback.
6. Avoid adding friendliness, formality, humor, or promotion without evidence.
7. State an assumption only when it affects the result materially.

Do not use the `Sie` fallback to convert a consistent `du` text, and do not introduce `Sie` into neutral text merely to make a choice. If a project context is available, apply the detailed precedence and override rules in [project-context.md](project-context.md).

When instructions conflict, preserve meaning and protected terminology first. Then follow the most specific and authoritative style evidence. Surface the conflict instead of silently inventing a hybrid voice.

## Final check

Before confirming a tone or register edit, ask:

- Does the context support the chosen address form and level of formality?
- Are pronouns, verbs, imperatives, greetings, and calls to action consistent?
- Is the tone appropriate for both the audience and the channel?
- Have meaning, certainty, obligations, and product claims remained unchanged?
- Did the edit remove a real mismatch rather than merely impose another voice?
