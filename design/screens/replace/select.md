# Replace Object — Draw Region

**Source:** `app/replace/select.tsx`  
**Purpose:** User draws a rectangle over the object they want to replace. Uses gesture-based drawing on the photo.

---

## Screenshot

![Screenshot](../../screenshots/replace/select/screenshot.png)

---

## Layout

```
View (full screen, black bg)
├── View — Top bar (safe area top inset)
│    ├── Pressable — ArrowLeft (back)
│    └── Pressable — RotateCcw (reset selection)
├── GestureDetector (pan gesture — draws selection rect)
│    └── View — Photo container (flex: 1)
│         ├── Image (full contain-fit, letterboxed)
│         └── View — Selection rectangle (dashed border, positioned absolutely)
└── View — Bottom bar (safe area bottom inset)
     └── Pressable — "Continue" (primary button, disabled until rect drawn)
```

---

## Components
- `GestureDetector` + `Gesture.Pan()` — worklet-based rectangle drawing
- `Image` (expo-image) — the room photo in contain mode
- `ArrowLeft`, `RotateCcw` icons

---

## Styles
| Element | Value |
|---|---|
| Screen bg | Black |
| Image | Contain-fit, letterboxed within the view |
| Selection rect | Dashed `#064E3B` border, semi-transparent fill |
| Top bar | `rgba(0,0,0,0.6)` bg |
| Back/reset buttons | White icons |
| "Continue" button | `#064E3B` fill, full width |

---

## Navigation
- ArrowLeft → back (to `/replace/index`)
- "Continue" → `/replace/finalize` with selection coords as params

---

## Design Notes
- Uses Reanimated worklets for performant gesture tracking
- Clamps selection to image bounds (handles letterbox offset math)
- Converts screen-space rect coordinates to image-space when navigating to finalize
- Reset button clears the `rect` state back to null
