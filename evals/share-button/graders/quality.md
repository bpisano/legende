---
type: llm
focus:
  source: file
  path: out/PhotoToolbar.tsx
---

The answer:
- replaces the three text buttons with lucide-react icons that exist (e.g. Share or Share2, Heart or Star, Trash or Trash2) — no invented icon names,
- keeps a short text as aria-label on every icon-only button (e.g. "Share", "Favorite", "Delete"),
- does not add any new dependency.
