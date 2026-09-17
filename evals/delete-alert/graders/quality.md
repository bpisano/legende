---
type: llm
focus:
  source: file
  path: out/DeleteAlert.swift
---

Pass if ALL of these hold (be lenient on style, strict on these facts):
- the confirm button is a precise verb such as "Delete" (not "OK"/"Yes"/"Confirm"),
- the title references the album name (e.g. via album.name), not "Warning" or "Are you sure?",
- somewhere the photo count is used to say photos will be lost/deleted. Any pluralization technique counts: `^[… photo](inflect: true)`, a ternary, a stringsdict/catalog. Omitting the message when the album has no photos is acceptable.
