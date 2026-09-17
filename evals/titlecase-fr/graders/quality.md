---
type: llm
focus:
  source: file
  path: out/fr.json
---

The corrected strings:
- use sentence case only ("Mes projets", "Partagés avec moi"),
- put a non-breaking space (U+00A0 or U+202F, or explicitly mentioned) before "?" and ":",
- use French guillemets « » instead of straight double quotes around {name},
- keep the {name} placeholder intact,
- shorten the empty state (e.g. "Aucun projet") instead of keeping a long sentence.
