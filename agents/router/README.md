# Router Agent — Panduan Penggunaan & Business Outcome

> **Ini bukan manual teknis.** Ini penjelasan buat orang bisnis yang mau tau: "Router Agent ini ngapain buat bisnis gue, dan gimana cara pakainya?"

---

## 1. Router Agent itu Apa? (Bahasa Bayi)

Bayangkan lo punya **resepsionis pintar** di depan toko online lo. Tiap kali ada orang chat, resepsionis ini nggak langsung jualan. Dia dengerin dulu, terus putusin:

- **"Ini orang beneran mau beli"** → suruh ke sales
- **"Ini orang marah"** → suruh ke manager
- **"Ini spammer"** → usir tanpa di respon
- **"Ini orang yang pernah chat tapi kabur"** → kasih ke tim follow up

**Router Agent = resepsionis pintar itu.** Dia duduk di depan pintu, ngecek semua orang yang masuk, terus arahin ke jalur yang tepat.

---

## 2. Business Outcome — Apa yang Dibawakan ke Bisnis Lo?

### 2.1. Gak Ada Lagi Sales Team Kehabisan Waktu di Spam

| Sebelum Router Agent | Sesudah Router Agent |
|---|---|
| Tim sales bales chat spammer "Butuh pinjaman cepat?" | Spammer di-block otomatis, sales gak liat |
| Tim kehabisan energi di chat iseng | Chat iseng diarahkan kembali ke topik bisnis, gak ganggu sales |
| 20% waktu sales habis di chat gak penting | Sales fokus 100% di lead yang beneran mau beli |

**Outcome:** Sales team produktivitas naik 20-30%. Mereka chat sama orang yang beneran mau beli, bukan spammer.

### 2.2. Gak Ada Lagi Lead Marah di-Bales Robot

| Sebelum | Sesudah |
|---|---|
| Orang komplain "Refund!" di-bales "Kami punya promo diskon 10%" | Orang komplain langsung diarahkan ke human manager |
| Orang marah makin marah karena di-bales robot | Orang marah ditangani manusia dengan empathy |
| Review buruk di Google / Instagram | Review tetap baik karena masalah ditangani serius |

**Outcome:** Brand reputation terjaga. Lead yang marah ditangani manusia, bukan di-push sama AI yang gak ngerti emosi.

### 2.3. Lead yang Pernah Chat Tapi Gak Jadi Beli — Gak Hangus

| Sebelum | Sesudah |
|---|---|
| Orang chat kemarin, tanya harga, lalu kabur. Gak ada yang follow up. | Router ingat dia. Kalau dia chat lagi, langsung lanjut dari tadi, gak tanya "Siapa namanya?" dari awal. |
| 60% lead cuma tanya-tanya doang, gak ada nurture system | Cold lead di-save, di-follow up otomatis 1h/3h/7h/30h |
| Database lead gak ada yang manfaatin | Tiap lead punya file CRM, history lengkap, bisa di-pickup kapanpun |

**Outcome:** Conversion rate naik. Lead yang "tanya doang" di-nurture, gak di-buang. Sales gak mulai dari nol tiap chat.

### 2.4. Gak Ada Lagi "Salah Sambung" ke Sales

| Sebelum | Sesudah |
|---|---|
| Orang minta custom deal enterprise, di-bales sama junior sales yang gak punya authority | Enterprise deal langsung ke sales manager, gak ke junior |
| Orang minta refund, di-bales sama tim marketing yang gak bisa refund | Refund request langsung ke billing team |
| Legal threat di-bales sama chatbot tolol | Legal threat langsung ke tim legal, gak ada response yang salah |

**Outcome:** Lebih sedikit kerugian finansial & legal. Deal yang besar ditangani orang yang berwenang. Masalah sensitif gak di-salah-handle.

### 2.5. Semua Lead Dapat Perlakuan Sesuai "Kualitas"-nya

Router kasih label:
- **Hot lead** → langsung ke sales, jangan di-tunggu
- **Warm lead** → nurture, follow up, kasih konten
- **Cold lead** → save, follow up nanti, gak usah di-push
- **Spam** → block, gak usah di-respon
- **Marah** → human, segera

**Outcome:** Sales prioritization otomatis. Gak ada lead hot yang di-tinggal karena sales sibuk bales spam.

---

## 3. Cara Kerja Router (Analogi)

### Analogi: Rumah Sakit

Orang masuk rumah sakit → Router = **triage perawat** di depan IGD.

1. **Pertama**, dia liat: "Ini orang darurat? Banyak darah?" → IGD
2. **Kedua**, dia liat: "Ini orang bawa virus?" → Isolasi
3. **Ketiga**, dia liat: "Ini orang cuma tanya arah ke farmasi?" → Arahkan
4. **Keempat**, dia liat: "Ini orang yang pernah rawat, mau kontrol?" → Lanjut rekam medisnya

Router Agent kerjaannya sama. Tiap chat masuk dia:
1. **Spam check** → usir atau lanjut?
2. **Escalation check** → marah/legal/refund?
3. **Returning check** → pernah chat sebelumnya?
4. **Routing** → arahin ke agent yang tepat

