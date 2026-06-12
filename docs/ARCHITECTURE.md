# NuxHub AI — Architecture Reference

## Layer 1 — Business Objective
Agent harus punya tujuan akhir yang jelas:
- Lead masuk → booking meeting
- Lead masuk → checkout
- Lead masuk → submit form
- Lead masuk → datang ke toko
- Lead masuk → kirim dokumen

Semua percakapan harus mengarah ke objective. Kalau tidak, AI ngobrol panjang tanpa menghasilkan.

## Layer 2 — User Journey State Machine
State-based, BUKAN intent-based. State lebih stabil dari intent.

```
NEW_LEAD → DISCOVERY → QUALIFICATION → OFFERING → OBJECTION → CLOSING → CONVERSION → FOLLOW_UP
```

Agent selalu tahu user di state mana.

## Layer 3 — Discovery Framework
Kumpulkan informasi dulu, jangan jualan dulu:
- Nama, Lokasi, Bisnis, Masalah, Goal, Budget, Timeline, Decision maker

Output: JSON profile terisi.

## Layer 4 — Qualification (BANT)
- Budget: Ada?
- Authority: Keputusan di tangan siapa?
- Need: Butuh?
- Timeline: Kapan mulai?

Skor 0-100:
- 80+ : Hot Lead
- 50-80: Warm Lead
- <50: Cold Lead

## Layer 5 — Psychological Profiling
4 tipe:
- Analytical: banyak tanya data → kasih data
- Driver: mau cepat → kasih rekomendasi tegas
- Amiable: banyak cerita → empati
- Expressive: antusias → match energi

## Layer 6 — Conversation Memory
- Short Memory: percakapan sekarang
- Long Memory (CRM): pernah chat, beli, meeting, komplain

Agent wajib baca sebelum balas.

## Layer 7 — Objection Handling
Database objections: Mahal, Belum yakin, Nanti dulu, Lagi mikir, Sudah ada vendor, Tidak ada budget.

Tiap objection punya: Root Cause, Response, Follow Up Question.
"Mahal" → bukan harga, value belum jelas → gali.

## Layer 8 — Hypnotic Selling (hati-hati, jangan manipulatif)
- Problem Amplification: "Apa dampaknya kalau tidak selesai 6 bulan?"
- Future Pacing: "Kalau target tercapai, apa yang berubah?"
- Contrast: "Saat ini vs target?"
- Gap Selling: Current State → Desired State → Gap (bukan produk)

## Layer 9 — Offer Engine
Problem → Produk mapping. Bukan lempar semua produk.
Rule: minimal discovery selesai dulu.

## Layer 10 — Closing Engine
CTA beda: Direct Buy, Consultation, Demo, Visit.

## Layer 11 — Recovery Flow
90% tidak beli. Follow up: 1 hari, 3 hari, 7 hari, 30 hari (reactivation).

## Layer 12 — Anti Spam
Spam Score (bukan block langsung):
- +10 off-topic
- +20 toxic
- +50 scam
- +100 blacklist

Jangan agresif — orang tua, gaptek, typo, bahasa campur bukan spam.

## Layer 13 — Human Escalation
Trigger: Marah, Komplain berat, Refund, Legal, Custom deal, Enterprise → langsung manusia.

## Layer 14 — Analytics
Track: Lead masuk, Discovery completed, Qualified, Offer shown, Meeting booked, Won, Lost.
Hitung: Discovery Rate, Qualification Rate, Meeting Rate, Close Rate.

## Arsitektur Multi-Agent
```
WhatsApp → Gateway → Orchestrator → State Manager → Memory → Lead Profile
                                         ↓
            Qualification Engine → Psychology Engine → Knowledge Base
                                         ↓
            Offer Engine → CRM → Human Handoff
```

Agent spesialis (JANGAN SATU AGENT BESAR):
```
Router Agent → Discovery Agent → Qualification Agent → Objection Agent → Closing Agent → Follow Up Agent
```
