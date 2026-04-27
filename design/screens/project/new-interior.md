# Interior Design Wizard

**Source:** `app/project/new.tsx`  
**Purpose:** 3-step wizard to generate an AI interior redesign. Steps: photo upload → room type → style selection.

---

## Screenshots

![Step 1 – Photo Upload](../../screenshots/project/new-interior/step1.png)
![Step 2 – Room Type](../../screenshots/project/new-interior/step2.png)
![Step 3 – Style Selection](../../screenshots/project/new-interior/step3.png)

---

## Step 1 — Photo Upload

```
SafeAreaView
├── View — Header (X close button + step indicator)
└── PhotoUploadStep component
     ├── Dashed upload area (tap → bottom-sheet picker)
     │    └── [Camera icon + "Upload a photo of your room"]
     │         OR selected photo preview
     ├── Row — 3 sample interior photos (horizontal, tappable)
     ├── Pressable — "Photo Tips" (expandable)
     └── Pressable — "Next" (primary button, disabled until photo selected)
```

## Step 2 — Room Type

```
SafeAreaView
├── View — Header (back + X + title "Choose Room Type")
├── Text — "Select the room you want to redesign"
└── ScrollView — Icon card grid
     └── Room type card × N (icon + label)
          [Living Room / Bedroom / Kitchen / Bathroom / Dining Room / Office / Other]
```

## Step 3 — Style Selection

```
SafeAreaView
├── View — Header (back + X + title "Choose a Style")
├── View — Credits pill (Zap icon + remaining count)
├── ScrollView horizontal — Group chips (5 groups)
└── ScrollView — Style grid
     ├── CustomStyleCard — "Upload Your Own Style" (full-width, dashed, top of grid)
     └── [For each group]
          ├── Section header
          └── StyleCard grid (2–3 columns)
               └── StyleCard — image + name + selected border
├── AIModelSelector — chip row (Gemini / Seedream / Grok)
└── Pressable — "Generate Design" (primary button, pinned footer)
```

---

## Components
- `PhotoUploadStep` — shared upload UI with bottom-sheet picker, samples, tips
- `StyleCard` (memoized) — image card with selection state + fullscreen modal
- `CustomStyleCard` — full-width dashed card for user-uploaded style reference
- `AIModelSelector` — 3-chip row for AI provider selection
- `X`, `ChevronLeft` icons — navigation controls

---

## Styles
| Element | Value |
|---|---|
| Background | `#F7F7F5` |
| Photo upload area | Dashed border, `#064E3B` accent |
| Room type card | Icon + label, selected state with primary border |
| Group chip | `BorderRadius.full`, primary fill when active |
| Generate button | `#064E3B` fill, full width, `paddingVertical: 16` |
| Custom style card | Full width, dashed border, left-aligned text |

---

## Navigation
- X button → Alert confirm discard → back
- Step 1 "Next" → Step 2
- Step 2 room type tap → Step 3
- "Generate Design" → fires edge function → `/(tabs)/saved`
- Insufficient credits → Alert with Upgrade option → `/paywall`

---

## Design Notes
- Credit check happens before generation — no orphan DB records on failure
- Style and room type state persists across steps within wizard
- `startStep=3` param allows skipping to style step (used by Explore flow)
