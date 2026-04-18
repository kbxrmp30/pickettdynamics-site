# Pickett Enterprises Website

Project folder for the Pickett Enterprises website.

## Folder structure

```
Pickett Enterprises Website/
├── src/                  Source code for the website
│   ├── pages/            HTML pages (or framework route files)
│   ├── styles/           CSS / SCSS stylesheets
│   ├── scripts/          JavaScript / TypeScript
│   ├── components/       Reusable UI components
│   └── assets/           Assets imported by source code (compiled output)
│
├── assets/               Master source files for media (pre-optimization)
│   ├── images/
│   │   ├── logos/        Logo files (SVG, PNG, variants)
│   │   ├── photos/       Photography (originals, high-res)
│   │   ├── icons/        Icon set
│   │   └── social/       Social media banners, OG images
│   ├── fonts/            Font files and licenses
│   └── videos/           Video assets
│
├── content/              Written content, drafts, and copy
│   ├── copy/             Page copy drafts (home, about, services, contact)
│   ├── blog/             Blog post drafts
│   ├── legal/            Privacy policy, terms, disclaimers
│   └── emails/           Email templates and marketing copy
│
├── design/               Design files and visual planning
│   ├── mockups/          Figma exports, high-fidelity mockups
│   ├── wireframes/       Low-fidelity layouts and sketches
│   ├── brand/            Brand guide, color palette, typography
│   └── inspiration/      Reference sites and moodboard
│
├── docs/                 Project documentation and planning
│   ├── planning/         Sitemap, user flows, project plan
│   ├── seo/              Keyword research, meta descriptions, SEO plan
│   ├── credentials/      Hosting, domain, CMS logins (keep secure!)
│   └── meeting-notes/    Notes from client/team meetings
│
└── build/                Compiled/production output (typically gitignored)
```

## Getting started

1. Decide on your tech stack (static HTML, WordPress, Next.js, etc.) and add the appropriate project files into `src/`.
2. Drop master logo and brand files into `assets/images/logos/` and `design/brand/`.
3. Draft page copy in `content/copy/` before building pages.
4. Keep `docs/credentials/` out of any public repo — add it to `.gitignore` if you use Git.

## Notes

- `assets/` holds originals; `src/assets/` holds optimized copies used by the site.
- `build/` is for generated output and can be safely deleted and regenerated.
