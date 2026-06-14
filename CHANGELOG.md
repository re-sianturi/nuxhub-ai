# Changelog

All notable changes to NuxHub AI are documented here.
Format loosely follows [Keep a Changelog](https://keepachangelog.com/).

---

## [1.0.0] — 2026-06-14

First foundation release. Multi-agent conversational sales pipeline,
**design-verified** (not yet live-run validated — see `docs/TESTING.md`).

### Added
- **7 specialist agents** (`agents/*/SKILL.md`): router, discovery,
  qualification, objection, closing, judge, follow_up
- **Orchestrator** (`orchestrator/SKILL.md`) — pipeline coordinator with a
  2000-token context guard so subagents never receive full conversation history
- **Schemas** — `artifact_schemas.yaml` (8 mandatory fields per artifact),
  `state_machine.yaml` (7 states + transition rules)
- **Shared knowledge** — objections (12+), products (template), personalities
  (4 profiles), spam_gate, escalation_gate, context_guard, memory_system,
  fixer_circuit_breaker, analytics (22 events / 12 metrics)
- **Isolated QA loop** — judge agent in a separate context, fixer with max 3
  retries, circuit breaker → human escalation on repeated failure
- **Follow-up engine** — recovery at 1h / 3h / 7h / 30h
- **E2E design-verification** — 7/7 PASS; full-flow 4/4 (hot, objection, cold,
  returning) + edge cases 6/6 (scam, toxic, 3× escalation, loop detection)
- **Docs** — README, ARCHITECTURE (14 layers), RESEARCH, TESTING, and this changelog

### Changed
- `.gitignore` now tracks synthetic fixtures (`data/e2e/`) while excluding
  PII-bearing runtime data (`data/artifacts/`, `data/leads/`, `data/logs/`)
- `qualification` artifact schema gained `conversation_summary`
- README status + roadmap rewritten to separate design verification from
  live-run validation, and v1.0 scope from production readiness

### Known issues
- `personality_type` null during partial discovery (by design, confidence < 0.6)
- No live-run validation yet — all PASS results are logical/by-design

### Not included (production readiness — see README roadmap)
- Live inference validation, DB-backed state persistence with locking,
  real escalation notifications, messaging gateways, cost tracking, metrics
  dashboard, real `products.yaml`
