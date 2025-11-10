# AI Context Documentation
Generated: 2025-11-10 15:07
Commit: 2de3389f5b995c8e888964a6a0a8431b3ae37189
Mode: incremental

## Last Updated
- Updated: workflows/mirror
- Structure: kept as-is
- Files analyzed: 1 (mirror-to-bitbucket.yml)
- Changes detected since: 2025-11-10 14:38 (commit: d90f8189b2590d09b455e48200241fb01093eea7)

## Structure

This repository contains reusable GitHub Actions workflows and templates.

### Domains

- **workflows**: Reusable GitHub Actions workflows
  - overview: Repository structure and architecture patterns
  - claude: Claude Code AI integration workflow
  - mirror: Bitbucket mirroring workflow with SSH

- **templates**: GitHub templates
  - pr-template: Pull request template structure and philosophy

## Key Conventions

- **Reusable workflows**: Use `workflow_call` trigger pattern
- **Permissions**: Explicitly declare minimal required permissions
- **Concurrency**: Repository-scoped groups prevent conflicts
- **Context loading**: Standard pattern for AI context priming
- **SSH authentication**: Agent-based key management for Git operations

## Usage

Load with context-prime for task-specific context.
