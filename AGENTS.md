# Repo notes

## What this project is

A single static HTML page (`index.html`). No package manager, no build step, no
backend. The page calls no APIs; the score is persisted in `localStorage`, and one
image is loaded from Wikimedia (external network only).

## How it runs here

`docker-compose.base44.yml` runs `nginx:alpine` on host port 3000 and bind-mounts
only `index.html` into the web root. Because the source file is mounted, edits show
up on the next page load without any rebuild or restart.

## Verifying a change

```bash
docker compose -f docker-compose.base44.yml ps
curl -s localhost:3000/ | head
```

Health: `docker compose -f docker-compose.base44.yml ps` should report `web` as
`healthy` (it probes `/index.html` with busybox `wget`).

## Quirks

- Original import had the entire HTML document inside `README.md`; it was extracted
  to `index.html` so it can be served. Keep new markup in `index.html`.
- `BASE44_PREVIEW_MODE` is passed to the `web` service but nothing keys off it: the
  container is plain nginx and needs no sandbox-specific override.
