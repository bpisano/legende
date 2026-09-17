# Legende

UI/UX design expert plugin for Claude Code. Design, *en légende*.

## Wording

Interface copy that is short, native and on-mood — or absent when the UI can show it.

Claude tends to write UI text that narrates ("Your changes have been saved successfully!"), explains ("Tap the button below to…") and translates literally ("Mettre à niveau"). The `wording` skill fixes that, both **while Claude builds UI** (it triggers on its own) and **on demand** with `/wording`.

### How it judges every string

1. **Remove** — would anyone miss it?
2. **Show** — can an icon, state, badge or haptic say it?
3. **Shorten** — fewest words, verbs on buttons.
4. **Tune** — base tone, overridden by the situation (destructive, error, payment…).

Plus a blacklist of AI-copy tics, native-writing rules per language (loanwords over invented words, platform vocabulary, typography), and localization-safe edits (String Catalogs, i18n JSON, `strings.xml`).

### Usage

```
/wording                  # UI files in the uncommitted diff
/wording Sources/Settings/SettingsView.swift
/wording "Your changes have been saved successfully!"
```

Rewordings are applied directly. Structural changes — removing text, replacing it with an icon, dropping a localization key — are proposed first.

### Project config

The first `/wording` in a project analyzes existing copy and asks up to 3 questions (tone, *tu*/*vous*, audience), each with previews built from your own strings. It writes `.legende/wording.md`:

```markdown
---
languages: [fr, en]
person: tu
base: complice      # neutral | sober | complice | premium | energetic | custom
audience: general   # general | tech | young | pro
situations:
  destructive: serious
  error: calm
---

## Voice
## Lexicon
## Validated examples
```

Commit it. Situation guardrails (e.g. never "OK" on a delete) always apply, whatever the tone.

## Install

```
/plugin marketplace add bpisano/legende
/plugin install legende@legende
```

## Evals

```
claude plugin eval . --judge-model sonnet
```

Each case runs with and without the plugin and reports the delta.

## License

MIT
