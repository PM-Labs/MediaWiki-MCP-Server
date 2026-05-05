# Deployment

This MCP server is deployed to the Pathfinder DO droplet as a Docker container.

## Quick Reference

| Field | Value |
|---|---|
| Droplet | `mcp-server` (SSH alias) |
| Service name | `mediawiki` |
| URL | `https://mediawiki.mcp.pathfindermarketing.com.au/mcp` |
| Docker image | `ghcr.io/pmlabs-org/mcp-mediawiki:latest` |
| Env file | `/opt/pmin-mcpinfrastructure/env/mediawiki.env` |
| Full docs | [PM-Labs/pmin-mcpinfrastructure](https://github.com/PM-Labs/pmin-mcpinfrastructure) → `docs/runbooks/mediawiki.md` |

## Deploy

```bash
# Deployments are automated via CI — push to master triggers build + deploy.
# Manual deploy (if needed):
ssh mcp-server "cd /opt/pmin-mcpinfrastructure && docker compose pull mediawiki && docker compose up -d --force-recreate mediawiki"
```

## Rollback

```bash
ssh mcp-server "cd /opt/pmin-mcpinfrastructure && docker compose stop mediawiki"
# Revert to previous image tag, then: docker compose up -d mediawiki
```

## Operational Docs

See [PM-Labs/pmin-mcpinfrastructure](https://github.com/PM-Labs/pmin-mcpinfrastructure) for:
- Architecture: `docs/ARCHITECTURE.md`
- Runbook: `docs/runbooks/mediawiki.md`
- Cron jobs: `docs/CRON-JOBS.md`
