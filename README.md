# RCSC
Website for RCSC on pump.fun

A single static page (`index.html`): a tongue-in-cheek "market sentiment" score for
Springfield episodes. Votes are stored in the browser's `localStorage` — there is no
backend, database, or API key involved.

## Run locally

```bash
docker compose -f docker-compose.base44.yml up -d
```

Then open http://localhost:3000.

In the Base44 sandbox, `BASE44_PREVIEW_MODE=1` is passed through to the `web` service.
The app needs no configuration keyed on it; shared behaviour is unchanged when the
variable is unset.
