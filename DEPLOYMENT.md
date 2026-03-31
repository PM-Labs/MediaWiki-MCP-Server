# Deployment

This MCP server is deployed to the Pathfinder DO droplet as a Docker container.

## Quick Reference

| Field | Value |
|---|---|
| Droplet | `mcp-server` |
| Service name | `mediawiki` |
| URL | `https://mediawiki.mcp.pathfindermarketing.com.au/mcp` |
| Docker image | `australia-southeast1-docker.pkg.dev/pathfinder-383411/cloud-run-source-deploy/mediawiki-mcp:latest` |
| Env file | `/opt/pmin-mcpinfrastructure/env/mediawiki.env` |
| Full docs | [PM-Labs/pmin-mcpinfrastructure](https://github.com/PM-Labs/pmin-mcpinfrastructure) → `docs/runbooks/mediawiki.md` |

## Deploy

```bash
gcloud builds submit --tag australia-southeast1-docker.pkg.dev/pathfinder-383411/cloud-run-source-deploy/mediawiki-mcp --project pathfinder-383411
ssh mcp-server "cd /opt/pmin-mcpinfrastructure && docker compose pull mediawiki && docker compose up -d mediawiki"
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
