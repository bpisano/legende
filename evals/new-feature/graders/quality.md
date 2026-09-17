---
type: llm
focus:
  source: file
  path: out/ProjectsListView.swift
---

The code:
- uses a native empty state (ContentUnavailableView or equivalent) with at most one short line of text and a create action,
- shows duplication feedback without a sentence announcing success (the new row appearing, a haptic, or a checkmark is fine),
- labels buttons with short verbs ("New Project", "Create Project", "Duplicate"),
- contains no text explaining how to use the UI.
