# Propify Demo

## Project Overview
Public-facing demo of Propify, my private NBA player prop analytics platform.
Deployed at propifydemo.up.railway.app. This is a portfolio/recruitment asset —
NOT the production product.

**Critical distinction:** This repo intentionally exposes ONLY the UI shell and
deterministic preview output. The real model, probability logic, data pipelines,
auth, and tracking backend live in the private Propify repo and must never leak
into this codebase.

## Tech Stack
- Python 3.x (see `runtime.txt`)
- Streamlit (UI framework)
- NumPy, Pandas (data layer)
- Railway (deployment via `railway.json` + `Procfile`)
- Devcontainer support (`.devcontainer/`)

## Repository Structure
- `propify_demo_app.py` — single-file Streamlit app, the entire demo
- `config.toml` — Streamlit theme config
- `propifynowordslogo.png` — logo asset
- `requirements.txt` — pinned Python deps
- `DEPLOY.md` — Railway deployment notes

## Architecture Rules
- **Single-file app.** Do not split into modules unless I explicitly ask. Mirror
  the private app's sectioned layout via Streamlit `tabs` / `columns`, not files.
- **Deterministic only.** Every "analysis" output must be reproducible from
  inputs. No randomness, no live data, no API calls to real prop sources.
- **No proprietary logic.** Never re-implement the real probability model,
  blending logic, or feature engineering here, even in stub form.
- **Locked sections stay locked.** Parlays, Tracking, Account, Saved Picks are
  product-preview UI only — visible but non-functional. Don't make them work.
- **Blurred values stay blurred.** The visual blur on analytical values is a
  feature, not a bug.

## UI / Brand
- Brand color: Tarheel blue gradient (#4B9CD3 base)
- Navigation hierarchy: Analyze → Parlays → Tracking → Learn → Account
- Only `Analyze` accepts user input (player, stat, line, opponent)
- Visual polish > functional depth. This is a product preview.

## Workflow Preferences
- Quantify changes when discussing scope ("3 new sections, ~80 lines")
- Default to minimal diffs; don't refactor untouched code
- When suggesting features, flag whether they belong in demo vs private repo
- If a change feels like it should live in private Propify, stop and ask

## Deployment
- Railway via `railway.json` + `Procfile`
- Test locally with `streamlit run propify_demo_app.py` before pushing
- Don't bump deps without checking Railway compatibility

## What This Repo Communicates
This is a recruiter / public-facing artifact. Code quality, comments, and
README polish matter more than feature volume. Treat every commit like
someone reviewing my resume will read it.
