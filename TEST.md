# TEST.md — Testing Guardrails

**Read this before running any test, authoring any instruction file, or executing any spec.**
These rules are non-negotiable. If a requested task would break one of them, stop and flag it rather than proceeding.

---

## 1. PII never leaves the machine in captures

Network captures (HAR), Playwright traces, and screenshots record real request/response payloads. Any test that touches production-like data can capture customer PII — a GDPR/EEA exposure.

**Rules**
- Scrub HAR files, traces, and screenshots of PII **before** they are committed, attached to a report, or shared with the client.
- Treat `reports/` as dirty by default. Nothing leaves it un-reviewed.
- Mask tokens, auth headers, emails, names, and payment fields in any artifact destined for a ticket, PR, or client hand-off.
- Prefer redacted HAR for evidence. Keep raw captures local and git-ignored.

**Never**
- Commit a raw HAR or trace from a prod or prod-like environment.
- Paste an unredacted network capture into a bug report.

---

## 2. Security tests are scoped by environment

Security payloads (injection strings, fuzzing, auth-bypass attempts) are gated on `env` and run only where explicitly permitted.

**Rules**
- Security payloads live in `lib/` and are selected by the `env` field — never inlined into an instruction file.
- Run security tests against `staging` only, unless there is **written client authorization** for another target.
- Config must refuse destructive or offensive operations when `env: prod`.

**Never**
- Fire security payloads at production without written authorization.
- Hardcode a target URL that bypasses the env guard.

---

## 3. Synthetic test data only

**Rules**
- All fixtures, BVA datasets, and seeded records in `data/` are synthetic.
- Secrets (logins, API keys, tokens) come from `.env` or a vault — never from inside an instruction file, spec, or commit.
- `auth/` storageState files are git-ignored and regenerated, not committed.

**Never**
- Put a real customer record in `data/` or any committed fixture.
- Write a credential into an instruction file or spec.

---

## Pre-run checklist

- [ ] Correct `env` selected; prod guard active if applicable
- [ ] Test data is synthetic; no real PII in scope
- [ ] Security payloads gated and authorized for this target
- [ ] Reports/captures will be scrubbed before leaving the machine
- [ ] No secrets in the instruction file or spec being run
