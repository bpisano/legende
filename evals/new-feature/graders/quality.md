---
type: llm
focus:
  source: file
  path: out/ProjectsListView.swift
---

Look only at user-visible strings (Text, Label, Button titles, alerts, navigation titles, accessibility announcements). Pass if ALL of these hold:
- the empty state has at most one short line of text plus a create action,
- no visible text announces that duplication succeeded (a haptic, highlight, or an accessibility-only announcement is fine),
- no visible text explains how to use the UI (e.g. "Swipe to…", "Tap…").
