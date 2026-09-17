---
description: Toolbar text buttons with universal meaning become icons from the project's library, keeping aria-labels.
tags: [show, web, react, en]
max_turns: 8
allowed_tools: [Read, Glob, Grep, Skill, Write]
---

Our React app uses lucide-react for icons. Improve the wording of this toolbar.

```tsx
import { Button } from "@/components/ui/button";

export function PhotoToolbar({ onShare, onDelete, onFavorite }: Props) {
  return (
    <div className="flex gap-2">
      <Button variant="ghost" onClick={onShare}>Share this photo</Button>
      <Button variant="ghost" onClick={onFavorite}>Add to favorites</Button>
      <Button variant="ghost" onClick={onDelete}>Delete photo</Button>
    </div>
  );
}
```

Write the final result to `out/PhotoToolbar.tsx`. All changes are pre-approved — apply them without asking.
