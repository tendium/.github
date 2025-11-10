# Version Pinning and References
Keywords: versioning, tags, version pinning, workflow references

## Version Reference Options

Users can reference workflows using multiple formats:

```yaml
# Latest (may include breaking changes)
uses: tendium/.github/.github/workflows/workflow.yml@main

# Major version (recommended - stability with bug fixes)
uses: tendium/.github/.github/workflows/workflow.yml@v1

# Specific version (maximum stability)
uses: tendium/.github/.github/workflows/workflow.yml@v1.2.3

# Specific commit (reproducibility)
uses: tendium/.github/.github/workflows/workflow.yml@abc123...
```

## Recommendations

**For production**: Use `@v1` major version tags
- Automatically receives bug fixes and security patches
- Protected from breaking changes
- Balances stability with improvements

**For testing**: Use `@main` or `@feature-branch`
- Latest features and fixes
- May include breaking changes
- Good for development/testing

**For maximum stability**: Use `@v1.2.3` specific versions
- Completely immutable
- No automatic updates
- Full reproducibility

## Version Tag Strategy

Moving major version tags point to latest minor release:
- Create `v1.0.0` → move `v1` to point to `v1.0.0`
- Create `v1.1.0` → move `v1` to point to `v1.1.0`
- Users on `@v1` automatically get v1.1.0
- Breaking changes require new major version (`v2`)

## References
- File: `.github/workflows/README.md:7-13`
- File: `CONTRIBUTING.md:92-130`
- Related contexts: project/contributing
