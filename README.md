# Artha Cal Slug Buildpack

Scalingo/Heroku-compatible buildpack that assembles the prebuilt Artha Scheduling
(Cal.com fork) runtime slug on the builder, avoiding the 300 MiB source-archive cap.

At build time it:
1. Downloads a pinned Node.js runtime into `.node/`.
2. Downloads the prebuilt Next.js standalone slug payload from `SLUG_PAYLOAD_URL`
   (a GitHub release asset) and extracts it into the app root.
3. Wires `PATH` so `node` resolves to the bundled runtime.

Config:
- `SLUG_PAYLOAD_URL` (required) — URL of the gzipped slug payload tarball.
- `NODE_VERSION` (optional, default `v22.12.0`).
