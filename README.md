# cinnamon-hr.com

Static rebuild of the PeopleOps/Cinnamon HR landing page (previously on Framer). Plain HTML/CSS, no build step, no runtime dependencies.

## Files

- `index.html` — the page
- `styles.css` — all styling
- `CNAME` — tells GitHub Pages which custom domain to serve this repo on

## Local preview

```
python3 -m http.server 8899
```
then open http://127.0.0.1:8899/index.html

## Deploying (GitHub Pages, free)

1. Push this repo to `main` on GitHub (already done if you're reading this from the repo).
2. On GitHub: **Settings → Pages** → under "Build and deployment", set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`. Save.
3. GitHub Pages will build at `https://<username>.github.io/peopleops-site/` and, because of the `CNAME` file, offer to serve it on `cinnamon-hr.com` once DNS is pointed (next step).

## Pointing cinnamon-hr.com at it (GoDaddy DNS)

In GoDaddy → your domain → DNS → Records, add/edit:

| Type  | Name | Value                  |
|-------|------|------------------------|
| A     | @    | 185.199.108.153        |
| A     | @    | 185.199.109.153        |
| A     | @    | 185.199.110.153        |
| A     | @    | 185.199.111.153        |
| CNAME | www  | `<username>.github.io` |

Remove any existing `@`/`www` A or CNAME records GoDaddy's builder added (its "parked page" or Website Builder records) so they don't conflict.

DNS can take anywhere from a few minutes to a few hours to propagate. Once it resolves, check the "Enforce HTTPS" box back on GitHub's Pages settings page (it only appears after DNS is verified) so the site serves over `https://`.

## Contact form

The form currently submits via a `mailto:` link (opens the visitor's own email client, addressed to `ana@cinnamon-hr.com`) — zero setup, zero cost, works anywhere a static site can be hosted. If you want submissions to land directly in your inbox without the visitor needing a configured mail client, swap in a free [Formspree](https://formspree.io) endpoint (50 submissions/month free): sign up, create a form, and replace the `action` attribute on the `<form>` in `index.html` with the endpoint they give you.
