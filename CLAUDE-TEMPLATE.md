# Claude Code — Project Instructions

<!-- 
  ╔══════════════════════════════════════════════════════════════╗
  ║  CLAUDE.md TEMPLATE v1.0                                    ║
  ║  Drop this into any project root and fill in the blanks.    ║
  ║  Placeholders are marked with {{PLACEHOLDER}}.              ║
  ║  Delete sections you don't need. Keep testing section #1.   ║
  ╚══════════════════════════════════════════════════════════════╝
-->

<!-- ============================================================
     SECTION 1: TESTING (always keep this at the TOP)
     Claude Code reads CLAUDE.md top-to-bottom and gives more
     weight to rules near the beginning.
     ============================================================ -->

## ⛔ MANDATORY: Testing Before ANY Completion (READ FIRST)

**This section overrides everything below. No exceptions. No shortcuts.**

### HARD RULES — violating any of these is a critical failure:

1. **NEVER claim a task is done without running tests and showing ACTUAL output**
2. **NEVER say "tests should pass" or "this should work" — RUN THEM and prove it**
3. **NEVER commit, push, or open a PR without green tests**
4. **NEVER summarize expected test results — execute the commands and paste real output**
5. **NEVER skip tests because "the change is small" or "it's just a typo fix"**

### Test commands (use these exact commands):

```bash
# Run ALL tests (preferred — always run this before commit/PR):
{{ROOT_TEST_COMMAND}}

# Per-workspace / per-area commands:
{{WORKSPACE_TEST_COMMANDS}}
# Examples (delete these after filling in yours):
# npm run test:backend     # API / server-side
# npm run test:frontend    # UI / client-side
# npm run test:shared      # shared packages / libs
# cd backend && pytest     # Python backend
# cd frontend && npm test  # React frontend

# E2E / integration / smoke tests (run when relevant):
{{E2E_TEST_COMMANDS}}
# Examples:
# npm run test:e2e         # Playwright / Cypress
# npm run test:smoke       # smoke tests against live env

# Post-deployment verification (if applicable):
{{DEPLOY_VERIFY_COMMAND}}
# Example:
# ./scripts/verify-deployment.sh
```

### STOP-AND-VERIFY pattern (follow this EVERY time):

```
1. Make code changes
2. STOP — run the root test command
3. Paste the FULL test output (not a summary)
4. If ANY test fails → fix and re-run. Do NOT proceed.
5. Only after ALL tests pass → continue to commit/PR
```

### When working in parallel sessions:

- Each session MUST test in its own workspace/branch
- Do NOT trust that "another session already tested this"
- If tests fail due to conflicts from another session, STOP and report to {{DEVELOPER_NAME}}

### Anti-patterns (DO NOT DO THESE):

- ❌ "The tests should pass based on the changes I made"
- ❌ "I verified the logic is correct" (without actually running tests)
- ❌ Committing code then running tests after
- ❌ Running only one test file when multiple areas were changed
- ❌ Skipping deployment verification after deploying
- ❌ Saying "deployed successfully" without running verification
- ❌ Moving a task card to "Done" / "In Review" before tests pass


<!-- ============================================================
     SECTION 2: CODE QUALITY GATES (optional but recommended)
     ============================================================ -->

## Code Quality Gates

Before committing, also run:

```bash
# Linting
{{LINT_COMMAND}}
# Examples: npm run lint / ruff check . / eslint .

# Type checking
{{TYPECHECK_COMMAND}}
# Examples: npx tsc --noEmit / mypy . / pyright

# Formatting check
{{FORMAT_CHECK_COMMAND}}
# Examples: npm run format:check / ruff format --check .
```

**Commit order: format → lint → typecheck → test → commit.**


<!-- ============================================================
     SECTION 3: GIT & BRANCHING CONVENTIONS
     ============================================================ -->

## Git Conventions

### Branch naming
```
{{BRANCH_PATTERN}}
```
<!-- Examples:
  issue-N-<slug>         (e.g. issue-42-auth-fix)
  feat/<slug>            (e.g. feat/dark-mode)
  fix/<slug>             (e.g. fix/login-crash)
-->

### Commit messages
Use {{COMMIT_CONVENTION}} convention.
<!-- Examples: Conventional Commits, Angular, custom -->

```
{{COMMIT_FORMAT}}
```
<!-- Example:
  feat(scope): short description
  fix(scope): short description
  chore(scope): short description
-->

### PR workflow
1. Create feature branch from `{{DEFAULT_BRANCH}}`
2. Make changes and run `{{ROOT_TEST_COMMAND}}`
3. Push and open PR
4. PR title follows commit convention
5. PR body includes: summary, test report, related issue link


<!-- ============================================================
     SECTION 4: TASK WORKFLOW (optional — for issue trackers)
     Delete this section if not using GitHub Issues / Projects.
     ============================================================ -->

## Working on Tasks

When told to **"work on issue #N"** (or similar), follow this sequence:

### 1. Read the task
```bash
{{READ_TASK_COMMAND}}
```
<!-- Example: gh issue view N --json title,body,labels,comments -->

### 2. Plan before coding
- Understand acceptance criteria
- Identify affected areas / files
- Consider what tests need to be written or updated

### 3. Execute
- Create feature branch: `{{BRANCH_PATTERN}}`
- Implement the changes
- Write/update tests alongside code (not after)

### 4. ⛔ TEST — MANDATORY GATE
- Run `{{ROOT_TEST_COMMAND}}`
- **Paste full test output as proof**
- If tests fail → fix and re-run until green

### 5. Open PR
```bash
gh pr create \
  --title "{{COMMIT_FORMAT_EXAMPLE}}" \
  --body "Closes #N

## Summary
...

## Test Report
- Tests run: X
- Tests passed: X
- Tests failed: 0
"
```

### Error handling
- **Tests fail**: fix first, do NOT open PR until all tests pass
- **Blocked by another issue**: flag it and ask {{DEVELOPER_NAME}}


<!-- ============================================================
     SECTION 5: DEPLOYMENT (optional — for deployed services)
     Delete if project doesn't deploy.
     ============================================================ -->

## Deployment Verification (MANDATORY)

After **every** deployment, run:
```bash
{{DEPLOY_VERIFY_COMMAND}}
```

**NEVER** claim a deployment is complete without verification passing.

<!-- Describe what your verification does:
  - Checks deployed endpoints respond correctly
  - Verifies database migrations ran
  - Smoke tests critical paths
  - Compares expected vs actual deployed artifacts
-->


<!-- ============================================================
     SECTION 6: PROJECT-SPECIFIC RULES
     Add any rules unique to this project.
     ============================================================ -->

## Project-Specific Rules

<!-- Examples:
  - New API endpoints must be registered in src/index.ts
  - All new components need Storybook stories
  - Database migrations must be reversible
  - Environment variables go in .env.example (never commit .env)
-->


<!-- ============================================================
     SECTION 7: ARCHITECTURE NOTES (optional but helpful)
     Brief context so Claude Code understands the project.
     ============================================================ -->

## Architecture Overview

<!-- Fill in a brief description:
  - Project type: {{PROJECT_TYPE}} (monorepo / single app / microservices)
  - Stack: {{TECH_STACK}}
  - Key directories:
    - {{DIR_1}} — description
    - {{DIR_2}} — description
  - External services: {{SERVICES}}
-->
