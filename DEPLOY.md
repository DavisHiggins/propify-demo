# Propify Demo — Railway Deployment

## What changed in your code
**Nothing.** Your `propify_demo_app.py` is untouched. We're just adding Railway config files alongside it.

## Files to add to your demo repo

| File | Purpose |
|---|---|
| `Procfile` | Tells Railway how to start the app |
| `railway.json` | Build config, healthcheck, restart policy (no sleeping) |
| `runtime.txt` | Pins Python to 3.11 |
| `requirements.txt` | Replace your existing one with this pinned version |
| `.streamlit/config.toml` | Headless mode for Railway |
| `.gitignore` | Standard hygiene |

## Deployment steps

### 1. Add files to your existing demo GitHub repo
Drop all these files into the root of your `propify-demo` (or whatever you named it) GitHub repo, **next to** `propify_demo_app.py`. Replace the existing `requirements.txt` with the pinned version.

```bash
git add Procfile railway.json runtime.txt requirements.txt .streamlit/config.toml .gitignore
git commit -m "Add Railway deployment config"
git push
```

### 2. Create the Railway project
1. Go to https://railway.app → sign in with GitHub
2. **New Project** → **Deploy from GitHub repo** → pick your demo repo
3. Railway auto-detects Python and starts building (~2 min)

### 3. No environment variables needed
The demo has no Supabase, no auth, no API keys. Nothing to configure.

### 4. Generate a public domain
Railway dashboard → **Settings** → **Networking** → **Generate Domain**

You'll get something like `propify-demo-production.up.railway.app`.

### 5. (Optional) Custom domain
Same Networking tab → **Custom Domain** → enter `demo.propify.app` (or whatever) → add the CNAME record to your DNS.

### 6. Update your resume / LinkedIn
Replace your old Streamlit Cloud URL with the new Railway URL. The Railway URL won't sleep — when a recruiter clicks it 3 weeks from now, it loads instantly.

## Cost
- Railway Hobby: $5/mo with $5 of usage included
- The demo is lightweight, so you'll use ~$1–2/mo of that

## Why this fixes the sleep problem
Streamlit Cloud's free tier sleeps after ~7 days of inactivity. When a recruiter clicks your demo link cold, they hit a 30-second wakeup screen — which kills first impressions.

Railway keeps your container warm 24/7. First click is instant. Always.
