# GitHub Actions Workflows

This directory contains the GitHub Actions workflows for the OpenCode repository.

## Sync Upstream Workflow

The `sync-upstream.yml` workflow automatically synchronizes changes from the upstream repository ([anomalyco/opencode](https://github.com/anomalyco/opencode)) to this fork.

### How It Works

- **Schedule**: Runs daily at 2:00 AM UTC
- **Manual Trigger**: Can be triggered manually via the GitHub Actions UI
- **Auto-merge**: If no conflicts are detected, changes are automatically merged and pushed to the `dev` branch
- **Conflict Handling**: If merge conflicts are detected, a pull request is created with the conflicts for manual resolution

### Manual Trigger

To manually trigger the upstream sync:

1. Go to the [Actions tab](../../actions)
2. Select "Sync Upstream" workflow
3. Click "Run workflow"
4. Select the branch (should be `dev`)
5. Click "Run workflow"

### What Happens When Conflicts Occur

When merge conflicts are detected:

1. The workflow creates a new branch named `sync-upstream-YYYYMMDD-HHMMSS`
2. A pull request is opened with:
   - Title: "🔄 Sync upstream changes from anomalyco/opencode"
   - The conflicted merge state
   - Instructions to resolve conflicts manually
3. You'll need to:
   - Check out the PR branch
   - Resolve the conflicts
   - Push the resolved changes
   - Merge the PR

### Troubleshooting

If the workflow fails:

- Check the workflow run logs in the Actions tab
- Ensure the repository has proper permissions (contents: write, pull-requests: write)
- Verify that the `dev` branch is the default branch
- Check if there are any network issues or API rate limits

### Related Files

- Workflow: `.github/workflows/sync-upstream.yml`
- Upstream Repository: [anomalyco/opencode](https://github.com/anomalyco/opencode)
