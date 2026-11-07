# luizfelipefb.com

Personal site of Luiz Felipe Fontes Botelho ("pin"). One static page styled as a terminal: on load it types a short shell session (`whoami`, `cat about.md`, `ls skills/`, `cat links.txt`), and a button switches between dark (default) and light mode.

Built with [Astro](https://astro.build). No UI framework, no analytics, no client-side dependencies.

## Develop

Requires Node.js 24 (pinned in `.node-version`).

```bash
npm install
npm run dev       # dev server at http://localhost:4321
npm run build     # static build to dist/ (one self-contained index.html)
npm run preview   # serve the production build locally
```

## Layout

| Path | What it is |
| --- | --- |
| `src/pages/index.astro` | The whole page: content arrays and markup at the top, CSS at the bottom |
| `public/favicon.svg` | Favicon (π + n, drawn as paths so it doesn't depend on installed fonts) |
| `astro.config.mjs` | Astro config: site URL, stylesheets inlined into the HTML |

## Editing content

- **Skills** are grouped by the problem they solve. Each group in the `skills` array in the frontmatter of `index.astro` has a `name`, a one-line `about` and a list of `skills`.
- **Links** are the `links` array in the same place.
- **Bio** is the paragraph under `cat about.md`.
- **Typing animation:** each command line has `--n`, the number of characters in the command. If you rename a command, update `--n` to match or the text will be clipped or padded. `--d` is when typing starts, `--t` is how long it takes, and `--o` is when the output appears.

## Design notes

- Colors are CSS variables in `:root` (dark) and `:root[data-theme='light']`. Dark is the default regardless of the OS setting. The choice is saved in `localStorage`.
- The only animation is the load-time typing sequence and the blinking cursor. Both are disabled under `prefers-reduced-motion`.
- Font is JetBrains Mono from Google Fonts, falling back to the system monospace font.
