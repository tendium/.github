# Pull Request Template
Keywords: pr template, pull request, documentation, testing

## Structure

The PR template follows a structured format with 5 main sections:

### 1. WHY - Context and Motivation
Purpose: Explain the problem/feature in simple terms for non-technical stakeholders.

### 2. WHAT - What was Changed
Purpose: High-level overview of code modifications.
- Small changes (< 10 files): List specific files
- Large changes: Group by component/category with counts

### 3. HOW - How the Changes Were Made
Purpose: Technical implementation details.
**Encourages**: ASCII diagrams for architecture, flows, relationships, or complex interactions.

### 4. Testing
Purpose: Document testing approach with checkboxes.

Testing levels (in order of rigor):
```markdown
- [ ] 😨 Brain testing (informal)
- [ ] 😬 Manual testing (pushed buttons)
- [ ] 🏆 Automated tests (preferred)
- [ ] ✏️ Other (describe)
```

### 5. Optional Sections
- Screenshots/Demo: For UI changes showing before/after
- Open Questions: Areas needing reviewer focus

## Template Philosophy

- **Accessibility**: Non-technical explanations in WHY section
- **Visual aids**: Encouraged for complex changes
- **Honest testing**: Playful emoji scale acknowledges reality while encouraging rigor
- **Flexibility**: Optional sections for situational needs

## References
- File: `.github/pull_request_template.md:1`
- Related contexts: workflows/claude (PR review automation)
