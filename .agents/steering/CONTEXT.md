# AI Context Documentation
Generated: 2025-11-10 15:22
Commit: a202465ebfb51921e6a736b8800533806cecd24a
Mode: incremental

## Last Updated
- Updated: project (new domain)
- Structure: added project/contributing and project/versioning
- Files analyzed: 3 (CONTRIBUTING.md, CHANGELOG.md, workflows/README.md)
- Changes detected since: 2025-11-10 15:07 (commit: 2de3389f5b995c8e888964a6a0a8431b3ae37189)

## Structure

This repository contains reusable GitHub Actions workflows and templates.

### Domains

- **workflows**: Reusable GitHub Actions workflows
  - overview: Repository structure and architecture patterns
  - claude: Claude Code AI integration workflow
  - mirror: Bitbucket mirroring workflow with SSH

- **templates**: GitHub templates
  - pr-template: Pull request template structure and philosophy

- **project**: Project conventions and development
  - contributing: Workflow creation, testing, and release process
  - versioning: Version pinning strategies and tag management

## Key Conventions

- **Reusable workflows**: Use `workflow_call` trigger pattern
- **Permissions**: Explicitly declare minimal required permissions
- **Concurrency**: Repository-scoped groups prevent conflicts
- **Context loading**: Standard pattern for AI context priming
- **SSH authentication**: Agent-based key management for Git operations
- **Versioning**: Semantic versioning with moving major version tags (v1 → latest v1.x.x)
- **Version references**: Recommend `@v1` for stability with automatic bug fixes

## Usage

Load with context-prime for task-specific context.
