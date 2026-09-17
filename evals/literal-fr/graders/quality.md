---
type: llm
focus:
  source: file
  path: out/fr.json
---

Pass if ALL of these hold:
- no string reads as a literal English translation (no "Mettre à niveau", "Obtenir commencé", "Quelque chose s'est mal passé", "Garde-moi connecté"),
- "tu" is used wherever a person is addressed, never "vous"/"votre",
- settings.title is "Réglages",
- the generic error invites the user to retry rather than saying "Oups".
