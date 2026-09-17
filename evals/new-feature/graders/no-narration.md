---
type: regex
target:
  source: file
  path: out/ProjectsListView.swift
pattern: "\"[^\"]*(successfully|Tap (the|here|to)|Swipe (left|right|to)|You don't have any)[^\"]*\""
flags: i
match: not_contains
---
