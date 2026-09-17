---
description: French strings that read like literal translations get rewritten natively.
tags: [native, fr, i18n]
max_turns: 8
allowed_tools: [Read, Glob, Grep, Skill, Write]
---

Voici les chaînes françaises de notre app iOS grand public (on tutoie). Améliore le wording.

```json
{
  "paywall.cta": "Mettre à niveau vers Pro",
  "onboarding.done": "Vous êtes tout prêt !",
  "onboarding.start": "Obtenir commencé",
  "error.generic": "Oups ! Quelque chose s'est mal passé.",
  "search.empty": "Aucun résultat trouvé pour votre recherche",
  "settings.title": "Paramètres",
  "login.remember": "Garde-moi connecté"
}
```

Écris le résultat final dans `out/fr.json`. Tous les changements sont pré-approuvés, applique-les sans demander.
