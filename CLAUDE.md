# Pickett Enterprises Website

Portfolio site for Pickett Dynamics and its ventures, including the Hooked on Fishing community fishing program.

## Project Structure

```
/
├── index.html                        # Pickett Dynamics landing page (static)
├── HookedOnFishing/
│   └── index.html                    # Full single-page app (inline CSS + JS)
├── game.html                         # Hook the Fish canvas game (root + mirrored in HookedOnFishing/)
│
├── rentals.html                      # Rentals overview (two properties)
├── rentals-laconia-nh.html           # Laconia, NH property detail page
├── rentals-black-lake-mi.html        # Black Lake, MI property detail page
│
├── woodworking.html                  # Woodworking section home
├── woodworking-gallery.html          # Filterable photo gallery (23 pieces)
├── woodworking-custom-coffee-tables.html
├── woodworking-custom-work.html      # Custom project inquiry (mailto form)
├── woodworking-sign-designer.html    # AI sign design guide + Web3Forms upload
├── woodworking-contact.html
│
└── assets/images/
    ├── rentals/                      # Rental property photos (JPG)
    └── woodworking/                  # Project photos (JPG/PNG)
```

## Tech Stack

- **Pure HTML/CSS/JS** — no build tools, no frameworks, no package.json
- **localStorage** — all HookedOnFishing data (sessions, RSVPs, leaderboard, gallery, videos) is stored client-side per-browser; data is not shared across users or devices
- **Web3Forms** — sign design quote form with file upload (Woodworking)
- **Google Fonts** — Inter, Playfair Display (loaded via CDN)

## Hosting

- **Cloudflare Workers** serves the site at `https://www.pickettdynamics.com` — DNS and routing are managed through Cloudflare, not GitHub Pages directly
- Repo: `https://github.com/kbxrmp30/pickettdynamics-site` — push to `main` triggers deployment
- DNS registered and managed in Cloudflare; Worker records for `pickettdynamics.com` and `www` point to the `pickettdynamics-site` worker (Proxied)
- **Always Use HTTPS** is enabled in Cloudflare SSL/TLS → Edge Certificates (redirects all HTTP → HTTPS)
- The `CNAME` file in the repo contains `www.pickettdynamics.com` (used by the Cloudflare Workers custom domain setup)
- GitHub Pages "Enforce HTTPS" does not apply — Cloudflare handles TLS termination

## Admin Access (HookedOnFishing)

- Triple-click the 🎣 fish emoji in the nav to open the login modal
- Authenticates via hardcoded password (`ADMIN_PW` constant in the script)
- Admin can: add/remove sessions, view attendee lists, add leaderboard entries, manage gallery photos and videos

## HookedOnFishing Data Model

All data lives in `localStorage` under these keys:
- `hof_sessions` — object keyed by `YYYY-MM-DD`, each value `{ time, location }`
- `hof_rsvps` — object keyed by date, each value an array of `{ id, name, email, phone, at }`
- `hof_my_rsvp` — per-device map of date → RSVP id (tracks this browser's RSVPs)
- `hof_leaderboard` — array of `{ id, name, size, fishType, photo, addedAt }`
- `hof_gallery` — array of `{ id, src (base64), cap, addedAt }`
- `hof_videos` — array of `{ id, ytId, title, desc, addedAt }`

Seed photos are local files in `HookedOnFishing/assets/images/photos/`. Admin-uploaded photos are stored as base64 in localStorage.

## Conventions

- All styles are inline in `<style>` tags — no external CSS files
- HookedOnFishing CSS variables: `--forest`, `--lake`, `--sand`, `--cream`, `--charcoal`, `--muted`
- Shadow/radius tokens: `--sh-s/m/l`, `--r-s/m/l/xl`
- Woodworking CSS variables use `--ww-` prefix throughout all woodworking pages

## Web3Forms (Sign Designer)

- **Access Key**: in `woodworking-sign-designer.html` hidden input
- **Purpose**: Sign design quote requests with image attachment → `matt@pickettdynamics.com`
- Free tier, no backend needed

## Woodworking Section

- All woodworking contact emails: `matt@pickettdynamics.com`
- Nav on all woodworking pages: Gallery · Coffee Tables · Custom Work · Sign Designer · Contact
- `woodworking-custom-work.html` form uses mailto (builds URL from form fields in JS)
- `woodworking-sign-designer.html` form uses Web3Forms fetch API with file upload

## Rentals Section

- Two properties: Laconia NH (Airbnb link wired) and Black Lake MI (Airbnb link wired)
- Contact: `matt@pickettdynamics.com` · Phone: `520-208-3424`
- Each property page has: hero photo, photo strip, Nearby cards (clickable links), From the Locals section, Good For section

## Future Work

- RSVP email notifications to matthew@pickettdynamics.com (EmailJS or similar — not yet implemented)
- Shared session/RSVP data across devices (Firebase or similar backend — currently localStorage only)
- Gallery photo uploads via Cloudinary (replace base64-in-localStorage approach)
- Woodworking: pricing page, lead time estimates, Stripe deposits
- Rentals: direct booking form (currently routes to Airbnb or email)
