# Snittet.dk

Beregn dit vægtede karaktergennemsnit ud fra karakterer og ECTS-point.
Et gratis værktøj til danske universitetsstuderende.

Live: https://snittet.dk

## Structure

Static single-page site — no build step, no dependencies.

| Path | Purpose |
|---|---|
| `index.html` | The entire page: markup, styles, and inline logic |
| `support.js` | Application script |
| `assets/` | Images, served with a one-year immutable cache |
| `_headers` | Cache-Control rules applied by Cloudflare |
| `wrangler.jsonc` | Worker config — serves the repo root as static assets |
| `.assetsignore` | Files kept out of the deployed site |

## Deploying

Pushes to `main` deploy automatically to the `snittet` Cloudflare Worker
via Workers Builds. There is no build command; `npx wrangler deploy`
uploads the files as-is.

To deploy by hand:

```sh
npx wrangler deploy
```

The `name` in `wrangler.jsonc` must stay `snittet` — Workers Builds
rejects the deploy if it does not match the connected Worker.
