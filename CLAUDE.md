# luizfelipefb.com redesign (handoff from a claude.ai chat)

## Goal
Replace Luiz Felipe's old personal site (Nuxt 2 + Vuetify 2, client-rendered, repo `github.com/luizfelipefb/luizfelipefb.com`, hosted on Firebase/Cloudflare) with a modern, simple static site built in Astro. He no longer wants Vue. Content is personal only: bio, skills, links. No user interaction.

## Decisions already made
- Framework: Astro (pinned `astro@7.4.2`), static output, no UI framework, no analytics (old `UA-` Google Analytics is dead).
- Visual direction: "terminal dark". Page is one screen that types a short shell session on load (`whoami`, `cat about.md`, `ls skills/`, `cat links.txt`).
- Tokens: bg `#0E1116`, text `#E6EDF3`, muted `#8B98A5`, accent mint `#3DDC97`, rule `#232A33`. Light mode via toggle (`data-theme="light"`: bg `#F6F8FA`, text `#1F2328`, accent `#0B7A4B`). Dark is the default regardless of OS setting.
- Type: JetBrains Mono (Google Fonts) with system mono fallback.
- Dropped on purpose: Medium publications carousel, Facebook link, old section layout, Vuetify.
- Motion: only the one load-time typing sequence; fully disabled under `prefers-reduced-motion`.
- Identity: "pin" (a.k.a. pi + n, site was once 3.14n.dev). Footer keeps the "πn" nod.

## Current state
- `src/pages/index.astro` holds everything (content arrays at the top, CSS at the bottom).
- `npm run build` outputs a single self-contained `dist/index.html` (CSS inlined).
- Bio text and social links were drafted by Claude from his old site and GitHub profile. He has not yet reviewed them.

## Next steps
1. Review/edit bio, skills, and links in `src/pages/index.astro`.
2. Replace the Nuxt 2 code in the existing repo with this project (new branch, e.g. `astro-redesign`; the old repo has 8 open PRs and a Firebase deploy workflow in `.github/workflows/ci.yml`).
3. Decide hosting: Cloudflare Pages (build `npm run build`, output `dist`) or keep Firebase and update `firebase.json` to serve `dist`.
4. Add OG image, `robots.txt`, and a sitemap if wanted.
5. Check contrast, keyboard focus, and mobile in a real browser.

## Notes
- Never commit tokens/secrets (old workflow used `FIREBASE_TOKEN` and `FIREBASE_PROJECT` secrets).
- Keep it simple: one page, minimal dependencies.
