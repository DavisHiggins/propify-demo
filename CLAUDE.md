# Propify Demo

## Project Overview
Public-facing demo of Propify, my private NBA player prop analytics platform.
Deployed at propifydemo.up.railway.app.

**Critical distinction:** This repo intentionally exposes ONLY the UI shell and
deterministic preview output. The real model, probability logic, data pipelines,
auth, and tracking backend are private.

## Tech Stack
- Python 3.x (see `runtime.txt`)
- Streamlit (UI framework)
- NumPy, Pandas (data layer)
- Railway (deployment via `railway.json` + `Procfile`)
- Devcontainer support (`.devcontainer/`)

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
