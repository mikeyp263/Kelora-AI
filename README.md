# Kelora AI – Render setup (exact values) + connect `keloraai.com`

You are in the correct place: **Render → New Static Site → Configure**.

## Use these exact values on that screen

- **Service type:** Static Site ✅
- **Name:** `kelora-ai` (or any unique name)
- **Branch:** `main`
- **Root Directory:** *(leave empty)*
- **Build Command:** `:` *(recommended no-op; use this if Render UI won’t let the field be blank)*
  - If you see a `$`, that is usually just a prompt icon in the UI, not part of your command.
- **Publish Directory:** `.`
- **Environment Variables:** none needed for this simple static page

Then click **Create Static Site**.

---

## 1) Add a page so Render has content

Create `index.html` in repo root:

```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Kelora AI</title>
  </head>
  <body>
    <h1>Kelora AI is live ✅</h1>
  </body>
</html>
```

Commit + push:

```bash
git add index.html
git commit -m "Add initial static homepage"
git push
```

Render will auto-deploy from `main`.

---

## 2) Verify deployment

After deploy, open your Render URL, e.g.:
- `https://kelora-ai.onrender.com`

If you see your page, hosting is good.

---

## 3) Connect `keloraai.com`

In Render:
1. Open your Static Site.
2. Go to **Settings → Custom Domains**.
3. Add:
   - `keloraai.com`
   - `www.keloraai.com`

At your DNS provider:
- Set the records exactly to what Render shows in that Custom Domains panel.
- Commonly:
  - `www` → CNAME to your Render host (`your-service.onrender.com`)
  - `@` → apex record value/type Render provides (varies by DNS provider)

Wait for propagation, then click **Verify** in Render.

---

## 4) Which Render option should I use?

From your screenshot:
- **Static Sites** = correct choice for this repo/site.
- **Web Services** = only if running a backend server process.
- Others (Workers, Cron, Postgres, KV, Private Service) are not needed for this static site.

---

## 5) If it doesn't work

- Remove conflicting old `@` / `www` DNS records.
- Confirm your nameservers are pointing to the DNS provider where you changed records.
- Re-check Build Command is `:` (or blank if Render allows it) and Publish Directory is `.`.

If you want, next I can generate the `index.html` file and a cleaner landing page for you directly in this repo.
