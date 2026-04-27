# HOMAGIC ARCHITECT — Design System

Source of truth: [`constants/theme.ts`](../constants/theme.ts)

---

## Brand Identity

HOMAGIC ARCHITECT is a premium AI home design app. The visual language is **luxury and calm** — dark forest green as the primary brand color, warm off-white backgrounds, gold accents, and a serif + sans-serif typography pairing that feels editorial and trustworthy.

---

## Color Palette

| Token | Hex | Usage |
|---|---|---|
| `primary` | `#064E3B` | Buttons, active states, headers, icons, borders, brand text |
| `secondary` | `#D4AF37` | Gold accent — Pro badge, specialist icons, premium highlights |
| `tertiary` | `#2C2C2C` | Body text, labels, secondary content |
| `neutral` | `#F7F7F5` | Screen background (warm off-white) |
| `white` | `#FFFFFF` | Cards, modals, input fields, button text |
| `error` | `#DC2626` | Validation errors, failed states |

### Extended / In-Code Colors
These appear inline in components but are part of the visual system:

| Value | Usage |
|---|---|
| `#003526` | Slightly darker primary variant (header title, filter chip active) |
| `#1a1c1b` | Card titles on home feed |
| `#707975` | Muted subtitles |
| `#e8e8e6` | Inactive filter chip background |
| `#eeeeec` | Avatar button background |
| `#fef3c7` | Amber warning banner background |
| `#92400e` | Amber warning text |
| `#166534` | Success text (reset password confirmation) |
| `#F0FDF4` | Success container background |
| `#BBF7D0` | Success container border |
| `rgba(0,0,0,0.68)` | Gradient overlay on Explore style cards |
| `rgba(0,0,0,0.93)` | Full-screen preview modal background |

---

## Typography

| Token | Font | Weight | Usage |
|---|---|---|---|
| `serif` | Noto Serif | 400 Regular | Body serif text, taglines |
| `serifBold` | Noto Serif | 700 Bold | Section headings, screen titles, card names |
| `sans` | Manrope | 400 Regular | Body copy, labels, subtitles, metadata |
| `sansMedium` | Manrope | 500 Medium | Sub-labels, chip text, row titles |
| `sansBold` | Manrope | 700 Bold | Button text, emphasized labels, counts |

### Type Scale (key sizes used in-app)
| Size | Usage |
|---|---|
| 10–11px | Micro labels (room type badge, style count, card mood text) |
| 12–13px | Supporting metadata, subtitles, footer notes |
| 14px | Body copy, link text, secondary labels |
| 16px | Form labels, button text, section subheadlines |
| 18px | Screen subheadings, primary button text on landing |
| 22px | Card headings on home feed |
| 26–28px | Tab screen main headings (Explore, Saved, Assistants) |
| 28px | Auth headlines ("HOMAGIC ARCHITECT", "Reset Password") |

---

## Spacing Scale

| Token | Value | Usage |
|---|---|---|
| `xs` | 4px | Tight internal gaps (card body gap, moodboard gap) |
| `sm` | 8px | Small gaps between related elements |
| `md` | 16px | Standard section padding, form field gaps |
| `lg` | 24px | Large section padding, horizontal screen padding |
| `xl` | 32px | Extra large section gaps |
| `xxl` | 48px | Bottom scroll padding, major section separators |

---

## Border Radius

| Token | Value | Usage |
|---|---|---|
| `sm` | 8px | Small elements (filter chips, style count tags) |
| `md` | 12px | Input fields, buttons, cards in forms |
| `lg` | 16px | Specialist cards, feed cards |
| `xl` | 24px | Main CTA buttons on landing screen |
| `full` | 9999px | Pill buttons, avatar circles, credits pill, "TRY IT!" button |

---

## Shadows / Elevation

