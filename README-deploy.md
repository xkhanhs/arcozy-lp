# Purisia — Deploy guide (Cloudflare Pages)

Static site for **purisia.com**. This is a **separate** Cloudflare Pages project named
`purisia` — it has nothing to do with `p.arcozy.com` / the `marketing-plan` project.

## Structure

```text
purisia/
  dist/                     # deploy output (Cloudflare serves this folder)
    index.html              # homepage — beauty/sleep review site
    lp/
      tapeher/index.html    # money page — "Best mouth tape" comparison (TapeHer #1)
  README-deploy.md          # this file
```

- Homepage:   https://purisia.com/
- Money page: https://purisia.com/tapeher/

## Deploy

```bash
cd "/Users/binhbui/Documents/Marketing Plan"
npx wrangler pages deploy purisia/dist --project-name purisia --commit-message "deploy" --commit-dirty=true
```

Notes:
- First deploy: if the project doesn't exist yet, wrangler will prompt to create it
  (choose production branch `main`).
- Always pass `--commit-message "deploy"` (ASCII). Wrangler otherwise forwards the latest
  git commit message to the Cloudflare API, which rejects non-ASCII (Vietnamese) strings
  with error `8000111 Invalid commit message`.
- Use `wrangler pages deploy` (Pages) — **not** `wrangler deploy` (that's Workers).

## Custom domain (purisia.com)

After the first successful deploy, attach the domain in the Cloudflare dashboard:

1. Dashboard → **Workers & Pages** → **purisia** → **Custom domains** → **Set up a domain**.
2. Enter `purisia.com` (and optionally `www.purisia.com`). Cloudflare adds the CNAME/route
   automatically if the zone is on your account.
3. Wait for SSL (Active). Then both URLs above resolve over HTTPS.

## Updating content

Edit the HTML files under `purisia/dist/` directly (they are fully self-contained — inline
CSS, no build step, no external fonts/JS), then re-run the deploy command above.

## Affiliate / tracking notes

- The only affiliate link on the money page is `https://tapeher.com/?ref=serena1` with UTM
  params per CTA position (`utm_content=hero|comparison|review|final|sticky`).
- Competitor products in the comparison table are intentionally **not** linked.
- All affiliate links use `rel="sponsored noopener"` and `target="_blank"`.
