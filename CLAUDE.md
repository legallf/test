# CLAUDE.md

This file provides guidance for AI assistants (Claude and others) working in this repository.

---

## Repository Overview

This repository is currently in its initial setup phase. Update this section as the project evolves to describe what the project does, its purpose, and the primary technologies used.

---

## Project Structure

```
/
├── CLAUDE.md          # This file — AI assistant guidance
└── ...                # Project files to be added
```

Update this tree as directories and files are added to the project.

---

## Development Workflow

### Branch Strategy

- The main branch holds production-ready code.
- Feature branches follow the pattern: `feature/<short-description>`
- Bug fix branches: `fix/<short-description>`
- AI-generated branches: `claude/<description>-<session-id>`

### Commit Conventions

Use clear, imperative commit messages:

```
Add user authentication module
Fix null pointer exception in parser
Refactor database connection pool
Update CLAUDE.md with project structure
```

- Keep the subject line under 72 characters.
- Use the body to explain *why*, not *what*, when context is non-obvious.
- Do not use emojis in commit messages unless the project explicitly adopts them.

### Pull Requests

- PR titles should mirror the commit message style.
- Include a brief summary of what changed and why.
- Link related issues when applicable.

---

## Git Operations for AI Assistants

- **Push branch**: `git push -u origin <branch-name>`
- Branch names for AI work must start with `claude/` and end with the session ID.
- On push failures due to network errors, retry up to 4 times with exponential backoff (2 s, 4 s, 8 s, 16 s).
- Fetch specific branches when possible: `git fetch origin <branch-name>`

---

## Code Conventions

These are general conventions to follow until language- or framework-specific guidelines are added.

### General

- Prefer clarity over cleverness.
- Keep functions and methods small and focused on a single responsibility.
- Avoid premature abstraction — three similar lines of code is better than a premature helper.
- Do not add comments that merely restate what the code does; only comment where the logic is non-obvious.
- Do not add error handling for impossible scenarios; trust internal invariants.

### Security

- Never commit secrets, credentials, API keys, or `.env` files.
- Validate all input at system boundaries (user input, external API responses).
- Avoid introducing OWASP Top 10 vulnerabilities (XSS, SQL injection, command injection, etc.).

### File Management

- Edit existing files in preference to creating new ones.
- Do not create files that are not directly needed for the current task.
- Do not create documentation files (README, changelogs, ADRs) unless explicitly requested.

---

## Testing

Add project-specific test instructions here as the project grows. General guidelines:

- Run all tests before committing.
- Do not disable or skip tests to make CI pass — fix the underlying issue.
- Aim for tests that are fast, deterministic, and independent of external services.

---

## Environment Setup

Document setup steps here as the project is established. Example structure:

```bash
# Install dependencies
<command>

# Run the project
<command>

# Run tests
<command>
```

---

## AI Assistant Instructions

### Scope of Changes

- Only make changes that are directly requested or clearly necessary.
- Do not refactor, reformat, or "improve" surrounding code unless asked.
- Do not add type annotations, docstrings, or comments to code you did not change.
- Do not introduce feature flags or backwards-compatibility shims when a direct change suffices.

### Reversibility and Blast Radius

- Freely make local, reversible changes (editing files, running tests).
- Ask for confirmation before taking actions that are hard to reverse (force-push, dropping tables, deleting branches, closing issues/PRs, sending external messages).

### Research Before Writing

- Read relevant files before suggesting or making modifications.
- Understand existing patterns before introducing new ones.

### Parallelism

- Make independent tool calls in parallel to maximise efficiency.
- Wait for results from one step before using its output in a subsequent step.

---

## Updating This File

Keep CLAUDE.md up to date as the project evolves:

- Add the tech stack and project description once established.
- Update the directory tree when the structure changes significantly.
- Add language- or framework-specific linting, formatting, and testing commands.
- Record architectural decisions or notable conventions that aren't obvious from the code.
