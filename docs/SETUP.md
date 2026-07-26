# Repository setup for automation (secrets & first-run)

This profile repository uses GitHub Actions to refresh generated SVG assets.

## Required secrets

None. `GITHUB_TOKEN` is provided automatically by GitHub Actions and is enough for:

- `.github/workflows/profile-3d.yml`
- `.github/workflows/snake.yml`

## Recommended GitHub profile settings

1. **Private contributions on your profile (optional)**  
   Profile → Contribution settings → enable *Include private contributions on my profile*  
   so calendars / streak / 3D / snake reflect private work.

2. **Allow Actions to create commits**  
   Repository → Settings → Actions → General → Workflow permissions → **Read and write permissions**.

3. **Enable workflows**  
   After the first push that adds workflow files, open the **Actions** tab and ensure workflows are not blocked.

## First-time run (required)

Until these jobs succeed once, README image paths may be placeholders.

1. Actions → **Profile 3D Contrib** → Run workflow  
2. Actions → **Contribution Snake** → Run workflow  

## Generated outputs

| Asset | Workflow |
| --- | --- |
| `profile-3d-contrib/profile-night-green.svg` (and sibling themes) | Profile 3D Contrib |
| `assets/github-contribution-grid-snake-dark.svg` | Contribution Snake |

## Scheduling

| Workflow | Cron (UTC) |
| --- | --- |
| Contribution Snake | `0 0 * * *` |
| Profile 3D Contrib | `0 18 * * *` |

Jobs that push to `main` share concurrency group `profile-generated-assets` so commits do not race.
