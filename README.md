# Tendium GitHub Workflows & Templates

This is a special **`.github`** repository that GitHub recognizes at the organization level. It provides:

- **Organization-wide defaults**: Templates and workflows available to all Tendium repositories
- **Reusable workflows**: Shared workflows callable from any repo using `tendium/.github/.github/workflows/...@main`
- **Default community health files**: PR templates, issue templates, and other defaults apply across the organization

## What's Included

- **Reusable Workflows**: Share common CI/CD patterns across repositories
  - [Claude Code Integration](.github/workflows/README.md#claude-code-workflow) - AI-powered code reviews and assistance
  - [Bitbucket Mirroring](.github/workflows/README.md#bitbucket-mirror-workflow) - Automated repository synchronization

- **Templates**: Standard templates for consistency
  - [Pull Request Template](.github/pull_request_template.md) - Structured PR documentation

## Usage

See [workflows/README.md](.github/workflows/README.md) for detailed usage examples.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines on creating and releasing workflows.

Quick start:
1. **Make changes** in feature branches
2. **Test workflows** using branch references (`@your-branch-name`)
3. **Submit PR** using the provided template
4. **AI Review** - Tag @claude in comments for AI assistance

## Documentation

- [CONTRIBUTING.md](CONTRIBUTING.md) - Workflow development and release process
- [CHANGELOG.md](CHANGELOG.md) - Version history and release notes
- `CLAUDE.md` - AI agent coding standards
- `.agents/steering/` - Task-focused context for AI tools

For questions or issues, open an issue in this repository.
