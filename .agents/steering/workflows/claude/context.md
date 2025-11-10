# Claude Code Workflow
Keywords: claude, ai, code review, anthropic, automation

## Purpose

Reusable workflow for integrating Claude Code AI assistant into GitHub repositories for:
- Interactive @claude mentions in comments, reviews, and issues
- Automatic PR reviews with progress tracking

## Workflow Structure

### Job 1: claude-interactive
Triggers on @claude mentions in:
- Issue comments
- PR review comments
- PR reviews
- Issue body/title

**Required Permissions**: contents:write, pull-requests:write, issues:write, id-token:write, actions:read

### Job 2: claude-pr-review
Automatically triggers on PR events (excludes bots).

**Required Permissions**: contents:read, pull-requests:write, id-token:write

## Context Loading Pattern

Both jobs use a consistent context loading approach:

```yaml
prompt: |
  Before responding:
  1) Map .agents/steering/ structure
  2) Read relevant context.md files
  3) Read CLAUDE.md for guidelines
```

This ensures Claude has project-specific knowledge before responding.

## PR Review Configuration

The review focuses on 6 areas:
1. Repository scope alignment
2. Code quality
3. Security
4. Performance
5. Testing
6. Documentation

**Output Style**: Direct, concise, problem-focused (no praise).

## Progress Tracking

Both jobs enable `track_progress: true` which:
- Creates tracking comments with checkboxes
- Includes full PR context
- Updates progress during execution
- Marks completion

## Tool Restrictions

PR review limits Claude to specific safe tools:
- `mcp__github_inline_comment__create_inline_comment`
- `Bash(gh pr *)` for PR operations
- `Read`, `Glob`, `Bash(find:*)` for code inspection

## Required Secrets
- `anthropic_api_key`: API key for Claude access

## References
- File: `.github/workflows/claude-generic.yml:1`
- Related contexts: workflows/overview
