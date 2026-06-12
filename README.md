# Powerhouse — TikTok LIVE Agency

Landing page for **Powerhouse**, a TikTok LIVE agency founded by Alondra Vogl.
Static site (plain HTML/CSS, no build step) hosted on **DigitalOcean App Platform**.

- Production: https://powerhouse-agency.com
- App spec: [`.do/app.yaml`](.do/app.yaml)

## Editing

Everything lives in three files:

| File | What it is |
|---|---|
| `index.html` | All page content (benefits, FAQ, apply section) |
| `styles.css` | Neon-on-navy theme |
| `404.html` | Not-found page |

The application button currently opens a prefilled email to
`apply@powerhouse-agency.com` — set up that mailbox (or change the address in
`index.html`, two places) and you're live.

## Deploying changes

The app uses a public-git source, so pushes do **not** auto-deploy.
After pushing to `main`, trigger a deployment:

```sh
git push
doctl apps list                          # find the app ID
doctl apps create-deployment <APP_ID>
```

## DNS (Namecheap)

`powerhouse-agency.com` is registered at Namecheap. The app expects:

| Type | Host | Value |
|---|---|---|
| ALIAS | `@` | the app's `*.ondigitalocean.app` hostname |
| CNAME | `www` | the app's `*.ondigitalocean.app` hostname |

SSL certificates are issued automatically by App Platform once DNS resolves.
