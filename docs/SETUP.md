# Repository setup for automation (secrets & first-run)

This profile repository uses GitHub Actions to refresh generated SVG assets.

## Required secrets

None. `GITHUB_TOKEN` is provided automatically by GitHub Actions and is enough for:

- `.github/workflows/profile-3d.yml`

## Recommended GitHub profile settings

1. **Private contributions on your profile (optional)**  
   Profile → Contribution settings → enable *Include private contributions on my profile*  
   so the 3D contribution graph reflects private work.

2. **Allow Actions to create commits**  
   Repository → Settings → Actions → General → Workflow permissions → **Read and write permissions**.

3. **Enable workflows**  
   After the first push that adds workflow files, open the **Actions** tab and ensure workflows are not blocked.

## First-time run (required)

Until this job succeeds once, the README image path may be a placeholder.

1. Actions → **Profile 3D Contrib** → Run workflow

## Generated outputs

| Asset | Workflow |
| --- | --- |
| `profile-3d-contrib/profile-night-green.svg` (and sibling themes) | Profile 3D Contrib |

## Scheduling

| Workflow | Cron (UTC) |
| --- | --- |
| Profile 3D Contrib | `0 18 * * *` |
