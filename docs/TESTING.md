# NuxHub AI — Testing Methodology

This document explains **how** NuxHub AI is verified, **what** the test results
mean, and — critically — **what they do not yet prove**. Read this before
trusting any "PASS" badge.

---

## Two kinds of verification

| Kind | What it checks | Status in v1.0 |
|---|---|---|
| **Design verification** (current) | Logical coherence: do the agent rules, state machine, and judge criteria agree on hand-authored scenarios? | Done — 7/7 PASS |
| **Live-run validation** (future) | Real model inference filling artifacts end-to-end under real timing/cost | Not started |

Everything in v1.0 is **design verification**. No live model run has executed
the full pipeline yet. This is an honest limitation, not a marketing footnote.

---

## What design verification is

Each E2E test is a **hand-authored scenario** stored as a YAML fixture in
`data/e2e/`. A fixture encodes:

- the inbound message(s) for each turn
- the expected state at each step (DISCOVERY, QUALIFICATION, ...)
- the expected artifact fields each agent should produce
- the expected judge verdict (PASS / FIXER / ESCALATE)
- the expected final state (CONVERSION / FOLLOW_UP / BLACKLIST / HUMAN_ESCALATION)

A test "PASSes" when the scenario can be walked through the agent SKILL.md
rules and `schemas/state_machine.yaml` **without contradiction** — every
transition is legal, every required artifact field has a defined source, and
the judge criteria produce the expected verdict.

### What this proves
- The state machine has no dead-ends or illegal transitions for these paths
- Each agent's required output fields are satisfiable from available input
- Judge rules are internally consistent (a PASS scenario isn't also a FIXER trigger)
- The spam/escalation gates fire on the right signals and stay quiet otherwise

### What this does NOT prove
- That a live model will actually fill artifacts correctly
- Behavior under real concurrency (two messages from one lead at once)
- Real cost and latency per lead (~7-10 agent calls)
- Robustness to inputs nobody thought to author a fixture for

---

## Test inventory

| Test | Scenario | Path exercised | Fixture |
|---|---|---|---|
| E2E-001 | Discovery → Judge | DISCOVERY artifact + verdict | `data/artifacts/e2e_judge_001.yaml` |
| E2E-002 | Qualification → Judge | QUALIFICATION (BANT) + verdict | `data/artifacts/e2e_judge_002.yaml` |
| E2E-003 | Hot lead full-flow | DISCOVERY→QUALIFICATION→OFFERING→CLOSING→CONVERSION | `data/e2e/e2e_003_fullflow_hot.yaml` |
| E2E-004 | Warm + objection "mahal" | OFFERING→OBJECTION→CLOSING→CONVERSION (no discount) | `data/e2e/e2e_004_fullflow_objection.yaml` |
| E2E-005 | Cold lead | DISCOVERY→QUALIFICATION→FOLLOW_UP (stops stage 2, anti-spam) | `data/e2e/e2e_005_fullflow_cold.yaml` |
| E2E-006 | Returning lead | FOLLOW_UP re-entry → CONVERSION (uses long memory) | `data/e2e/e2e_006_fullflow_returning.yaml` |
| E2E-007 | Edge cases (6) | scam blacklist, toxic scoring, off-topic guard, 3× escalation, loop detection | `data/e2e/e2e_007_edge_cases.yaml` |

**State coverage:** all 9 states reached at least once — DISCOVERY,
QUALIFICATION, OFFERING, OBJECTION, CLOSING, CONVERSION, FOLLOW_UP, BLACKLIST,
HUMAN_ESCALATION. All 7 specialist agents + judge are exercised.

---

## Fixtures vs runtime data

The repo intentionally tracks only synthetic fixtures:

- `data/e2e/**` — synthetic scenarios, **no PII** → committed to git
- `data/artifacts/**`, `data/leads/**`, `data/logs/**` — runtime output, may
  contain PII → **git-ignored** (`.gitignore`: `data/*` with `!data/e2e/`)

Never commit a fixture built from a real lead conversation without scrubbing PII.

---

## How to run a live validation (when ready)

Live validation is **not** part of v1.0. When you get there:

1. Install the skill pack (see README "Quick Start")
2. Replace `shared/products.yaml` template with real products
3. Load `nuxhub-orchestrator` and send a real inbound message
4. Compare the produced artifacts in `data/artifacts/` against the matching
   `data/e2e/` fixture — the design fixture is the expected-output oracle
5. Watch for: missing required fields, judge false-PASS, cost per lead, latency

A divergence between live output and the fixture is a real finding — investigate
whether the rule, the schema, or the fixture is wrong.

---

## Known issues (minor, non-blocking)

- `personality_type` is null during partial discovery — **by design**
  (confidence < 0.6 defers assignment rather than guessing)
- `conversation_summary` was occasionally missing in qualification artifacts —
  added to the schema and satisfied across all new fixtures
