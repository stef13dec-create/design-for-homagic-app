# Proposal View Screen

**Source:** `app/assistant/proposal/[id].tsx`  
**Purpose:** Shows the status and details of a consultation — 4 distinct states depending on where the consultation is in the workflow.

---

## Screenshot

![Pending](../../screenshots/assistant/proposal/pending.png)
![Proposal Received](../../screenshots/assistant/proposal/proposal.png)

---

## 4 States

### State 1 — Pending Review
```
├── Clock icon (large, muted)
├── Text — "Pending Review"
└── Text — "Our specialist is reviewing your request…"
```

### State 2 — Under Review
```
├── Clock icon (blue tint)
├── Text — "Under Review"
└── Text — "The specialist is working on your proposal"
```

### State 3 — Proposal Ready (most complex)
```
├── View — Proposal card
│    ├── Text — admin message
│    ├── View — Details row
│    │    ├── CalendarDays icon + timeline weeks
│    │    └── DollarSign icon + price range
│    └── View — Action row
│         ├── Pressable — "Decline" (destructive)
│         └── Pressable — "Accept & View on Upwork" (primary)
│              └── ExternalLink icon
```

### State 4 — Accepted
```
├── CheckCircle icon (green)
├── Text — "Proposal Accepted"
├── Text — summary text
└── Pressable — "Open Upwork Contract" (primary, ExternalLink icon)
```

---

## Components
- `Clock`, `CheckCircle`, `XCircle`, `ExternalLink`, `CalendarDays`, `DollarSign` icons
- `ArrowLeft` — back navigation
- `Linking.openURL` — opens Upwork in browser on Accept

---

## Styles
| Element | Value |
|---|---|
| Background | `#F7F7F5` |
| State icon | Large (40–48px), color matches status |
| Proposal card | White bg, `BorderRadius.lg`, `elevation: 2`, `padding: 24` |
| Admin message | Noto Serif, italic |
| Detail chips | CalendarDays/DollarSign in primary color |
| Decline button | Outlined, destructive red text |
| Accept button | `#064E3B` fill with ExternalLink icon |

---

## Navigation
- ArrowLeft → back (to Assistants tab)
- "Accept" → marks accepted in DB + opens Upwork URL
- "Decline" → Alert confirm → marks declined in DB

---

## Design Notes
- Loading state shown while fetching consultation + proposal data
- State is determined by `consultation.status` + whether `proposal` record exists
- Upwork URL comes from admin when creating the proposal record
