---
type: llm
focus:
  source: file
  path: out/fr.json
---

Pass if ALL of these hold:
- labels use sentence case ("Mes projets" or "Projets", "Partagés avec moi"),
- the rename label uses French guillemets « » around the {name} placeholder,
- the empty state is short (a few words, e.g. "Aucun projet"),
- no placeholder is added that was not in the original string of the same key (only project.rename had {name}).
