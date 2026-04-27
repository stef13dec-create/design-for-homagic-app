# Result Screen

**Source:** `app/project/[id].tsx`  
**Purpose:** Displays the completed AI redesign with a before/after slider, full-screen zoom view, and download/share actions.

---

## Screenshot

![Screenshot](../../screenshots/project/result/screenshot.png)

---

## Layout

```
SafeAreaView (edges: top)
├── View — Header
│    ├── Pressable — ChevronLeft → back
│    ├── View — Title block
│    │    ├── Text — Room type label (uppercase)
│    │    └── Text — Style display name
│    └── View — spacer
├── ScrollView
│    ├── BeforeAfterSlider (full width, with drag handle)
│    └── View — Metadata card
│         ├── Text — "Before / After" section label
│         ├── Text — style name + mood
│         └── View — Action row
│              ├── Pressable — "View Full" (opens full-screen modal)
│              └── Pressable — "Download" (saves to gallery, turns green on success)
│
└── Modal — "View Full" (full-screen)
     └── GestureHandlerRootView
          ├── GestureDetector (pan gesture)
          │    └── Animated.View
          │         └── Image (result image, full screen)
          ├── View — Zoom controls (+/−)
          └── Pressable — X close
```

---

## Components
- `BeforeAfterSlider` — draggable divider between before/after images
- `GestureDetector` + `Animated.View` — pan + zoom in full-screen modal
- `ChevronLeft`, `X`, `Minus`, `Plus` icons
- `Image` (expo-image) — result image display
- `MediaLibrary.saveToLibraryAsync` — download to gallery

---

## Styles
| Element | Value |
|---|---|
| Background | `#F7F7F5` |
| Header | Horizontal row, paddingHorizontal: 16, paddingVertical: 12 |
| Room type label | Manrope Bold, 10px, primary color, uppercase, letterSpacing: 1 |
| Style name | Noto Serif Bold, 18px |
| Slider | Full width, aspect ratio from image |
| Action row | Row with gap, full width |
| "View Full" button | `#064E3B` fill, flex: 1, `BorderRadius.md` |
| "Download" button | `#064E3B` fill → `#065F46` (success), flex: 1 |
| Full-screen modal | Black background, image fills screen |
| Zoom buttons | Circular, `rgba(0,0,0,0.5)` bg, positioned bottom-center |
| Close (full-screen) | Circular, top-right, `rgba(0,0,0,0.5)` |

---

## Navigation
- ChevronLeft → back to Saved tab
- "View Full" → opens Modal (no navigation)
- "Download" → saves to device gallery (no navigation)

---

## Design Notes
- Zoom supports up to 4× scale (increments of 0.75)
- Pan resets to center when zoom returns to 1×
- Download button shows success state (darker green) — persists until screen remounts
- Share button uses `Share.share()` native sheet
- `BeforeAfterSlider` shows original photo on left, AI result on right with draggable vertical divider
