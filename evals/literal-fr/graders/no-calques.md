---
type: regex
target:
  source: file
  path: out/fr.json
pattern: "Mettre à niveau|Obtenir commencé|s'est mal passé|Garde-moi|tout prêt"
flags: i
match: not_contains
---
