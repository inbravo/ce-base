# Context Engineering Use Case Base

This repository contains practical **Context Engineering** use case examples designed for demos, partner conversations, and internal reference.

The site is a lightweight static web app under `docs/` and is intended for GitHub Pages hosting.

## What is in this repo

- `docs/index.html` — main interactive use case experience
- `docs/semantic-components.html` — semantic-components focused page
- `docs/README.md` — short docs-level note

## Core focus areas

The content demonstrates Context Engineering across:

- Cloud platform mappings (AWS today, with space for Databricks/Snowflake/Azure)
- Semantic modeling and business glossary patterns
- End-to-end use case narratives (for example, Amazon UK delivery-style scenarios)

## Run locally

No build step is required.

1. Clone the repo.
2. Open `docs/index.html` directly in a browser.

## Publish on GitHub Pages

1. Push changes to `main`.
2. In GitHub: **Settings → Pages**.
3. Set source to `main` and folder to `/docs` (or `/ (root)` if you move files accordingly).

## Contribution notes

Keep this repo simple and portable:

- Prefer vanilla HTML/CSS/JS
- Avoid adding build tooling unless truly needed
- Keep examples concrete, reusable, and cloud-comparable