---

## 4. 5 Skenario yang Ditangani Router

### Skenario A: Lead Normal yang Baru Chat

**Input:**
```
User: "Halo, saya butuh bantuan untuk dapat lebih banyak customer. Bisa bantu?"
```

**Router kerja:**
1. Spam score? 0 → bersih
2. Escalation? Tidak ada keyword marah → lanjut
3. Returning lead? Belum pernah chat → baru
4. Decision: **DISCOVERY** → delegate ke Discovery Agent

**Output ke user:**
```
Agent: "Tentu, Pak. Boleh saya tahu bisnis apa yang sedang Bapak jalankan?"
```

**Business value:** Lead masuk pipeline, mulai di-qualify.

---

### Skenario B: Spammer

**Input:**
```
User: "BUTUH PINJAMAN CEPAT? BUNGA RENDAH 0.1% TRANSFER SEKARANG KE REKENING 1234567890!!!"
```

**Router kerja:**
1. Spam score? 110 (off-topic +10, scam pattern +50, urgency manipulation +50)
2. Spam score ≥ 100 → **BLACKLIST**
3. Tidak kirim response apapun
4. Simpan ke blacklist

**Output ke user:**
```
(tidak ada response)
```

**Business value:** Sales gak keganggu. Gak ada tim yang bales spammer.

---

### Skenario C: Orang Marah / Komplain

**Input:**
```
User: "Saya marah! Layanan jelek banget, saya mau refund uang saya!"
```

**Router kerja:**
1. Spam score? 0 → bukan spam
2. Escalation? Keyword "marah" + "refund" → **ESCALATE = true**
3. Priority: high
4. Decision: **HUMAN_ESCALATION** → delegate ke human, bukan AI

**Output ke user:**
```
Agent: "Mohon maaf atas ketidaknyamanannya. Saya akan sambungkan Bapak dengan tim kami yang bisa membantu langsung."
```

**Business value:** Masalah sensitif ditangani manusia. Gak ada response AI yang salah bikin makin parah.

---

### Skenario D: Lead yang Pernah Chat (Returning Lead)

**Input:**
```
User: "Halo, saya kemarin tanya soal paket digital marketing. Ada update harga?"
```

**Router kerja:**
1. Spam score? 0
2. Escalation? Tidak
3. Returning lead? Ya, lead_id ditemukan di CRM
4. Previous state: DISCOVERY (belum selesai kemarin)
5. Decision: **DISCOVERY** (re-entry) → delegate ke Discovery Agent dengan data lama

**Output ke user:**
```
Agent: "Halo Pak [nama], senang chat lagi. Kemarin kita sampai di bahas bisnis Bapak di Jakarta. Sekarang saya bantu lanjut ya — kalau boleh tahu, target customer per bulan yang Bapak harapkan?"
```

**Business value:** Gak perlu tanya nama, lokasi, bisnis lagi. Lanjut dari kemarin. Sales gak dianggap "gak ingat" customer.

---

### Skenario E: Off-topic (Chat Iseng)

**Input:**
```
User: "Halo cantik, kamu siapa?"
```

**Router kerja:**
1. Spam score? 10 (off-topic ringan)
2. Spam score < 100 → gak di-block
3. Escalation? Tidak
4. Decision: **DISCOVERY** tapi arahkan kembali

**Output ke user:**
```
Agent: "Halo! Saya Ucok, asisten dari NuxHub. Saya bisa bantu untuk kebutuhan digital marketing Bapak/Ibu. Ada yang bisa saya bantu?"
```

**Business value:** Chat iseng gak ke sales. Diarahkan balik ke topik bisnis. Kalau masih iseng terus, baru naik ke spam.

---

## 5. Cara Pakai Router Agent (Step by Step)

### Langkah 1: Install Skill

Copy file skill ke folder Hermes:
```bash
mkdir -p ~/.hermes/skills/nuxhub-router
cp agents/router/SKILL.md ~/.hermes/skills/nuxhub-router/
```

### Langkah 2: Pastikan File Pendukung Ada

Router butuh 2 file konfigurasi:
```
/shared/spam_gate.yaml        ← aturan spam scoring
/shared/escalation_gate.yaml   ← aturan escalation
```

Pastikan file ini ada di project folder.

### Langkah 3: Panggil Router

Kirim input ke Router dengan format:
```yaml
lead_id: null                   # null = lead baru, "xxx" = lead lama
raw_message: "Halo, saya butuh bantuan..."
spam_score: 0                   # dari Spam Gate (jalankan dulu sebelum Router)
spam_flags: []
escalate_flag: false            # dari Escalation Gate
escalate_reason: null
long_memory: null               # dari CRM (jika returning lead)
```

### Langkah 4: Baca Output Router

