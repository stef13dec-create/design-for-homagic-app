# Settings Screen

**Source:** `app/settings.tsx`  
**Purpose:** App settings, support links, legal documents, account management, and version info.

---

## Screenshot

![Screenshot](../../screenshots/profile/settings/screenshot.png)

---

## Layout

```
SafeAreaView
├── View — Header
│    ├── Pressable — ChevronLeft (back)
│    └── Text — "Settings"
└── ScrollView
     ├── View — Banner (ImageBackground with LinearGradient overlay)
     │    ├── [Pro badge if subscribed]
     │    └── App name / tagline overlay
     ├── View — Section: Account
     │    ├── Row — Edit Profile (User icon)
     │    ├── Row — Show User ID (Tag icon)
     │    └── Row — Delete My Information (Trash2 icon, destructive)
     ├── View — Section: Support
     │    ├── Row — Help Center (HelpCircle icon)
     │    ├── Row — Contact Us (MessageSquare icon)
     │    ├── Row — Rate the App (Star icon)
     │    └── Row — Share App (Share2 icon)
     ├── View — Section: Legal
     │    ├── Row — Terms of Service (FileText icon) → homagic.app/terms
     │    └── Row — Privacy Policy (Shield icon) → homagic.app/privacy
     ├── Row — Restore Purchase (RefreshCw icon)
     ├── Row — Redeem Code (Tag icon)
     └── Text — Version {appVersion} (centered, muted)
```

---

## Components
- `ImageBackground` + `LinearGradient` — banner with design image overlay
- `ChevronLeft`, `ChevronRight` icons on each row
- `User`, `Trash2`, `HelpCircle`, `MessageSquare`, `Star`, `Share2`, `FileText`, `Shield`, `RefreshCw`, `Tag`, `Lock`, `CheckCircle` icons
- `Linking.openURL` — external links (Terms, Privacy, Play Store)
- `Share.share()` — native share sheet for "Share App"
- `Alert` — delete account confirmation

---

## Styles
| Element | Value |
|---|---|
| Background | `#F7F7F5` |
| Banner | Full width image, `height: 140`, gradient overlay |
| Section header | Manrope Bold, 11px, uppercase, muted, `letterSpacing: 1` |
| Settings row | White bg, `BorderRadius.md`, `paddingVertical: 14`, icon + label + ChevronRight |
| Destructive row | Red text (`#DC2626`) for "Delete My Information" |
| Version text | Manrope 400, 12px, 40% opacity, centered |

---

## Navigation
- ChevronLeft → back (to Profile)
- Terms → `Linking.openURL('https://homagic.app/terms')`
- Privacy → `Linking.openURL('https://homagic.app/privacy')`
- Delete → Alert confirm → sign out → `/(auth)`

---

## Design Notes
- Banner uses a style asset image (`assets/styles/industrial.jpg`) as background
- `Constants.expoConfig?.version` for app version display
- Pro badge shown in banner if user is subscribed
