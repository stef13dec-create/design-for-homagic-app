# Exterior Design Wizard

**Source:** `app/project/exterior.tsx`  
**Purpose:** 3-step wizard to generate an AI exterior/facade redesign. Steps: photo upload → building type → style selection.

---

## Screenshots

![Step 1 – Photo Upload](../../screenshots/project/new-exterior/step1.png)
![Step 2 – Building Type](../../screenshots/project/new-exterior/step2.png)
![Step 3 – Style Selection](../../screenshots/project/new-exterior/step3.png)

---

## Step 1 — Photo Upload

```
SafeAreaView
├── Header (X close + credits pill)
├── Text — "Upload a photo of your building exterior"
├── Dashed upload area → bottom-sheet picker (Gallery / Camera)
├── Row — 3 facade sample photos
└── Pressable — "Next" button
```

## Step 2 — Building Type

```
├── Header (back + title "Exterior Design")
├── Text — "Choose the type of building"
└── ScrollView — Building type icon cards
     [House / Apartment / Villa / Commercial / Other]
```

## Step 3 — Style Selection

```
├── Header (back + title + credits pill)
├── ScrollView horizontal — Group chips (5 exterior groups)
└── ScrollView — Style grid
     ├── CustomStyleCard — "Upload Your Own Style"
     └── [14 exterior style cards in 5 groups]
├── AIModelSelector
└── "Generate Design" pinned footer button
```

---

## Components
- `StyleCard` (memoized), `CustomStyleCard`, `AIModelSelector`
- `EXTERIOR_BUILDING_ICONS` from `lib/space-types.ts`
- Bottom-sheet picker Modal for photo source selection (Gallery / Camera)
- `Camera`, `ImageIcon` icons

---

## Styles
Same token system as Interior wizard. 14 style cards across 5 groups.

| Group | Styles |
|---|---|
| Modern | Contemporary, Warm Minimalism, Coastal Modern |
| Classic | Modern Tudor, Mediterranean Rustic, New Transitional |
| Nature | Biophilic Eco, Organic Modern, Modern Prairie |
| Tech | Smart High-Tech, Textured Industrial |
| Farm | Modern Farmhouse 2.0, Mid-Century Modern, Japandi |

---

## Navigation
- Same pattern as Interior wizard
- "Generate Design" → edge function → `/(tabs)/saved`
- File size limit: 10MB (shows error if exceeded)

---

## Design Notes
- Has a custom bottom-sheet `Modal` for photo source (Gallery vs Camera) — not `PhotoUploadStep`
- Photo Tips are shown in a separate Modal (tipsVisible state)
- Building type icons use `EXTERIOR_BUILDING_ICONS` map from `lib/space-types.ts`
