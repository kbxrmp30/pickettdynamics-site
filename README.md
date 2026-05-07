# Pickett Enterprises Website

Portfolio site for Pickett Dynamics and its ventures — hosted at [pickettdynamics.com](https://www.pickettdynamics.com).

## Ventures

| Venture | Status | Description |
|---|---|---|
| **Hooked on Fishing** | Live | Community fishing program — sessions, RSVPs, leaderboard, gallery |
| **Rentals** | Live | Two vacation rental properties (Laconia NH, Black Lake MI) |
| **Woodworking** | Live | Custom woodworking and CNC-crafted pieces, AI Sign Designer |

## Project Structure

```
/
├── index.html                        # Pickett Dynamics landing page
│
├── HookedOnFishing/
│   └── index.html                    # Full single-page app
│
├── rentals.html                      # Rentals overview
├── rentals-laconia-nh.html           # Laconia, NH property page
├── rentals-black-lake-mi.html        # Black Lake, MI property page
│
├── woodworking.html                  # Woodworking home
├── woodworking-gallery.html          # Photo gallery (23 pieces, filterable)
├── woodworking-custom-coffee-tables.html
├── woodworking-custom-work.html      # Custom project inquiry form
├── woodworking-sign-designer.html    # AI sign design guide + quote form
├── woodworking-contact.html
│
├── game.html                         # Hook the Fish canvas game
│
└── assets/
    └── images/
        ├── rentals/                  # Rental property photos
        └── woodworking/              # Woodworking project photos + EPOXY_POUR.mp4
```

## Tech Stack

- **Pure HTML/CSS/JS** — no build tools, no frameworks, no package.json
- **Firebase Realtime Database** — sessions, RSVPs, leaderboard, gallery, videos (HookedOnFishing)
- **Firebase Authentication** — email/password admin login (HookedOnFishing)
- **EmailJS** — RSVP notification emails (HookedOnFishing)
- **Web3Forms** — sign design quote form with file upload (Woodworking)
- **Google Fonts** — Inter, Playfair Display (CDN)

## Hosting

- **GitHub Pages** at `https://www.pickettdynamics.com`
- Repo: `https://github.com/kbxrmp30/pickettdynamics-site`
- Branch: `main` — deploys automatically on push

## Third-Party Services

### Firebase (hooked-on-fishing-648e6)
- DB URL: `https://hooked-on-fishing-648e6-default-rtdb.firebaseio.com`
- Rules: `.read` open; `.write` requires auth except `rsvps` (public write)
- API key in client HTML is intentional — security enforced via rules

### EmailJS
- Public Key: `xeNvEhsVhteGUuSUc` · Service: `service_lvfh20a` · Template: `template_fhd5nxm`
- Sends to `matthew@pickettdynamics.com` on new RSVPs · Free tier: 200/month

### Web3Forms
- Sign Designer quote form — sends to `matt@pickettdynamics.com` with image attachment
- Free tier: unlimited submissions

## Admin Access (HookedOnFishing)

Triple-click the 🎣 fish emoji in the nav → login modal → Firebase email/password auth.

Admin can: add/edit sessions, view/copy attendee lists, manage leaderboard, gallery, and videos.

## Conventions

- All styles inline in `<style>` tags — no external CSS files
- HookedOnFishing CSS vars: `--ink`, `--forest`, `--lake`, `--sand`, `--cream`, `--muted`
- Woodworking CSS vars: `--ww-espresso`, `--ww-walnut`, `--ww-brass`, `--ww-parchment`, `--ww-cream`
- Rentals CSS vars: `--primary`, `--accent`, `--sand`, `--cream`
- Firebase data cached in local JS vars and synced via `onValue` listeners
- Woodworking contact email: `matt@pickettdynamics.com`
