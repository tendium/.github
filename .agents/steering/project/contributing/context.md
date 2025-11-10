# Contributing and Development
Keywords: contributing, development, versioning, release process, workflow creation

## Workflow Creation

### Structure Requirements
- Use `workflow_call` trigger for reusability
- Document all inputs and secrets with clear descriptions
- Include usage example in header comments
- Update README with usage examples
- Run context-update after changes

### File Location
- Place in `.github/workflows/`
- Follow naming pattern: `descriptive-name.yml`

## Versioning Strategy

### Semantic Versioning with Moving Tags

```
v1.0.0  ← Immutable specific release
v1      ← Moving tag (latest v1.x.x) - recommended for users
```

### Version Bumps

**Patch (v1.0.x)**: Bug fixes, docs, no behavior changes
- Security patches
- Error handling fixes
- Documentation updates

**Minor (v1.x.0)**: New features, backward-compatible
- New optional inputs
- Additional functionality
- Feature deprecations (with warnings)

**Major (vX.0.0)**: Breaking changes
- Remove/rename inputs or secrets
- Change default behavior
- Remove deprecated features
- Change required permissions

## Release Process

1. **Prepare**: Review changes, verify tests
2. **Tag specific version**: `git tag -a v1.0.0 -m "Release v1.0.0: description"`
3. **Move major tag**: `git tag -fa v1 -m "Update v1 to v1.0.0"`
4. **Push tags**: `git push origin v1.0.0 && git push origin v1 --force`
5. **Update docs**: CHANGELOG.md, README, context-update

## Testing Approach

Before merging:
- Test using branch references: `@feature-branch-name`
- Verify with all input combinations
- Check error scenarios
- Review workflow logs

## References
- File: `CONTRIBUTING.md:1`
- File: `CHANGELOG.md:1`
- Related contexts: workflows/overview
