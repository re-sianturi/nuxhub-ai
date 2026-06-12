# NuxHub AI — Research: Best Practices & Common Pitfalls

> Sumber: MAST taxonomy (NeurIPS 2025, 1.600+ traces), Orq.ai, Augment Code, MindStudio, Azure Architecture Center

## Best Practices

### 1. Handoff Pattern (JSON/YAML artifacts)
- Output antar-agent HARUS terstruktur (JSON/YAML), bukan conversational prose
- Schema dulu, prompt belakangan — jangan harap output rapi dari prompt aja
- Format: JSON = machine-to-machine, Markdown = human-machine hybrid, HTML = rendering final
- Wajib ada field `status`, `error_code`, `confidence_score`

### 2. Specification-Driven Development
- Setiap agent punya JSON Schema kontrak: agent_id, role, capabilities, constraints, success_criteria
- Living specs — update specs saat agent selesai kerja
- Field harus typed: ISO 8601 date, integer count, boolean flag, array list

### 3. Clear Role Boundaries
- Satu resource (DB table, API, file) = satu agent owner
- Role overlap = duplikasi kerja = konflik = loop tak berujung
- Agent kecil spesialis > agent besar monolithic

### 4. Orchestration Patterns (dari Azure)
- Sequential: pipeline linear A → B → C
- Handoff: dynamic delegation, router-based
- Concurrent: parallel agents + aggregator
- Untuk NuxHub: kombinasi sequential + handoff

### 5. Independent Validation (QA/Fixer Loop)
- Judge/verifier agent TERPISAH konteksnya dari agent produksi
- Prompt verifier berbeda + scoring criteria tersembunyi
- Kalau verifier share context sama producer → jadi "collective delusion"

### 6. MCP / JSON-RPC untuk Agent Communication
- JSON-RPC 2.0 sebagai format message standar
- {jsonrpc, id, method, params} structure
- Bisa pakai file-based YAML/JSON sebagai gantinya untuk simplicity

## Common Pitfalls

### Pitfall 1: Specification Ambiguity (41.77% failure)
- Agent misinterpret role → duplikasi kerja → skip verifikasi
- **Fix:** JSON schema ketat + explicit ownership + auto-constraint validation

### Pitfall 2: Coordination Breakdowns
- Agent A kirim prose, Agent B harus parse prose → cascade error
- **Fix:** Structured handoff artifact (YAML/JSON) selalu

### Pitfall 3: Verification Gaps (21% failure)
- Output tidak dicek → error lolos ke downstream
- **Fix:** Judge agent dengan context terisolasi

### Pitfall 4: Context Pollution
- Single agent dengan 15+ tools → cognitive overload
- **Fix:** Multi-agent specialist, tiap agent pegang max 3-5 tools

### Pitfall 5: Compounding Errors
- Salah kecil di awal → cascade besar di ujung
- **Fix:** Verifier di setiap handoff point

### Pitfall 6: Poor Termination Conditions
- Agent loop tak berujung, task 10 detik jalan selamanya
- **Fix:** max_iterations, timeout, explicit stop criteria

### Pitfall 7: Coordination Costs Scale Exponentially
- 4 agents = 6 failure points, 10 agents = 45 failure points
- **Fix:** Jangan kebanyakan agent. 5-7 specialist cukup.

### Pitfall 8: Memory Decay
- Agent "lupa" keputusan sebelumnya → restart workflow
- **Fix:** Resumable sessions + artifact-based state passing

## QA/Fixer Loop Pattern

```
Producer Agent → Output Artifact → Judge Agent → PASS? → Lanjut
                                                   ↓ FAIL?
                                               Fixer Agent → Retry (max 3x)
                                                   ↓ STILL FAIL?
                                               Human Escalation
```

- Judge: isolated context, baca output artifact vs original spec
- Fixer: terima error_report dari judge, perbaiki output
- Circuit breaker: 3x retry gagal → escalate ke human
- Log semua untuk analytics
