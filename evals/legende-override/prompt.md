---
description: A playful base tone never leaks into destructive or error situations.
tags: [situation, tone, fr]
max_turns: 8
allowed_tools: [Read, Glob, Grep, Skill]
---

Notre `.legende/wording.md` contient :

```markdown
---
languages: [fr]
person: tu
base: complice
audience: young
---
## Voice
Complice, léger, drôle. Emojis autorisés.
```

Écris le wording de ces trois éléments de notre app photo iOS :
1. l'état vide de la galerie,
2. la confirmation de suppression d'un album nommé par `album.name` contenant `album.count` photos,
3. l'erreur quand l'upload échoue faute de réseau.
