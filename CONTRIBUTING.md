# Contributing to Tendium Projects

Thank you for contributing to Tendium! This guide provides standards and workflows for internal team members contributing across our repositories.

## Code of Conduct

- Be respectful and professional in all interactions
- Welcome new team members and help them get started
- Accept constructive criticism gracefully
- Focus on what is best for the team and our customers

## Development Workflow

### 1. Clone the Repository

```bash
# Clone the repository
git clone https://github.com/tendium/[repository-name].git
cd [repository-name]
```

### 2. Create a Branch

Create a feature branch from `main`:

```bash
git checkout main
git pull origin main
git checkout -b feature/your-feature-name
```

**Branch naming conventions:**

- `feature/` - New features
- `fix/` - Bug fixes
- `docs/` - Documentation updates
- `refactor/` - Code refactoring
- `chore/` - Maintenance tasks

### 3. Make Changes

- Write clear, concise commit messages
- Follow the existing code style in the project
- Add tests for new functionality
- Update documentation as needed
- Ensure your changes work in the target environment

### 4. Commit Your Changes

```bash
git add .
git commit -m "feat: add new feature description"
```

**Commit message format:**

- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation changes
- `test:` - Test updates
- `refactor:` - Code refactoring
- `chore:` - Maintenance tasks
- `perf:` - Performance improvements
- `style:` - Code style changes (formatting, etc.)

### 5. Push and Create Pull Request

```bash
git push origin feature/your-feature-name
```

Then create a pull request on GitHub following the PR template.

## Development Setup

Each repository may have specific setup requirements. Check the repository's README.md for:

- Prerequisites and dependencies
- Local environment setup instructions
- Configuration requirements
- How to run tests
- How to run the application locally

## Coding Standards

### Code Style

- Follow the existing code style in the project
- Use consistent naming conventions
- Write clear, self-documenting code
- Add comments for complex logic
- Keep functions small and focused

### Testing

- Write tests for all new features
- Ensure existing tests pass before submitting PR
- Aim for good test coverage of critical paths
- Include both unit and integration tests where applicable
- Test edge cases and error handling

### Documentation

- Update README.md if your changes affect setup or usage
- Document public APIs and functions
- Add inline comments for complex code
- Update relevant documentation in the repository
- Include examples where helpful

## Pull Request Process

1. **Create a clear PR description** using the PR template:
   - What changes you made
   - Why you made them
   - How to test the changes
   - Any breaking changes or migrations needed

2. **Link related issues** using GitHub keywords:
   - `fixes #123` - Automatically closes issue on merge
   - `relates to #123` - Links without closing
   - `see #123` - Reference related issue

3. **Ensure all checks pass:**
   - All tests passing
   - Code quality checks passing
   - No merge conflicts

4. **Request review** from appropriate team members
   - Tag relevant team members
   - Add reviewers based on code ownership

5. **Address feedback:**
   - Respond to review comments
   - Make requested changes
   - Re-request review when ready

6. **Merge:**
   - Use appropriate merge strategy (squash, rebase, or merge commit based on project conventions)
   - Delete your branch after merging

## Review Guidelines

When reviewing pull requests:

- **Be constructive and respectful** - Focus on the code, not the person
- **Be timely** - Respond to review requests within 1-2 business days
- **Ask questions** to understand the changes and approach
- **Test locally** if possible, especially for significant changes
- **Check for:**
  - Code quality and maintainability
  - Test coverage
  - Documentation updates
  - Potential edge cases or bugs
  - Performance implications
  - Security considerations
- **Approve or request changes clearly** with specific feedback

## Issue Tracking

### Creating Issues

Use the appropriate issue template:

- **Bug Report** - For reporting bugs or unexpected behavior
- **Feature Request** - For proposing new features or enhancements

Fill out all relevant sections to help the team understand and prioritize.

### Issue Labels

Common labels used across repositories:

- `bug` - Something isn't working
- `enhancement` - New feature or request
- `documentation` - Documentation improvements
- `good first issue` - Good for newcomers
- `help wanted` - Extra attention needed
- `wontfix` - This will not be worked on
- `duplicate` - This issue already exists
- `priority: high` - High priority issue
- `priority: medium` - Medium priority issue
- `priority: low` - Low priority issue

## Getting Help

- **Documentation:** Check the repository README and docs
- **Internal Resources:** Check team wiki or knowledge base
- **Ask the Team:** Reach out on Slack or during team meetings
- **Code Owners:** Tag repository maintainers for guidance

## Best Practices

### Security

- Never commit secrets, API keys, or credentials
- Use environment variables for sensitive configuration
- Report security vulnerabilities privately to the security team
- Follow security guidelines for the tech stack

### Performance

- Consider performance implications of your changes
- Profile code for performance-critical sections
- Optimize database queries and API calls
- Monitor resource usage

### Accessibility

- Ensure UI changes are accessible
- Test with keyboard navigation
- Use semantic HTML
- Provide alt text for images

## Repository Maintenance

### Keeping Your Branch Updated

```bash
# While on your feature branch
git fetch origin
git rebase origin/main
```

### Cleaning Up

```bash
# Delete local branch after merge
git branch -d feature/your-feature-name

# Delete remote branch (if not auto-deleted)
git push origin --delete feature/your-feature-name
```

## Questions?

If you have questions about contributing, reach out to:

- Your team lead
- Repository maintainers (see CODEOWNERS if present)
- The engineering team on Slack

Thank you for contributing to Tendium! 🚀
