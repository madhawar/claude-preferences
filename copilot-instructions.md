# Copilot Instructions

## Project context
- Playwright + TypeScript + Node.js automation suite.
- Design pattern: **Page Object Model**. New page interactions belong in a Page Object, not inline in tests.
- CI/CD: Azure Pipelines, multiple configurable pipelines for granular test execution.
- Reusable building blocks:
  - Generic API request script — reads request bodies from JSON, parameters are overridable per test.
  - Generic DB query script — runs SQL against test DBs based on input query.
- Tests verify across three layers in one flow: **API → UI → DB**.

## Code style
- TypeScript strict mode. **No `any`** — use `unknown` + narrowing, or define the type.
- Prefer named exports over default exports.
- Async/await only. No `.then()` chains.
- Locators: dedicated, stable selectors (data-testid or role-based). Avoid brittle CSS/XPath.
- Keep test files thin — assertions and orchestration only. Logic goes in Page Objects, fixtures, or helpers.
- File naming: `kebab-case.ts` for files, `PascalCase` for Page Object classes, `camelCase` for functions.

## Test guardrails — non-negotiable
- **Never** execute `DELETE` queries against any environment.
- **Never** run CRUD operations inside sanity tests — sanity is read-only.
- **Never** target production. Test environment URLs only.
- Only use approved test data. Don't fabricate user accounts or PII.
- Don't mutate shared resources without a teardown.

## Test writing
- Each test must be independent and runnable in isolation. No order dependencies.
- Use Playwright fixtures for setup/teardown, not `beforeAll` with shared state.
- Assertions: prefer Playwright's `expect` with auto-retry over manual waits.
- No `page.waitForTimeout()` — use locator-based waits.
- One logical assertion per test where possible; group related checks with `test.step()`.

## When suggesting code
- Lead with the code. Minimal preamble.
- If the request is ambiguous, ask **one** sharp question — don't guess across three options.
- Push back if I'm about to violate a guardrail or break the POM pattern.
- Don't pad explanations with emojis or section headers for short answers.
- If a simpler approach exists than what I asked for, say so in one line.

## What to avoid
- Inline page interactions in test files (must go in Page Objects).
- Hardcoded waits, sleeps, or magic timeouts.
- Test data fabricated on the fly instead of using the approved test data source.
- Copy-pasted API request blocks — extend the generic API script instead.
- New abstractions when an existing helper covers the case.
