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
├── woodworking-custom-work.html      # Custom project inquiry form (mailto)
├── woodworking-sign-designer.html    # AI sign design guide + quote form
├── woodworking-contact.html
│
├── game.html                         # Hook the Fish canvas game
│
└── assets/
    └── images/
        ├── rentals/                  # Rental property photos
        └── woodworking/             # Woodworking project photos
```

## Tech Stack

- **Pure HTML/CSS/JS** — no build tools, no frameworks, no package.json
- **localStorage** — HookedOnFishing data (sessions, RSVPs, leaderboard, gallery, videos) stored client-side per-browser
- **Web3Forms** — sign design quote form with file upload (Woodworking)
- **Google Fonts** — Inter, Playfair Display (CDN)

## Hosting

- **Cloudflare Workers** at `https://www.pickettdynamics.com` — Cloudflare handles DNS, routing, and TLS (not GitHub Pages directly)
- Repo: `https://github.com/kbxrmp30/pickettdynamics-site` — push to `main` deploys automatically
- Always Use HTTPS enabled in Cloudflare (SSL/TLS → Edge Certificates)

## Admin Access (HookedOnFishing)

Triple-click the 🎣 fish emoji in the nav → login modal → hardcoded admin password.

Admin can: add/edit sessions, view attendee RSVP lists, manage leaderboard, gallery, and videos.

## Conventions

- All styles inline in `<style>` tags — no external CSS files
- HookedOnFishing CSS vars: `--forest`, `--lake`, `--sand`, `--cream`, `--charcoal`, `--muted`
- Woodworking CSS vars: `--ww-` prefix throughout
- Woodworking contact email: `matt@pickettdynamics.com`
- HookedOnFishing contact email: `matthew@pickettdynamics.com`
