# Profile repository automation

## Workflows

### Contribution Snake Animation
- **Schedule (UTC):** `0 16 * * *` (18:00 CEST / 17:00 CET daily)
- **Output:** `assets/github-contribution-grid-snake-dark.svg`
- **Action:** Platane/snk generates animated contribution graph

## Configuration

1. Ensure GitHub Actions have **Read and write permissions** in repository settings
2. Optional: Enable *Include private contributions on my profile* for complete activity tracking

## Manual Trigger

To run workflows manually: **Actions → [Workflow Name] → Run workflow**
