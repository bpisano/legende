---
description: Destructive confirmation names the object, states the loss, uses the exact verb.
tags: [situation, destructive, swiftui, en]
max_turns: 8
allowed_tools: [Read, Glob, Grep, Skill, Write]
---

Polish the wording of this delete confirmation.

```swift
.alert("Warning", isPresented: $showDelete) {
    Button("OK") { store.delete(album) }
    Button("Cancel", role: .cancel) {}
} message: {
    Text("Are you sure you want to do this? This action cannot be undone.")
}
// album.name is the album title, album.photos.count its number of photos
```

Write the final result to `out/DeleteAlert.swift`. All changes are pre-approved — apply them without asking.
