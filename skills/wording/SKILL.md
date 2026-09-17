---
name: wording
description: Craft UI copy the way a senior UX writer would — short, native, on-mood, or no text at all when the UI can show it. Use whenever you write, edit or review any user-facing text in an interface (button labels, titles, subtitles, empty states, errors, alerts, confirmations, toasts, loading, onboarding, paywalls, permission prompts, localization catalogs), including while building a new screen or component even if the user never mentioned wording. Also runs as /wording [file | text] to rework existing copy.
---

# Wording

Great interface copy is mostly **absent**. Every string must earn its place. The UI shows; text only says what the UI cannot.

## 0. Load context

1. Read `.legende/wording.md` at the project root if it exists: frontmatter = `languages` (source first), `person`, `base` tone, `audience`, `situations` overrides; body = voice, lexicon, validated examples. The lexicon always wins.
2. No config:
   - **Manual run** (`/wording`) → run the setup in `references/setup.md` first, then continue.
   - **Auto mode** (you are writing UI as part of another task) → never interrupt. Infer tone, person and language from existing strings in the project, apply plugin defaults, keep going.
3. Detect the stack (SwiftUI, UIKit, web framework, Compose) and where strings live (inline, `.xcstrings`, `Localizable.strings`, i18n JSON, `strings.xml`).

## 1. Judge every string — the ladder

For each string, go down in order and **stop at the first rung that works**. Details and before/after examples: `references/ladder.md`.

1. **Remove** — would the user understand without it? Titles repeating the button, subtitles repeating the title, text explaining what the UI already shows → delete.
2. **Show** — can a visual carry it? Icon, button state (disabled, spinner, checkmark), badge, color, haptic, animation, native empty-state component → replace. Rules: `references/visuals.md`.
3. **Shorten** — text is needed → minimum words. Buttons are verbs. No sentence where a word works.
4. **Tune** — apply the base tone, or the tone of the detected situation (`references/situations.md`, tones in `references/tones.md`).

Then reject anything in `references/blacklist.md`. The worst offenders:
- Narrating what the app did: "Your changes have been saved successfully"
- Explaining how the UI works: "Tap the button below to…"
- Filler politeness, vague reassurance, dev jargon, repeating what the user just did.

Exceptions where text is **required** (never remove, never shorten past meaning): irreversible destructive actions (name what is lost), errors (say what to do), legal/consent/pricing.

## 2. Write native, never translate

Write directly in the target language. Never draft in English and translate. Use the words the target user actually says out loud, follow platform vocabulary, prefer common English loanwords over invented or stiff equivalents, respect each language's typography. Rules per language: `references/native.md`.

French: before `? ! : ;` and inside `« »` the space is **non-breaking** — write it as an escape (` ` in JSON/JS, `\u{202F}` in Swift), never a typed space.

## 3. Apply

### Auto mode (writing UI inside another task)
- Apply the ladder silently to the strings you write. No report, no questions.
- Only touch strings that are part of the task. Do not rewrite unrelated existing copy.
- Follow the localization rules in `references/i18n.md`.

### Manual mode (`/wording`)
**Scope**
- `/wording <file>` → that file. `/wording "<text>"` → answer with rewrites only, no file changes.
- `/wording` without argument → UI files in the uncommitted diff; if empty, UI files you edited earlier in this session; otherwise ask for the target. Never scan the whole repo silently.

**Change policy**
- **Apply directly**: rewording (shorter, clearer, native, on-tone).
- **Propose first**: removing a string, replacing text with an icon or visual, adding a UI element, removing a localization key.
- Replacing text with an icon: **always keep the text as the accessibility label** (`accessibilityLabel`, `aria-label`, `contentDescription`).

**Report** — follows its own rules: short, no intro, no summary of what was analyzed. Write it in the user's language.

```
Applied (4)
  SettingsView.swift:42   "Save changes" → "Save"
  SettingsView.swift:58   "Your settings have been saved successfully!" → removed, checkmark on button
  ...

To validate (2)
  1. ProjectRow.swift:17  Remove subtitle "Tap to open"
                          → row already has a chevron
  2. Toolbar.swift:9      "Share" button → icon square.and.arrow.up
                          a11y label kept

Apply 1, 2? (all / numbers / none)
```

- One line per change; a reason only for structural changes, a few words.
- Nothing to change → `Nothing to change.`

**Learning**
- When the user rejects a proposal and gives their own wording (e.g. "no, say *Delete*"), offer to add the rule to the lexicon in `.legende/wording.md` in one line. Write only after they agree.
- When a term is used consistently across the codebase and missing from the lexicon, offer to add it.
- Add validated examples only when the user asks.
