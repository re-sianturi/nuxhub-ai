# NuxHub AI — Task Plan

## Fase 0: Scaffolding
Status: pending

- [ ] Buat struktur folder proyek
- [ ] Buat artifact schema definitions (YAML/JSON schema untuk handoff antar-agent)
- [ ] Buat shared config (objectives, state machine, personality profiles, objections DB)

## Fase 1: Core Infrastructure
Status: pending

- [ ] State Machine Engine — mengelola perpindahan antar state (NEW_LEAD → ... → FOLLOW_UP)
- [ ] Artifact Bus — mekanisme baca/tulis artifact antar agent via YAML file
- [ ] Memory System — short-term (session) + long-term (CRM-like, file-based)
- [ ] Context Manager — memastikan main context orchestrator tetap bersih

## Fase 2: Agent Skills (Specialist)
Status: pending

- [ ] Router Agent — klasifikasi lead masuk, tentukan state awal, delegasi ke specialist
- [ ] Discovery Agent — kumpulkan info lead (nama, bisnis, masalah, goal, budget, timeline)
- [ ] Qualification Agent — BANT scoring (0-100), tentukan hot/warm/cold
- [ ] Psychology Agent — profiling (analytical/driver/amiable/expressive), adjust tone
- [ ] Objection Agent — handle objections dari database, root cause analysis
- [ ] Offer Engine — problem→product mapping, munculkan offer di timing tepat
- [ ] Closing Agent — generate CTA sesuai state (direct buy/consultation/demo/visit)
- [ ] Follow Up Agent — recovery flow (1h, 3h, 7h, 30h)

## Fase 3: Orchestrator
Status: pending

- [ ] Main Orchestrator — baca context, tentukan agent mana yang dipanggil, manage handoff
- [ ] Delegation logic — orchestrator hanya kirim artifact (YAML) ke subagent, BUKAN full context
- [ ] Anti-pollution guard — verifikasi context size sebelum/sesudah subagent run

## Fase 4: QA & Fixer Loop
Status: pending

- [ ] Judge Agent — verifikasi output tiap agent sebelum handoff ke agent berikutnya
- [ ] Fixer Agent — terima error_report, perbaiki output, max 3 retry
- [ ] Circuit Breaker — 3x retry gagal → escalate ke human
- [ ] Spam Scorer — +10 off-topic, +20 toxic, +50 scam, +100 blacklist

## Fase 5: Human Escalation
Status: pending

- [ ] Escalation triggers — marah, komplain berat, refund, legal, custom deal, enterprise
- [ ] Handoff artifact — bikin artifact siap untuk human agent baca

## Fase 6: Analytics & Logging
Status: pending

- [ ] Conversation logger — log semua: lead masuk, discovery completed, qualified, offer, meeting, won, lost
- [ ] Metrics engine — hitung discovery rate, qualification rate, meeting rate, close rate
- [ ] Artifact audit trail — semua artifact disimpan untuk debugging

## Fase 7: Integration & Testing
Status: pending

- [ ] Integration test — simulasi full flow NEW_LEAD → CONVERSION
- [ ] Edge case test — spam, toxic, human escalation, loop detection
- [ ] Documentation — README, usage guide, agent configuration guide
