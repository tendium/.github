# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.0] - 2025-11-10

### Added

- **Claude Code Workflow** (`claude-generic.yml`)
  - Interactive @claude mentions in issues, PRs, and comments
  - Automatic PR reviews with progress tracking
  - Context-aware responses using project documentation

- **Bitbucket Mirror Workflow** (`mirror-to-bitbucket.yml`)
  - Full repository mirroring or selective branch sync
  - SSH-based authentication
  - Tag synchronization
  - Dry-run mode for testing
  - Concurrency protection to prevent conflicts

- **Pull Request Template**
  - Structured format: WHY/WHAT/HOW/Testing/Screenshots
  - Testing checklist with honest emoji scale
  - Encourages visual aids and diagrams

- **Documentation**
  - Main README explaining special `.github` repository
  - Workflows README with detailed usage examples
  - CONTRIBUTING.md with development and versioning guide
  - Version pinning documentation (tags, branches, commit SHAs)

- **AI Context Documentation**
  - `.agents/steering/` hierarchical documentation
  - Workflow conventions and patterns
  - Template structure and philosophy
  - CLAUDE.md with coding standards

[Unreleased]: https://github.com/tendium/.github/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/tendium/.github/releases/tag/v1.0.0
