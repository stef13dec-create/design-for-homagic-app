# Forgot Password Screen

**Source:** `app/(auth)/forgot-password.tsx`  
**Purpose:** User enters email to receive a password reset link.

---

## Screenshot

![Screenshot](../../screenshots/auth/forgot-password/screenshot.png)

---

## Layout

```
SafeAreaView
└── KeyboardAvoidingView
    └── ScrollView (padding: 24, gap: 24)
        ├── Pressable — "← Back to Sign In"
        ├── Text — "Reset\nPassword" (serif bold, 2-line headline)
        └── [State A — Form]
             ├── Text — description paragraph
             ├── ErrorBanner (conditional)
             ├── InputField — Email
             └── Pressable — "Send Reset Email" (primary button)
        OR
        └── [State B — Success]
             └── View (green card, rounded)
                  ├── Text — "Check your inbox" (bold)
                  └── Text — "We've sent a password reset link to {email}"
```

---

## Components
- `InputField` — single email field with validation
- `ErrorBanner` — API error display
- `ActivityIndicator` — loading state on send button
- Success card: `#F0FDF4` background, `#BBF7D0` border, `#166534` text

---

## Styles
| Element | Value |
|---|---|
| Background | `#F7F7F5` |
| Headline | Noto Serif Bold, 28px, `#064E3B`, `lineHeight: 36` |
| Description | Manrope 400, 16px, `#2C2C2C` at 70% opacity, `lineHeight: 24` |
| Send button | `#064E3B`, `BorderRadius.md`, `paddingVertical: 16` |
| Success card | `#F0FDF4` bg, `#BBF7D0` border, `BorderRadius.md`, `padding: 24` |
| Success title | Manrope Bold, 18px, `#166534` |
| Success body | Manrope 400, 14px, `#166534`, `lineHeight: 22` |

---

## Navigation
- "← Back to Sign In" → `/(auth)/login`
- Success state: stays on screen (no automatic redirect)

---

## Design Notes
- Two UI states controlled by a single `sent` boolean
- Form replaces completely with the green success card after email is sent
- Deep link redirect URL: `homagic://reset-password`
