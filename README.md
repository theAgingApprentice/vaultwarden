# Vaultwarden

Self-hosted Vaultwarden (Bitwarden-compatible) password manager for MitchellNET.

## Access

- **Vault UI:** https://mitchellnet.local/vault/
- **Admin panel:** https://mitchellnet.local/vault/admin
- **LAN-only** — not exposed to the internet

## Architecture

- Runs as a Docker container on the MitchellNET server
- Joins the `mitchellnet` Docker network
- NGINX reverse-proxy handles SSL termination at `/vault/`
- Data persisted in Docker named volume `vaultwarden_data`

## Setup

See [docs/SETUP.md](docs/SETUP.md) for full setup instructions.

## Image

Uses the official `vaultwarden/server` image (pinned tag — update deliberately).
