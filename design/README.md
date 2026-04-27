# HOMAGIC ARCHITECT — Design Documentation

This folder contains the complete design reference for the HOMAGIC ARCHITECT app, organized for easy handoff to a product designer.

---

## How to Use This Folder

### Screenshots
Each screen has a dedicated folder under `screenshots/`. When you take a screenshot in Expo Go:
1. Find the matching folder (e.g. `screenshots/tabs/home/`)
2. Drop the image file inside and rename it to `screenshot.png`
3. The markdown doc for that screen (under `screens/`) will automatically display it

### Docs
Each screen has a corresponding markdown file under `screens/` with:
- Purpose of the screen
- Layout structure (header / body / footer)
- Every UI component used
- Colors, fonts, and spacing applied
- Navigation flow (what leads here, where it goes)
- Design notes and special behaviors

### Design System
See [design-system.md](design-system.md) for the full color palette, typography, spacing scale, and border radius system.

---

## App Navigation Map

```
Landing (auth/index)
 ├── Register (auth/register)
 │    └── → Home tabs
 ├── Login (auth/login)
 │    ├── → Home tabs
 │    └── Forgot Password (auth/forgot-password)
 └── → Home tabs (if already signed in)

Home Tabs (bottom navigation: Home · Explore · Saved · Assistants)
 │
 ├── [Home tab]
 │    ├── Interior Design → project/new
 │    ├── Exterior Design → project/exterior
 │    ├── Garden Design   → project/garden
 │    ├── Replace Objects → replace/index → replace/select → replace/finalize → replace/result
 │    └── Profile (top-right avatar) → profile
 │
 ├── [Explore tab]
 │    └── Tap style card  → explore/create (2-step wizard) → Saved tab
 │
 ├── [Saved tab]
 │    └── Tap result card → project/[id] (result screen)
 │
 └── [Assistants tab]
      ├── Specialist card → assistant/[type]
      │    └── "Request Consultation" → assistant/request → Assistants tab
      └── Active request  → assistant/proposal/[id]

Profile → profile
 ├── Settings → settings
 └── Upgrade / Manage → paywall
```

---

## Screen Index

### Authentication
| Screen | Doc | Screenshot |
|---|---|---|
| Landing | [screens/auth/landing.md](screens/auth/landing.md) | [screenshots/auth/landing/](screenshots/auth/landing/) |
| Login | [screens/auth/login.md](screens/auth/login.md) | [screenshots/auth/login/](screenshots/auth/login/) |
| Register | [screens/auth/register.md](screens/auth/register.md) | [screenshots/auth/register/](screenshots/auth/register/) |
| Forgot Password | [screens/auth/forgot-password.md](screens/auth/forgot-password.md) | [screenshots/auth/forgot-password/](screenshots/auth/forgot-password/) |

### Main Tabs
| Screen | Doc | Screenshot |
|---|---|---|
| Home | [screens/tabs/home.md](screens/tabs/home.md) | [screenshots/tabs/home/](screenshots/tabs/home/) |
| Explore | [screens/tabs/explore.md](screens/tabs/explore.md) | [screenshots/tabs/explore/](screenshots/tabs/explore/) |
| Saved | [screens/tabs/saved.md](screens/tabs/saved.md) | [screenshots/tabs/saved/](screenshots/tabs/saved/) |
| Assistants | [screens/tabs/assistants.md](screens/tabs/assistants.md) | [screenshots/tabs/assistants/](screenshots/tabs/assistants/) |

### Design Wizards
| Screen | Doc | Screenshot |
|---|---|---|
| Interior Wizard | [screens/project/new-interior.md](screens/project/new-interior.md) | [screenshots/project/new-interior/](screenshots/project/new-interior/) |
| Exterior Wizard | [screens/project/new-exterior.md](screens/project/new-exterior.md) | [screenshots/project/new-exterior/](screenshots/project/new-exterior/) |
| Garden Wizard | [screens/project/new-garden.md](screens/project/new-garden.md) | [screenshots/project/new-garden/) |
| Result Screen | [screens/project/result.md](screens/project/result.md) | [screenshots/project/result/](screenshots/project/result/) |
| Explore Create | [screens/explore/create.md](screens/explore/create.md) | [screenshots/explore/create/](screenshots/explore/create/) |

### Replace Objects
| Screen | Doc | Screenshot |
|---|---|---|
| Draw Region | [screens/replace/select.md](screens/replace/select.md) | [screenshots/replace/select/](screenshots/replace/select/) |
| Finalize | [screens/replace/finalize.md](screens/replace/finalize.md) | [screenshots/replace/finalize/](screenshots/replace/finalize/) |
| Result | [screens/replace/result.md](screens/replace/result.md) | [screenshots/replace/result/](screenshots/replace/result/) |

### Assistants
| Screen | Doc | Screenshot |
|---|---|---|
| Specialist Detail | [screens/assistant/specialist-detail.md](screens/assistant/specialist-detail.md) | [screenshots/assistant/specialist-detail/](screenshots/assistant/specialist-detail/) |
| Request Form | [screens/assistant/request.md](screens/assistant/request.md) | [screenshots/assistant/request/](screenshots/assistant/request/) |
| Proposal View | [screens/assistant/proposal.md](screens/assistant/proposal.md) | [screenshots/assistant/proposal/](screenshots/assistant/proposal/) |

### Profile & Account
| Screen | Doc | Screenshot |
|---|---|---|
| Profile | [screens/profile/profile.md](screens/profile/profile.md) | [screenshots/profile/profile/](screenshots/profile/profile/) |
| Settings | [screens/profile/settings.md](screens/profile/settings.md) | [screenshots/profile/settings/](screenshots/profile/settings/) |
| Paywall | [screens/profile/paywall.md](screens/profile/paywall.md) | [screenshots/profile/paywall/](screenshots/profile/paywall/) |
