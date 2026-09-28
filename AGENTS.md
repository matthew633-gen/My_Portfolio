# Base44 Dev Environment

## Project Overview
Static HTML/CSS personal portfolio site (Genesis Diaz). No backend, no build step, no JavaScript files, no API calls. External resources loaded via CDN (Google Fonts, FontAwesome).

## Running the App
```bash
docker compose -f docker-compose.base44.yml up -d
```
- Served by nginx:alpine on host port 3000 (container port 80).
- Source is bind-mounted read-only at `/usr/share/nginx/html`.
- Entry point is `Home.html` (configured as nginx `index`), not `index.html`.
- nginx config lives in `nginx.base44.conf`.

## Files
- `Home.html` — main portfolio page (all markup + inline JS in one file)
- `index.css` — stylesheet
- `Resusme.jpg.png` — profile image

## Notes
- The repo directory had restrictive 700 permissions that blocked nginx's worker process; run `chmod 755 .` if nginx returns 403.
- No live-reload dev server; edits to HTML/CSS are served immediately by nginx from the bind mount, but the browser must be refreshed (call `reload_preview` after changes).
- No external credentials or secrets required.
