# Replace Object — Result

**Source:** `app/replace/result.tsx`  
**Purpose:** Displays the completed object replacement with a before/after slider and full-screen zoom view.

---

## Screenshot

![Screenshot](../../screenshots/replace/result/screenshot.png)

---

## Layout

```
View (full screen, safe area insets)
├── View — Header (safe area top)
│    ├── Pressable — ArrowLeft (back)
│    └── View — Action buttons row
│         ├── Pressable — Download (ArrowDown icon)
│         └── Pressable — Share (Share2 icon)
├── ScrollView
│    ├── BeforeAfterSlider (original vs result)
│    └── View — Info card
│         ├── Text — prompt used
│         └── Pressable — "View Full" button
└── Modal — Full-screen view
     └── GestureHandlerRootView
          ├── GestureDetector (pan)
          │    └── Animated.Image (result, full screen)
          ├── Zoom controls (+/−)
          └── Pressable — X close
```

---

## Components
- `BeforeAfterSlider` — drag to compare original and replaced image
- `useReplaceRealtime` — Supabase realtime subscription for status updates
- `GestureDetector` + Reanimated — pan + zoom in modal
- `ArrowLeft`, `RefreshCw`, `X`, `Minus`, `Plus` icons
- `MediaLibrary.saveToLibraryAsync` — download

---

## Styles
Same visual language as the design result screen (`project/[id].tsx`).

| Element | Value |
|---|---|
| Background | `#F7F7F5` |
| Slider | Full width |
| Full-screen modal | Black bg, image fills screen |
| Zoom controls | Circular buttons, `rgba(0,0,0,0.5)`, bottom-center |

---

## Navigation
- ArrowLeft → back (to Saved tab)
- "View Full" → opens full-screen Modal
- Download → saves to gallery
- Share → native share sheet

---

## Design Notes
- Realtime subscription via `useReplaceRealtime` — polls/listens until status is `complete`
- Shows retry option if status is `error`
- Same zoom/pan implementation as the design result screen