Router akan generate artifact:
```yaml
state_assignment: "DISCOVERY"   # atau BLACKLIST, HUMAN_ESCALATION, dll
delegated_agent: "discovery"     # agent mana yang harus jalan selanjutnya
reason: "Lead baru, spam score 0, no escalation"
is_returning_lead: false
```

### Langkah 5: Jalankan Agent Berikutnya

Berdasarkan `delegated_agent`, jalankan agent selanjutnya:
- `discovery` → load skill nuxhub-discovery
- `null` → stop (untuk BLACKLIST atau HUMAN_ESCALATION)

---

## 6. Konfigurasi yang Bisa Diubah (Tanpa Coding)

### 6.1. Ganti Spam Threshold

Edit `shared/spam_gate.yaml`:
```yaml
blacklist:
  score: 100    # ← ganti angka ini. Default 100. Lebih kecil = lebih sensitif.
```

### 6.2. Tambah Keyword Escalation

Edit `shared/escalation_gate.yaml`:
```yaml
marah:
  keywords: ["marah", "kesal", "kecewa", "parah"]
  # ← tambah keyword baru di sini
```

### 6.3. Ganti Response Escalation

Edit `shared/escalation_gate.yaml`:
```yaml
marah:
  message_to_lead: "Mohon maaf, saya akan sambungkan..."
  # ← ganti teks ini sesuai brand voice lo
```

### 6.4. Ganti State Awal untuk Lead Baru

Edit `agents/router/SKILL.md` di bagian "Lead Baru":
```
IF lead_id == null:
    → state_assignment: DISCOVERY    # ← ganti ke state lain jika perlu
```

---

## 7. Metrics & KPI yang Bisa Dipantau

| Metric | Cara Hitung | Target |
|---|---|---|
| **Spam Block Rate** | Jumlah blacklist / jumlah total chat | < 5% (kalau terlalu banyak, spam gate terlalu sensitif) |
| **Escalation Rate** | Jumlah escalate ke human / jumlah total chat | < 15% (kalau tinggi, berarti banyak masalah atau AI belum cukup pintar) |
| **Returning Lead Recognition** | Returning lead yang dikenali / returning lead yang chat | > 90% (kalau rendah, CRM gak jalan) |
| **Routing Accuracy** | Routing yang benar / total routing | Diukur manual via review sampel |
| **Time to Route** | Waktu Router dari input sampai output | < 2 detik |

---

## 8. FAQ (Pertanyaan yang Sering Ditanyakan Bisnis)

### Q: Router ini ngerti bahasa Indonesia gak? Campur Inggris?
**A:** Ngerti. Keyword di spam gate dan escalation gate bisa di-edit tambah bahasa apa pun. Typo dan bahasa campur masih di-toleransi.

### Q: Kalau orang chat "hai" doang, dianggap spam gak?
**A:** Gak. Ada exception rule: "Pesan pendek (1-3 kata) dari lead baru = toleransi." Jadi "hai" diarahkan ke Discovery, gak di-block.

### Q: Kalau orang tua yang typing-nya aneh, ke-block gak?
**A:** Gak. Ada exception: "Typo atau bahasa campur = gaptek atau orang tua, bukan spam."

### Q: Router ini bisa di-pake untuk WhatsApp / Telegram / Instagram?
**A:** Bisa. Router gak peduli platform. Dia cuma baca `raw_message`. Platform (WA, IG, Telegram) = gateway yang kirim pesan ke Router. Lo tinggal pasang gateway yang sesuai.

### Q: Kalau lead marah di group chat, di-escalate juga?
**A:** Ya, selama keyword escalation terdeteksi. Tapi untuk group chat, biasanya escalation-nya ke admin grup, bukan ke sales manager.

### Q: Gimana kalau orang ngaku mau beli tapi ternyata spammer?
**A:** Spam score itu cumulative. Tiap turn dihitung. Orang bisa mulai dengan "Halo, saya mau beli" (score 0), lalu turn 5 mulai spam. Score numpuk, akhirnya ke-block. Jadi gak mungkin spammer lama-lama di-pihak.

### Q: Bisa gak Router di-pake buat bisnis lain selain digital marketing?
**A:** Bisa. Ganti konfigurasi di `shared/spam_gate.yaml` dan `shared/escalation_gate.yaml`. Tapi logic routing (NEW_LEAD → DISCOVERY) tetap sama untuk semua bisnis.

---

## 9. Summary (1 Halaman)

**Router Agent = Gate depan toko online lo.**

Dia kerjanya 5 hal:
1. **Filter spam** → block spammer, sales gak ganggu
2. **Detect masalah** → orang marah langsung ke human
3. **Kenali customer lama** → gak tanya "Siapa namanya?" lagi
4. **Arahkan ke sales yang tepat** → hot ke closing, warm ke nurture, cold ke follow up
5. **Save everything** → tiap chat di-log, bisa di-audit

**Lo gak perlu coding buat ganti behavior.** Edit file YAML, ganti keyword, ganti threshold. Router bakal baca ulang.

**Resume nanti:**
```
load /home/ubuntu/projects/nuxhub-ai/agents/router/README.md dan lanjutin
```
