# Setup — `.legende/wording.md`

Runs on a manual `/wording` when `.legende/wording.md` doesn't exist. Never in auto mode.

## 1. Analyze (silently)

- **Platform**: Xcode project, `package.json`, Gradle.
- **Languages**: localization catalogs (`.xcstrings`, `*.lproj`, `locales/`, `values-*/strings.xml`). Source language = development region / default locale.
- **Existing copy**: collect 20–40 user-facing strings. Infer current person (*tu*/*vous*, casual/formal) and tone.
- **Product context**: README, App Store metadata (`fastlane/metadata`), landing page copy in repo.
- **Recurring terms**: domain nouns used consistently (Project, Workspace, Trip…) → lexicon candidates.
- **Quality**: if existing copy is poor (verbose, narrating, literal translations), do **not** treat it as the reference tone. Say so in one line.

## 2. Ask — 3 questions max, with previews

Use `AskUserQuestion` in the user's language. Pre-select (first option, marked recommended) what the analysis detected. Every option carries a **preview** showing the same 3–4 strings rewritten in that option.

**Previews use real strings from the project**: pick one button, one empty state, one error, one destructive confirmation if they exist. Fall back to generic examples (projects list) only when the project has no copy yet.

### Q1 — Base tone
Options: the 4 most plausible of `neutral`, `sober`, `complice`, `premium`, `energetic` (definitions in `tones.md`); "Other" is automatic and becomes `base: custom` with the answer in **Voice**.

Preview format:
```
Button       Create project → C'est parti
Empty        Rien pour l'instant.
Error        Pas de réseau. On réessaie ?
Delete       Supprimer « Voyage » ?
             12 photos seront perdues.
```

### Q2 — Person
Only for languages with a distinction (fr: tu / vous / impersonal; de: du / Sie; es: tú / usted…). Skip for English-only apps.
Preview: the same strings in each form.

### Q3 — Audience
Options: `general`, `tech`, `young`, `pro`. Preview: the same strings, showing loanword vs native choices ("liker" vs "aimer", "feed" vs "fil d'actualité").

Skip any question whose answer is unambiguous from the analysis — confirm it in the summary instead.

## 3. Write the file

Create `.legende/wording.md`:

```markdown
---
languages: [fr, en]      # source first
person: tu               # tu | vous | impersonal (per-language when needed)
base: complice           # neutral | sober | complice | premium | energetic | custom
audience: general        # general | tech | young | pro
situations:              # override tones only; guardrails are fixed
  destructive: serious
  error: calm
  payment: neutral
  permission: base
  empty-state: base
  success: base
  onboarding: base
  legal: neutral
---

## Voice

<!-- to review --> Two or three sentences describing how the app talks. Allowed/forbidden: emoji, exclamation marks, humor.

## Lexicon

<!-- to review -->
- "Projet", never "Workspace"
- "Supprimer", never "Effacer"

## Validated examples

<!-- Added on request only. -->
```

- Fill **Voice** and **Lexicon** from the analysis, marked `<!-- to review -->`.
- Leave **Validated examples** empty.
- Tell the user in one line that the file should be committed.

Then continue with the original `/wording` request.
