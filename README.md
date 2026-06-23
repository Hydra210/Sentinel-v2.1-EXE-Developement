# EXE Development — Frontend

A multi-page SaaS frontend for EXE Development and Sentinel.

## File Structure

```
exe-development/
├── index.html                  ← EXE homepage (main entry point)
│
├── auth/
│   ├── signup.html             ← EXE account signup
│   └── login.html              ← EXE account login
│
├── sentinel/
│   ├── index.html              ← Sentinel product page (features + pricing)
│   ├── plans.html              ← Standalone plan picker
│   └── app.html                ← Sentinel dashboard (post-login)
│
└── legal/
    ├── terms.html              ← Terms of Service
    ├── privacy.html            ← Privacy Policy
    └── contact.html            ← Contact form
```

## Pages Overview

### EXE Homepage (`index.html`)
- Hero section with EXE branding + future expansion messaging
- Sentinel highlight with UI preview mockup
- Partner section for Error Dev Group
- Footer with legal links

### Auth (`auth/`)
- **Signup** — creates an EXE account (any values accepted in mock mode), redirects to plan selection
- **Login** — authenticates via EXE account (no PINs), redirects to Sentinel app

### Sentinel Product Page (`sentinel/index.html`)
- Hero clearly marking Sentinel as a **paid** product (no free tier)
- Features grid
- Pricing section with 3 paid plans: Starter ($9), Pro ($24), Enterprise ($79)
- Unauthenticated users clicking a plan → redirected to signup

### Sentinel Plans (`sentinel/plans.html`)
- Standalone plan picker used after signup or as a standalone page

### Sentinel App (`sentinel/app.html`)
- Full dashboard with tabs: Overview, Queue, Rules, Audit Logs, Settings, Billing, Admin (Enterprise only)
- Auth-guarded: redirects to login if no EXE session found
- No PIN system — all identity via EXE account stored in sessionStorage
- Settings shows EXE account details (no PIN fields anywhere)
- Billing shows active Sentinel plan + invoice history
- Admin tab only visible for Enterprise plan holders

## Mock Auth Flow

1. User visits `index.html` → clicks "Get started"
2. Signs up at `auth/signup.html` → fills any values → clicks "Create account"
3. Redirected to `sentinel/plans.html` to pick a paid plan
4. Picks a plan → redirected to `sentinel/app.html`
5. Dashboard loads with their username + plan shown in topbar

Session is stored in `sessionStorage` (clears on tab close).

## Design Notes

- **EXE colorway**: Black `#080808`, white accent, noise texture, grid backgrounds, Syne/Outfit/DM Mono fonts
- **Sentinel colorway**: Same base + red `#ff3b3b` accents, red-tinted borders, red CTAs
- All pages are responsive
- No free plan appears anywhere — Sentinel is paid-only throughout
- PIN-based profiles are completely absent from all pages
