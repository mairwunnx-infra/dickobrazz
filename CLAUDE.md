# Commits Rules

Name commits shortly in Russian language.Use emoji before summary of commit which describes changes.

# Communication Rules

Communicate with user in preferly in russian language, but you can thinking in american english. For chatting you can use emoji.

# Project Overview

## Purpose
Dickobrazz stack for production and test workloads in personal server infrastructure.

## Architecture
- **Dickobrazz Bot** - Telegram bot runtime (`dickobrazz-bot`, `dickobrazz-bot-test`)
- **Dickobrazz Server** - API/session/random providers (`dickobrazz-server`, `dickobrazz-server-test`)
- **MongoDB** - persistent bot/server data (`dickobrazz-mongo`, `dickobrazz-mongo-test`)
- **Redis** - cache/session storage (`dickobrazz-redis`, `dickobrazz-redis-test`)
- **Offen Backup** - volume backups for prod MongoDB/Redis only

## Key Points
- All services connected to shared Docker network `infra`
- Production and test services are isolated by dedicated service names and named volumes
- Application images are rebuilt from upstream images with embedded `config.yaml`
- GitHub Actions workflows build and publish all custom images to GHCR

## File Structure
- `docker-compose.yaml` - full stack definition (prod + test + backups)
- `Dockerfile.dickobrazz-*` - custom image definitions for bot/server variants
- `config.dickobrazz-*.yaml` - embedded runtime config templates
- `.version.dickobrazz-*` - image version pinning for CI/CD workflows
- `.github/workflows/build-dickobrazz-*.yml` - image build/push automation

## Important Notes
- Do not expose internal ports to host for app/db/cache services (use `expose` only)
- Keep resource limits and healthchecks aligned between prod/test service pairs
- Backup services are intentionally created only for production volumes
