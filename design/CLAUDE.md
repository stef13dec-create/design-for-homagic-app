# CLAUDE.md — Home Magic (Homagic Architect) Project Memory

This file is auto-read at the start of every Cowork session. It gives Claude full context about this project without needing to re-read all files from scratch.

---

## App Overview

**App name:** Homagic Architect (marketed as "Home Magic")  
**Platform:** Android (React Native / Expo Router v4)  
**Purpose:** AI-powered home design app — users upload photos of their spaces and the app generates redesigns using AI image generation models  
**Owner:** Mircea (danimadimircea@gmail.com)

---

## Tech Stack

- React Native + Expo Router v4
- Moti (entrance animations), Reanimated v4 (drag, zoom, accordion)
- expo-image, lucide-react-native icons
- AI image/design generation via API

---

## Design System (source: design-system.md)

### Colors
| Token | Hex | Usage |
|---|---|---|
| `primary` | `#064E3B` | Buttons, active states, headers, brand |
| `secondary` | `#D4AF37` | Gold — Pro badge, premium highlights |
| `tertiary` | `#2C2C2C` | Body text, labels |
| `neutral` | `#F7F7F5` | Screen background (warm off-white) |
| `white` | `#FFFFFF` | Cards, inputs, modals |
| `error` | `#DC2626` | Validation errors |

### Typography
- **Serif:** Noto Serif (400 / 700) — headings, screen titles
- **Sans:** Manrope (400 / 500 / 700) — body, labels, buttons

### Spacing: xs=4, sm=8, md=16, lg=24, xl=32, xxl=48
### Border Radius: sm=8, md=12, lg=16, xl=24, full=9999

---

## Navigation Structure

```
Landing → Register / Login → Home Tabs

Home Tabs (4 tabs: Home · Explore · Assistants · Saved)
├── Home → Interior / Exterior / Garden wizards → Result
│         → Replace Objects flow (Select → Finalize → Result)
│         → Profile → Settings / Paywall
├── Explore → Style card → Explore Create wizard → Saved
├── Assistants → Specialist Detail → Request Consultation → Proposal
└── Saved → Result screen
```

---

## Screen Inventory (25 screens total)

### Auth (4)
- Landing
- Login
- Register
- Forgot Password

### Main Tabs (4)
- Home
- Explore
- Assistants
- Saved

### Design Wizards (5)
- Interior Wizard (new-interior)
- Exterior Wizard (new-exterior)
- Garden Wizard (new-garden)
- Result screen
- Explore Create (2-step wizard)

### Replace Objects Flow (3)
- Select / Draw Region
- Finalize
- Result

### Assistants Flow (3)
- Specialist Detail
- Request Consultation
- Proposal View

### Profile & Account (3)
- Profile
- Settings
- Paywall

---

## Analysis Findings (April 2026)

### Strengths
- Clear brand identity (green + gold, serif + sans)
- Logical navigation structure
- Explore tab is the strongest screen (full-bleed cards, gradient overlays)
- Saved tab grid layout is clean and scannable

### Issues Identified
- **Landing:** Too much empty space, buttons feel lonely, needs a hero visual
- **Login/Register:** Logo repetition wastes vertical space; inputs lack contrast (white on off-white)
- **Home:** Header brand title is small/weak; moodboard thumbnails inside cards are noisy; no clear visual hierarchy between header → chips → feed
- **Explore:** Dual filter layer (category chips + group sub-chips) is confusing
- **Assistants:** Cards feel sparse/list-like, no imagery, feels abstract
- **Saved:** "Untitled Project" on all cards is a UX gap; "View Details" button duplicates card tap
- **Profile:** "Sign Out" in red is jarring (red = error in design system, not destructive action)
- **Paywall:** Free and Pro cards have equal visual weight; Pro should dominate
- **Specialist Detail:** Needs a hero visual to make specialist feel human/inviting
- **Request Consultation:** Dense, needs more breathing room between sections

---

## Redesign Roadmap & Status

| # | Screen | Group | Status |
|---|---|---|---|
| 1 | Landing | Auth / First impressions | ⬜ To Do |
| 2 | Login | Auth / First impressions | ⬜ To Do |
| 3 | Register | Auth / First impressions | ⬜ To Do |
| 4 | Forgot Password | Auth | ⬜ To Do |
| 5 | Home Tab | Core experience | ⬜ To Do |
| 6 | Explore Tab | Core experience | ⬜ To Do |
| 7 | Saved Tab | Core experience | ⬜ To Do |
| 8 | Assistants Tab | Core experience | ⬜ To Do |
| 9 | Specialist Detail | Assistants flow | ⬜ To Do |
| 10 | Request Consultation | Assistants flow | ⬜ To Do |
| 11 | Proposal View | Assistants flow | ⬜ To Do |
| 12 | Profile | Account | ⬜ To Do |
| 13 | Settings | Account | ⬜ To Do |
| 14 | Paywall | Account | ⬜ To Do |
| 15 | Interior Wizard | Design wizards | ⬜ To Do |
| 16 | Exterior Wizard | Design wizards | ⬜ To Do |
| 17 | Garden Wizard | Design wizards | ⬜ To Do |
| 18 | Result Screen | Design wizards | ⬜ To Do |
| 19 | Explore Create | Design wizards | ⬜ To Do |
| 20 | Replace – Select | Replace flow | ⬜ To Do |
| 21 | Replace – Finalize | Replace flow | ⬜ To Do |
| 22 | Replace – Result | Replace flow | ⬜ To Do |

---

## Session Log

### Session 1 — April 27, 2026
- Full folder analysis completed
- All screenshots reviewed
- Design system documented
- Issues identified per screen
- Redesign roadmap agreed
- CLAUDE.md created
- Redesign not yet started
