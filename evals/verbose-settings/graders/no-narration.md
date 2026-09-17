---
type: regex
target:
  source: file
  path: out/SettingsView.swift
pattern: "saved successfully|Use the toggle below|Click Here"
flags: i
match: not_contains
---
