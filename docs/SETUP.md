# Vaultwarden Setup Guide

## First-time server setup

### 1. Create the Docker volume
```bash
docker volume create vaultwarden_data
```

### 2. Create the .env file
```bash
cp .env.example .env
```

Generate an admin token:
```bash
openssl rand -base64 48
```

Paste the output into `.env` as `ADMIN_TOKEN=`.

Set `SIGNUPS_ALLOWED=true` initially so you can create your account, then set it back to `false`.

### 3. Deploy
```bash
docker compose up -d
```

### 4. Create your account
Navigate to https://mitchellnet.local/vault/ and register your account.

### 5. Disable signups
Edit `.env` and set `SIGNUPS_ALLOWED=false`, then:
```bash
docker compose up -d
```

### 6. Verify admin panel
Navigate to https://mitchellnet.local/vault/admin and log in with your `ADMIN_TOKEN`.

## Updates

To update the image, change the pinned tag in `docker-compose.yml` and redeploy:
```bash
docker compose pull && docker compose up -d
```

## Data

All vault data is stored in the `vaultwarden_data` Docker named volume.
To back it up:
```bash
docker run --rm -v vaultwarden_data:/data -v $(pwd):/backup \
  alpine tar czf /backup/vaultwarden-backup.tar.gz /data
```
