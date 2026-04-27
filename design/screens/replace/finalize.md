# Replace Object — Finalize

**Source:** `app/replace/finalize.tsx`  
**Purpose:** User describes what they want to place in the selected region and optionally uploads a reference photo before triggering transformation.

---

## Screenshot

![Screenshot](../../screenshots/replace/finalize/screenshot.png)

---

## Layout

```
View (full screen, safe area insets)
├── View — Header (safe area top)
│    └── Pressable — ArrowLeft (back)
└── ScrollView
     ├── Image — Cropped object preview (the selected region from step 2)
     ├── Text — "What do you want here?" (label)
     ├── TextInput — Prompt (multiline, placeholder: "Describe what you want…")
     ├── Text — "Reference photo (optional)"
     ├── Pressable — Upload reference photo
     │    └── Camera icon + "Add reference photo" OR preview thumbnail
     └── Pressable — "Transform" (primary button, full width)
          └── ActivityIndicator during loading
```

---

## Components
- `Image` (expo-image) — cropped object preview
- `TextInput` — multiline prompt input
- `ImagePicker` — optional reference photo
- `Camera`, `ArrowLeft` icons
- `ImageManipulator` — crops the original photo using the rect coordinates

---

## Styles
| Element | Value |
|---|---|
| Background | `#F7F7F5` |
| Cropped preview | Rounded, full width, aspect ratio preserved |
| TextInput | White bg, `BorderRadius.md`, multiline, `minHeight: 100` |
| Reference upload | Dashed border or preview thumbnail |
| "Transform" button | `#064E3B` fill, full width |

---

## Navigation
- ArrowLeft → back to `/replace/select`
- "Transform" → creates `replacements` record + invokes edge function → `/replace/result`

---

## Design Notes
- Either a text prompt or a reference photo is required (alerts user if both are empty)
- The crop operation converts screen-space coordinates to pixel-space using `ImageManipulator`
- Reference photo is uploaded to Supabase storage before edge function call
