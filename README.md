# ai-adventure

A collection of findings and improvements from working with [Claude Code](https://docs.anthropic.com/en/docs/claude-code).

## Contents

### [`CLAUDE-TEMPLATE.md`](./CLAUDE-TEMPLATE.md)

A drop-in `CLAUDE.md` template for any project. It provides Claude Code with project-specific instructions and conventions, covering:

1. **Mandatory testing rules** — hard rules that require running tests and showing real output before any task is marked complete.
2. **Code quality gates** — lint, type-check, and format commands to run before every commit.
3. **Git & branching conventions** — branch naming patterns and commit message format.
4. **Task workflow** — step-by-step process for picking up an issue, implementing a fix, and opening a PR.
5. **Deployment verification** — commands to confirm every deployment is healthy.
6. **Project-specific rules** — a placeholder section for rules unique to a given project.
7. **Architecture overview** — brief context so Claude Code understands the tech stack and key directories.

#### Usage

Copy `CLAUDE-TEMPLATE.md` to the root of your project, rename it `CLAUDE.md`, and fill in the `{{PLACEHOLDER}}` values. Delete any sections that don't apply.

```bash
cp CLAUDE-TEMPLATE.md /path/to/your-project/CLAUDE.md
```
