# Bitbucket Mirror Workflow
Keywords: bitbucket, git mirror, sync, ssh, repository mirroring

## Purpose

Reusable workflow for mirroring GitHub repositories to Bitbucket using SSH authentication.

## Inputs

```yaml
repository: string (required)
  format: "org/repo" (e.g., "tendium/my-repo")

branches: string (optional)
  format: space-separated (e.g., "master main")
  default: "" (full mirror mode)

dry-run: boolean (optional)
  default: false
```

## Secrets

```yaml
ssh-private-key: string (required)
  SSH private key with write access to Bitbucket repository

ssh-known-hosts: string (optional)
  SSH known hosts content for bitbucket.org
```

**Note**: GitHub access is handled automatically via `GITHUB_TOKEN` - SSH key only needs Bitbucket write access.

## Operating Modes

### Full Mirror Mode
When `branches` is empty:
- Mirrors all branches and tags
- Uses `git push --mirror`

### Selective Sync Mode
When `branches` specified:
- Syncs only listed branches with force push
- Always syncs all tags
- Each branch pushed individually

## Concurrency Control

```yaml
concurrency:
  group: git-mirror-${{ inputs.repository }}
  cancel-in-progress: false
```

Prevents concurrent mirror operations per repository to avoid conflicts.

## SSH Setup Pattern

```bash
# Create SSH directory and configure key
mkdir -p ~/.ssh
echo "$SSH_KEY" > ~/.ssh/id_ed25519
chmod 600 ~/.ssh/id_ed25519

# Start SSH agent and add key
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Add destination remote
git remote add destination "git@bitbucket.org:org/repo.git"
```

## Repository URL Construction

Uses parameterized approach:
```bash
SOURCE_REPO="git@github.com:${{ inputs.repository }}.git"
DESTINATION_REPO="git@bitbucket.org:${{ inputs.repository }}.git"
```

This assumes matching org/repo structure between GitHub and Bitbucket.

## Dry Run Support

When `dry-run: true`:
- Adds `--dry-run` flag to all git push commands
- Prints "DRY RUN MODE" message
- No actual changes pushed to destination

## References
- File: `.github/workflows/mirror-to-bitbucket.yml:1`
- Related contexts: workflows/overview
