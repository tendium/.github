# Contributing to Tendium Workflows

Thank you for contributing to our shared GitHub workflows! This guide explains how to create, test, and release reusable workflows.

## Creating New Reusable Workflows

### File Structure

Create workflow files in `.github/workflows/`:

```yaml
name: Your Workflow Name

on:
  workflow_call:
    inputs:
      your-input:
        description: "Description of the input"
        required: true
        type: string
    secrets:
      your-secret:
        description: "Description of the secret"
        required: true

jobs:
  your-job:
    runs-on: ubuntu-latest
    steps:
      - name: Your step
        run: echo "Hello"
```

### Requirements

1. **Use `workflow_call` trigger** - Required for reusable workflows
2. **Document inputs and secrets** - Add clear descriptions
3. **Add usage example** - Include inline comment header showing how to call the workflow
4. **Update README** - Add usage examples to `.github/workflows/README.md`
5. **Update AI context** - Run `/tendium-local:context-update` to update documentation

### Usage Example Header

Add this header to your workflow file:

```yaml
# Your Workflow Name
#
# Brief description of what the workflow does.
#
# Usage example:
#
#   name: Use Your Workflow
#   on: [push]
#   jobs:
#     use-workflow:
#       uses: tendium/.github/.github/workflows/your-workflow.yml@v1
#       with:
#         your-input: "value"
#       secrets:
#         your-secret: ${{ secrets.YOUR_SECRET }}
#
# For more examples, see: .github/workflows/README.md
```

## Testing Workflows

### Test Using Branches

Before merging, test your workflow using branch references:

```yaml
uses: tendium/.github/.github/workflows/your-workflow.yml@your-feature-branch
```

### Manual Testing

1. Create a test repository or use an existing one
2. Add a workflow that calls your new workflow using `@your-branch-name`
3. Trigger the workflow and verify behavior
4. Test all input combinations and edge cases

### Testing Checklist

- [ ] Test with all required inputs
- [ ] Test with optional inputs omitted
- [ ] Test error cases and failure scenarios
- [ ] Verify all secrets are properly handled
- [ ] Check workflow runs successfully on ubuntu-latest
- [ ] Review workflow logs for any warnings

## Versioning Strategy

We follow **Semantic Versioning** with moving major version tags.

### Version Format

- **v1.0.0** - Specific immutable release (major.minor.patch)
- **v1** - Moving tag pointing to latest v1.x.x (recommended for users)

### When to Bump Versions

**Patch (v1.0.x)**: Bug fixes, documentation updates, no behavior changes
- Fix incorrect behavior
- Update inline documentation
- Security patches

**Minor (v1.x.0)**: New features, backward-compatible changes
- Add new optional inputs
- Add new functionality while maintaining existing behavior
- Deprecate features (with warning)

**Major (vX.0.0)**: Breaking changes
- Remove or rename inputs/secrets
- Change default behavior
- Remove deprecated features
- Change required permissions

### Examples

```bash
# Bug fix: v1.2.3 → v1.2.4
- Fixed error handling in mirror workflow

# New feature: v1.2.4 → v1.3.0
- Added dry-run parameter to mirror workflow

# Breaking change: v1.3.0 → v2.0.0
- Removed deprecated sync-mode parameter
- Changed default branch behavior
```

## Release Process

### 1. Prepare Release

```bash
# Ensure you're on main branch
git checkout main
git pull origin main

# Verify tests pass
# Review changes since last release
git log v1.2.3..HEAD --oneline
```

### 2. Create Version Tag

```bash
# Create specific version tag
git tag -a v1.2.4 -m "Release v1.2.4: Brief description of changes"
git push origin v1.2.4
```

### 3. Move Major Version Tag

```bash
# Move the major version tag to point to the new release
git tag -fa v1 -m "Update v1 to v1.2.4"
git push origin v1 --force
```

### 4. Update Documentation

- Update CHANGELOG.md (if present) with release notes
- Ensure `.github/workflows/README.md` reflects any changes
- Update AI context if needed: `/tendium-local:context-update`

### 5. Communicate Breaking Changes

For major version bumps:
- Create GitHub release with migration guide
- Update all example code to show new version
- Notify teams about the new major version

## Version Tag Commands Reference

```bash
# List all tags
git tag -l

# Create annotated tag
git tag -a v1.0.0 -m "Release v1.0.0: Initial release"

# Move existing tag (e.g., v1)
git tag -fa v1 -m "Update v1 to v1.0.0"

# Push specific tag
git push origin v1.0.0

# Push tag with force (for moving tags)
git push origin v1 --force

# Delete local tag
git tag -d v1.0.0

# Delete remote tag
git push origin :refs/tags/v1.0.0
```

## Best Practices

1. **Test thoroughly** before creating tags
2. **Use semantic versioning** consistently
3. **Document breaking changes** clearly in release notes
4. **Keep major version tags updated** so users on `@v1` get bug fixes
5. **Add usage examples** for every workflow
6. **Update AI context** after significant changes
7. **Review security implications** of all changes

## Questions?

Open an issue in this repository for questions or discussions about workflow development.
