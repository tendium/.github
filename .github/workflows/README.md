# Reusable Workflows

These workflows are part of the special `.github` repository and can be called from any Tendium repository.

**Note on paths**: The path `tendium/.github/.github/workflows/...` is correct - the first `.github` is the repository name, the second is the GitHub directory within it.

## Claude Code Workflow

AI-powered code reviews and interactive assistance using Anthropic's Claude.

### Features
- Interactive @claude mentions in issues, PRs, and comments
- Automatic PR reviews with progress tracking
- Context-aware responses using project documentation

### Usage

Create `.github/workflows/claude.yml` in your repository:

```yaml
name: Claude Code

on:
  pull_request:
    types: [opened, synchronize, reopened]
  issue_comment:
    types: [created]
  pull_request_review_comment:
    types: [created]
  pull_request_review:
    types: [submitted]
  issues:
    types: [opened, edited]

jobs:
  claude:
    uses: tendium/.github/.github/workflows/claude-generic.yml@main
    secrets:
      anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
```

**Required Secret**: `ANTHROPIC_API_KEY` - Your Anthropic API key

**Interaction**: Mention @claude in any comment, review, or issue to get AI assistance.

---

## Bitbucket Mirror Workflow

Automated mirroring of GitHub repositories to Bitbucket using SSH.

### Features
- Full repository mirror or selective branch sync
- Tag synchronization
- Dry-run mode for testing
- Concurrency protection

### Usage Examples

#### Example 1: Mirror master branch on push

Create `.github/workflows/mirror.yml`:

```yaml
name: Mirror to Bitbucket

on:
  push:
    branches:
      - master

jobs:
  mirror:
    uses: tendium/.github/.github/workflows/mirror-to-bitbucket.yml@main
    with:
      repository: ${{ github.repository }}
      branches: "master"
    secrets:
      ssh-private-key: ${{ secrets.BITBUCKET_SSH_PRIVATE_KEY }}
      ssh-known-hosts: ${{ secrets.BITBUCKET_SSH_KNOWN_HOSTS }}
```

#### Example 2: Full mirror (all branches and tags)

```yaml
name: Full Mirror to Bitbucket

on:
  push:
    branches:
      - '**'

jobs:
  mirror:
    uses: tendium/.github/.github/workflows/mirror-to-bitbucket.yml@main
    with:
      repository: ${{ github.repository }}
      # branches: "" (omit for full mirror)
    secrets:
      ssh-private-key: ${{ secrets.BITBUCKET_SSH_PRIVATE_KEY }}
```

#### Example 3: Multiple branches

```yaml
with:
  repository: tendium/my-repo
  branches: "master main develop"
```

#### Example 4: Test with dry-run

```yaml
with:
  repository: tendium/my-repo
  branches: "master"
  dry-run: true
```

### Required Secrets

**`BITBUCKET_SSH_PRIVATE_KEY`**: SSH private key with write access to Bitbucket repository.

Generate SSH key:
```bash
ssh-keygen -t ed25519 -C "github-actions@tendium"
```

Add public key to:
- Bitbucket: Repository Settings → Access keys (with write access)

Note: GitHub access is handled automatically via `GITHUB_TOKEN` - no SSH key setup needed for GitHub.

**`BITBUCKET_SSH_KNOWN_HOSTS`** (optional): SSH known hosts for bitbucket.org

Get known hosts:
```bash
ssh-keyscan bitbucket.org
```

### Parameters

| Parameter | Required | Default | Description |
|-----------|----------|---------|-------------|
| `repository` | Yes | - | Format: `org/repo` (e.g., `tendium/my-repo`) |
| `branches` | No | `""` | Space-separated branches. Empty = full mirror |
| `dry-run` | No | `false` | Test without pushing |

### Notes

- Repository must exist on both GitHub and Bitbucket
- Same org/repo structure assumed on both platforms
- Uses `--force` for branch updates (be cautious!)
- Concurrency protection prevents simultaneous mirrors per repository
