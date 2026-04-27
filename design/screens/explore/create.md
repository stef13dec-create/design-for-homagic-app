# Explore Create Wizard

**Source:** `app/explore/create.tsx`  
**Purpose:** 2-step modal wizard launched from the Explore tab after a style card is tapped. Steps: space type selection → photo upload + generate.

---

## Screenshots

![Step 1 – Space Type](../../screenshots/explore/create/step1.png)
![Step 2 – Photo Upload](../../screenshots/explore/create/step2.png)

---

## Step 1 — Choose Space Type

```
SafeAreaView (edges: top)
├── View — Header
│    ├── Pressable — X (close wizard)
│    └── Text — "Choose Room Type" / "Choose Garden Area" / "Choose Building Type"
│         (title changes based on category)
├── Text — subtitle
├── Image — Selected style thumbnail banner (full width, 16:9)
└── ScrollView — Space type icon cards
     └── SpaceTypeCard × N
          ├── Icon (Lucide)
          └── Text — label
```

## Step 2 — Photo Upload + Generate

```
SafeAreaView (edges: top)
├── View — Header
│    ├── Pressable — ChevronLeft (back to step 1)
│    └── Pressable — X (close wizard)
├── Image — Selected style thumbnail banner (full width, 16:9)
├── ScrollView (flex: 1)
│    └── PhotoUploadStep
│         ├── Upload area (dashed, tappable)
│         ├── Sample photos row
│         └── Photo Tips
└── View — Pinned footer (safe area bottom inset applied)
     ├── AIModelSelector (chip row)
     └── Pressable — "Generate Design" (primary button, full width)
```

---

## Components
- `PhotoUploadStep` — shared photo upload UI
- `AIModelSelector` — Gemini / Seedream / Grok chip row
- `Image` (expo-image) — style thumbnail banner at top of both steps
- `X`, `ChevronLeft` icons
- `useSafeAreaInsets` — applies bottom padding to footer

---

## Styles
| Element | Value |
|---|---|
| Background | `#F7F7F5` |
| Style thumbnail | Full width, `aspectRatio: 16/9`, `contentFit: cover` |
| Space type card | Icon + label, selected state with primary border |
| Footer | Pinned below ScrollView, safe area bottom inset padding |
| Generate button | `#064E3B` fill, full width, `paddingVertical: 16` |

---

## Navigation
- X → closes wizard (back to Explore tab)
- Step 1 space type tap → Step 2
- ChevronLeft on Step 2 → back to Step 1
- "Generate Design" → fires edge function → `/(tabs)/saved`
- Insufficient credits → Alert → `/paywall`

---

## Design Notes
- Style thumbnail is always visible at the top of both steps — gives context of which style was selected
- Footer is pinned outside `ScrollView` to avoid being pushed off-screen by the keyboard or content
- `useSafeAreaInsets().bottom` applied to footer so it clears the Android navigation bar
- Category determines which space types and icons are shown (interior rooms / garden areas / building types)
