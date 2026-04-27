# Garden Design Wizard

**Source:** `app/project/garden.tsx`  
**Purpose:** 3-step wizard to generate an AI garden/landscape redesign. Steps: photo upload → area type → style selection.

---

## Screenshots

![Step 1 – Photo Upload](../../screenshots/project/new-garden/step1.png)
![Step 2 – Garden Area](../../screenshots/project/new-garden/step2.png)
![Step 3 – Style Selection](../../screenshots/project/new-garden/step3.png)

---

## Step 1 — Photo Upload

Uses the shared `PhotoUploadStep` component:
```
├── Header (X close + credits pill with Zap icon)
└── PhotoUploadStep
     ├── Dashed upload area
     ├── 3 garden sample photos
     ├── "Photo Tips" accordion
     └── "Next" button
```

## Step 2 — Garden Area Type

```
├── Header (back + title "Garden Design")
└── ScrollView — Area type icon cards
     [Backyard / Front Garden / Terrace / Balcony / Rooftop / Pool Area / Other]
     (icons from GARDEN_AREA_ICONS in lib/space-types.ts)
```

## Step 3 — Style Selection

```
├── Header (back + title + credits pill)
├── ScrollView horizontal — Group chips (6 garden style groups)
└── ScrollView — Style grid
     ├── CustomStyleCard — "Upload Your Own Style"
     └── [27 garden style cards in 6 groups]
├── AIModelSelector
└── "Generate Design" pinned footer button
```

---

## Style Groups (27 styles across 6 groups)
| Group | Example Styles |
|---|---|
| Zen / Japanese | Camellia & Iris, Maple Tsukubai, Tea House |
| Mediterranean | Provençal Lavender, Coastal Bougainvillea, Tuscan Villa |
| English | Cottage Roses, Herbaceous Border |
| Modern | Minimalist Basalt, Desert Joshua, California Coastal |
| French Formal | Grand Parterre, Château Arches |
| Spanish / Moorish | Andalusian Courtyard, Moroccan Courtyard |

---

## Components
- `PhotoUploadStep`, `StyleCard`, `CustomStyleCard`, `AIModelSelector`
- `GARDEN_AREA_ICONS` from `lib/space-types.ts`
- `Zap` icon for credits pill
- `X`, `ChevronLeft` for navigation

---

## Navigation
- Same flow as Interior/Exterior wizards
- "Generate Design" → `/(tabs)/saved`

---

## Design Notes
- `room_type` stored in DB as `'garden'` — sub-type (backyard, terrace, etc.) goes to edge function body only
- 27 style cards is the most of any wizard — scroll performance is important