Cards use subtle shadows for depth:
- **Feed cards (Home):** `elevation: 2`, shadow opacity `0.1`, radius `8`
- **Specialist cards:** `elevation: 3`, shadow opacity `0.06`, radius `8`
- **"TRY IT!" button:** `elevation: 4`, shadow opacity `0.25`, radius `4`
- **Active state:** No shadow change, opacity reduces to `0.85–0.9` on press

---

## Icon Library

All icons are from **lucide-react-native**.

| Icon | Usage |
|---|---|
| `Zap` | Credits pill, upgrade CTA |
| `User` | Avatar button on Home, Profile screen |
| `AlertTriangle` | Usage warning banner |
| `ChevronLeft` / `ArrowLeft` | Back navigation |
| `X` | Close modals, dismiss |
| `Eye` / `EyeOff` | Password visibility toggle |
| `Trash2` | Delete saved designs |
| `Maximize2` | Expand to full-screen preview |
| `Sofa` | Interior specialist |
| `Building2` | Exterior specialist |
| `Leaf` | Garden specialist |
| `ChevronRight` | List row navigation arrow |
| `Clock` | Pending consultation status |
| `CheckCircle` | Accepted consultation status |
| `MessageSquare` | Proposal ready status |
| `LogOut` | Sign out action |
| `RotateCcw` | Restore purchases |
| `Settings` | Settings navigation |
| `Lock` | Pro-gate indicator |
| `Star` | Rating / benefit highlight |
| `Camera` | Upload reference photo |
| `ArrowLeft`, `RefreshCw` | Replace flow navigation |
| `Minus` / `Plus` | Zoom controls in full-screen view |

---

## Animation

- **Moti** — used for entrance animations on Landing screen (logo, tagline, buttons fade+slide in sequence with delays)
- **Reanimated v4** — used for:
  - Before/After slider drag handle
  - FAQ accordion open/close (opacity + height interpolation + chevron rotation)
  - Zoom + pan in full-screen image modals
- **Interval-based** — Home screen moodboard thumbnails rotate every 4 seconds

---

## Key UI Patterns

### Buttons
| Style | Appearance | Usage |
|---|---|---|
| Primary | `#064E3B` fill, white text, `BorderRadius.md` | Main actions (Sign In, Generate, Submit) |
| Secondary / Ghost | White fill, `#064E3B` border + text | Google sign-in, secondary CTAs |
| Pill CTA | `#064E3B` fill, `BorderRadius.full`, `letterSpacing: 1.5` uppercase | "TRY IT!", credits pill |
| Outlined | `borderWidth: 1.5`, `borderColor: primary` | Landing "Sign In" secondary button |
| Destructive | `error` color | Delete account, decline proposal |

### Cards
| Type | Radius | Background | Shadow |
|---|---|---|---|
| Home feed card | 16px | White | `elevation: 2` |
| Specialist card | 16px | White + 4px green left accent | `elevation: 3` |
| Style card (Explore) | 12px | Image + gradient overlay | None |
| Saved design card | 12px top, square bottom | Image thumbnail + white body | None |
| Upgrade card | 12px | Primary green | None |

### Chips / Pills
- **Category chips (Home/Explore):** Pill shape (`BorderRadius.full`), active = `#003526` fill + white text
- **Group chips (Explore):** Smaller, neutral background, active = primary fill
- **Status pills (Assistants):** Dynamic color based on consultation status

### Input Fields
- White background, `BorderRadius.md` (12px), primary-colored label above
- Error state: red border + error text below
- `rightElement` slot for Eye icon on password fields

### Modals
- Full-screen preview: near-black background `rgba(0,0,0,0.93)`, white X close button top-right
- Bottom sheet picker: triggered by photo upload area tap

---

## Navigation Structure

The app uses **Expo Router v4** with:
- `(auth)` group — unauthenticated screens (no tab bar)
- `(tabs)` group — authenticated main navigation (bottom tab bar with 4 tabs)
- Modal screens — pushed on top of tabs (profile, paywall, settings, project wizards, replace flow, assistant flow)
