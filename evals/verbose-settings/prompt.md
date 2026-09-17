---
description: Narrating and explaining copy in a SwiftUI settings screen gets removed or shortened.
tags: [blacklist, swiftui, en]
max_turns: 8
allowed_tools: [Read, Glob, Grep, Skill, Write]
---

Improve the UI copy of this SwiftUI view.

```swift
struct SettingsView: View {
    @State private var notifications = true
    @State private var saved = false

    var body: some View {
        Form {
            Section(header: Text("Your Settings"), footer: Text("Use the toggle below to enable or disable notifications.")) {
                Toggle("Enable Notifications", isOn: $notifications)
            }
            Button("Click Here To Save Your Changes") {
                save()
                saved = true
            }
            if saved {
                Text("Your changes have been saved successfully!")
            }
        }
        .navigationTitle("Settings")
    }
}
```

Write the final result to `out/SettingsView.swift`. All changes are pre-approved — apply them without asking.
