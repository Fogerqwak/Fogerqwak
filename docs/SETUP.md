# Repository setup for automation (secrets & first-run)

This profile repository uses GitHub Actions to refresh generated SVG assets.

## Required secrets

Open:

**Repository Settings → Secrets and variables → Actions → New repository secret**

| Secret name | Required by | How to create | Scopes |
| --- | --- | --- | --- |
| `METRICS_TOKEN` | `.github/workflows/metrics.yml` | [Create a **classic** PAT](https://github.com/settings/tokens/new?description=metrics-profile&scopes=) (Tokens **(classic)**, not fine-grained) | Leave **all scopes unchecked**. Token value must start with `ghp_`. Do **not** use fine-grained (`github_pat_`) — metrics GraphQL rejects them. |

### Common `METRICS_TOKEN` failures

| Log message | Fix |
| --- | --- |
| `fine-grained personal access token` / `unsupported` | Recreate a **classic** PAT and update the secret |
| `token … (missing)` / `legacy or invalid` | Secret missing, empty, misnamed, or stored under **Variables** instead of **Secrets**. Name must be exactly `METRICS_TOKEN` under **Actions secrets** (not Environment secrets unless the job sets `environment:`). Re-paste the full `ghp_…` value with no spaces/newlines. |

`GITHUB_TOKEN` is provided automatically by GitHub Actions. It is enough for:

- `.github/workflows/profile-3d.yml`
- `.github/workflows/snake.yml`

## Recommended GitHub profile settings

1. **Private contributions on your profile (optional)**  
   Profile → Contribution settings → enable *Include private contributions on my profile*  
   so calendars / streak / 3D / snake reflect private work without extra token scopes.

2. **Allow Actions to create commits**  
   Repository → Settings → Actions → General → Workflow permissions → **Read and write permissions**.

3. **Enable workflows**  
   After the first push that adds workflow files, open the **Actions** tab and ensure workflows are not blocked.

## First-time run (required)

Until these jobs succeed once, README image paths are placeholders.

1. Actions → **Profile 3D Contrib** → Run workflow  
2. Actions → **Contribution Snake** → Run workflow  
3. Actions → **GitHub Metrics** → Run workflow (needs `METRICS_TOKEN`)

## Generated outputs

| Asset | Workflow |
| --- | --- |
| `profile-3d-contrib/profile-night-rainbow.svg` | Profile 3D Contrib |
| `assets/github-contribution-grid-snake-dark.svg` | Contribution Snake |
| `github-metrics.svg` | GitHub Metrics |

## Scheduling

| Workflow | Cron (UTC) |
| --- | --- |
| Contribution Snake | `0 0 * * *` |
| GitHub Metrics | `0 2 * * *` |
| Profile 3D Contrib | `0 18 * * *` |

Jobs that push to `main` share concurrency group `profile-generated-assets` so commits do not race.
