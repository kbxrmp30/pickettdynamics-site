# Pickett Enterprises Website

Portfolio site for Pickett Dynamics and its ventures, including the Hooked on Fishing community fishing program.

## Project Structure

```
/
├── index.html                        # Pickett Dynamics landing page (static)
├── HookedOnFishing/
│   └── index.html                    # Full single-page app (inline CSS + JS)
├── game.html                         # Hook the Fish canvas game
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
    └── woodworking/                  # Project photos (JPG/PNG) + EPOXY_POUR.mp4
```

## Tech Stack

- **Pure HTML/CSS/JS** — no build tools, no frameworks, no package.json
- **Firebase Realtime Database** — shared data across all users (sessions, RSVPs, leaderboard, gallery, videos)
- **Firebase Authentication** — email/password for admin login
- **EmailJS** — sends RSVP notification emails to matthew@pickettdynamics.com
- **Google Fonts** — Inter, Playfair Display (loaded via CDN)

## Hosting

- **GitHub Pages** at `https://www.pickettdynamics.com` (custom domain)
- Repo: `https://github.com/kbxrmp30/pickettdynamics-site`
- Branch: `main` — deploys automatically on push

## Firebase (hooked-on-fishing-648e6)

- **Database URL**: `https://hooked-on-fishing-648e6-default-rtdb.firebaseio.com`
- **Auth**: Email/Password — admin users are Matthew and his son
- **Rules**: `.read` open to all; `.write` requires `auth != null` except `rsvps` which is public write
- **Data paths**: `sessions/`, `rsvps/`, `leaderboard/`, `gallery/`, `videos/`
- API key in client HTML is intentional — Firebase security is enforced via rules, not key secrecy

## EmailJS

- **Public Key**: `xeNvEhsVhteGUuSUc`
- **Service ID**: `service_lvfh20a`
- **Template ID**: `template_fhd5nxm`
- Triggered on every new RSVP — sends to `matthew@pickettdynamics.com`
- Free tier: 200 emails/month

## Admin Access

- Triple-click the 🎣 fish emoji in the nav to open the login modal
- Authenticates via Firebase email/password
- Admin can: add/remove sessions, view attendee lists, copy attendee list to clipboard, add leaderboard entries, manage gallery photos and videos

## Conventions

- All styles are inline in `<style>` tags — no external CSS files
- CSS variables: `--ink`, `--forest`, `--lake`, `--sand`, `--cream`, `--muted` for theming
- Shadow/radius tokens: `--sh-s/m/l`, `--r-s/m/l/xl`
- Firebase data is cached in local JS variables (`_sessions`, `_rsvps`, etc.) and kept in sync via `onValue` listeners
- Optimistic UI updates: local cache updated immediately, Firebase write happens async
- Gallery seed photos are local files (`assets/images/photos/`); admin-uploaded photos are base64 in Firebase

## Web3Forms (Sign Designer)

- **Access Key**: in `woodworking-sign-designer.html` hidden input
- **Purpose**: Sign design quote requests with image attachment → `matt@pickettdynamics.com`
- Free tier, no backend needed

## Woodworking Section

- CSS variables use `--ww-` prefix throughout all woodworking pages
- All woodworking contact emails: `matt@pickettdynamics.com`
- Nav on all woodworking pages: Gallery · Coffee Tables · Custom Work · Sign Designer · Contact
- `woodworking-custom-work.html` form uses mailto (builds URL from form fields in JS)
- `woodworking-sign-designer.html` form uses Web3Forms fetch API with file upload

## Rentals Section

- Two properties: Laconia NH (Airbnb link wired) and Black Lake MI (Airbnb link wired)
- Contact: `matt@pickettdynamics.com` · Phone: `520-208-3424`
- Each property page has: hero photo, photo strip, Nearby cards (clickable links), From the Locals section, Good For section

## Future Work

- Gallery photo uploads via Cloudinary (replace base64-in-database approach)
- Woodworking: pricing page, lead time estimates, Stripe deposits
- Rentals: direct booking form (currently routes to Airbnb or email)
