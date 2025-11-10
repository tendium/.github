# AI Context Documentation
Generated: 2025-11-10 14:38
Commit: d90f8189b2590d09b455e48200241fb01093eea7
Mode: initial

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
