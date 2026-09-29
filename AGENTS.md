# Base44 Dev Environment

## Project Overview
Static HTML portfolio site (single `index.html` file, no build step, no backend, no dependencies).

## Setup Notes
- The repo's `index.html` was empty due to a botched git rename; content was restored from the first commit (`portfolio-mobike.html`).
- Served via `nginx:alpine` in docker compose, bind-mounting the repo root to `/usr/share/nginx/html`.
- The repo root directory must have `755` permissions so nginx's worker process can read it. If you get a 403, run `chmod 755 .`.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
App is served on port 3000. No secrets, no env vars, no migrations needed.

## Verification
- `curl -s -o /dev/null -w "%{http_code}" http://localhost:3000/` should return `200`.
- The page is a self-contained portfolio with inline CSS/JS; edits to `index.html` appear on browser refresh (no live-reload server, use `reload_preview` after changes).
