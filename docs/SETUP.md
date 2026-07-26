# Profile repository automation

## Secrets

None required. Workflows use the default `GITHUB_TOKEN`.

## Settings

1. **Actions → General → Workflow permissions** → Read and write permissions  
2. Optional: enable *Include private contributions on my profile* so the graph includes private work  

## Workflows

| Workflow | Schedule (UTC) | Output |
| --- | --- | --- |
| Profile 3D Contrib | `0 16 * * *` (18:00 CEST / 17:00 CET) | `profile-3d-contrib/profile-night-green.svg` |

First run: **Actions → Profile 3D Contrib → Run workflow**.
