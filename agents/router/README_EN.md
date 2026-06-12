# Router Agent — User Guide & Business Outcomes

> **This is NOT a technical manual.** This is a business-friendly guide explaining: "What does Router Agent do for my business, and how do I use it?"

---

## 1. What is Router Agent? (Simple Language)

Imagine you have a **smart receptionist** at the front desk of your online store. Every time someone sends a message, this receptionist doesn't immediately try to sell. Instead, they listen first, then decide:

- **"This person genuinely wants to buy"** → send to sales
- **"This person is angry"** → send to manager
- **"This is a spammer"** → kick out without response
- **"This person chatted before but disappeared"** → send to follow-up team

**Router Agent = that smart receptionist.** It sits at the front door, checks everyone who comes in, and directs them to the right path.

---

## 2. Business Outcomes — What Does It Bring to Your Business?

### 2.1. No More Sales Team Wasting Time on Spam

| Before Router Agent | After Router Agent |
|---|---|
| Sales team replies to spammers: "Need fast loan?" | Spammer auto-blocked, sales never sees it |
| Team drains energy on prank chats | Prank chats redirected back to business topic, no sales distraction |
| 20% of sales time wasted on useless chats | Sales focuses 100% on leads who actually want to buy |

**Outcome:** Sales team productivity increases 20-30%. They chat with real buyers, not spammers.

### 2.2. No More Angry Leads Getting Robot Responses

| Before | After |
|---|---|
| Complaint "Refund!" gets reply: "We have a 10% discount promo" | Complaint immediately routed to human manager |
| Angry person gets angrier because of robot reply | Angry person handled by human with empathy |
| Bad reviews on Google / Instagram | Reviews stay positive because issues are handled seriously |

**Outcome:** Brand reputation protected. Angry leads are handled by humans, not pushed by AI that doesn't understand emotions.

### 2.3. Leads Who Chatted Before but Didn't Buy — They Don't Die

| Before | After |
|---|---|
| Person chatted yesterday, asked price, then disappeared. No follow-up. | Router remembers them. If they chat again, continue from where they left off, no "What's your name?" from scratch. |
| 60% of leads just ask questions, no nurture system | Cold leads saved, auto-follow-up at 1h/3h/7h/30h |
| Lead database sits unused | Every lead has a CRM file, complete history, can be picked up anytime |

**Outcome:** Conversion rate improves. Leads who "just asked" are nurtured, not discarded. Sales doesn't start from zero every chat.

### 2.4. No More "Wrong Call" to Sales

| Before | After |
|---|---|
| Person asks for enterprise custom deal, junior sales replies who has no authority | Enterprise deal goes straight to sales manager, not junior |
| Refund request handled by marketing team who can't refund | Refund request goes straight to billing team |
| Legal threat replied by a stupid chatbot | Legal threat goes straight to legal team, no wrong response |

**Outcome:** Fewer financial & legal losses. Big deals handled by authorized people. Sensitive issues not mishandled.

### 2.5. Every Lead Gets Treatment Matching Their "Quality"

Router labels them:
- **Hot lead** → straight to sales, don't wait
- **Warm lead** → nurture, follow up, give content
- **Cold lead** → save, follow up later, don't push
- **Spam** → block, no response
- **Angry** → human, immediately

**Outcome:** Automatic sales prioritization. No hot lead left behind because sales was busy replying to spam.

---

## 3. How Router Works (Analogy)

### Analogy: Hospital

Person enters hospital → Router = **triage nurse** at the ER front door.

1. **First**, check: "Is this person emergency? Lots of blood?" → ER
2. **Second**, check: "Does this person carry a virus?" → Isolation
3. **Third**, check: "Is this person just asking for pharmacy directions?" → Direct them
4. **Fourth**, check: "Is this person returning for a follow-up?" → Continue their medical record

Router Agent works the same. Every incoming chat:
1. **Spam check** → kick out or continue?
2. **Escalation check** → angry/legal/refund?
3. **Returning check** → chatted before?
4. **Routing** → direct to right agent

---

## 4. 5 Scenarios Router Handles

### Scenario A: Normal New Lead

**Input:**
```
User: "Hello, I need help getting more customers. Can you help?"
```

**Router works:**
1. Spam score? 0 → clean
2. Escalation? No angry keywords → continue
3. Returning lead? Never chatted before → new
4. Decision: **DISCOVERY** → delegate to Discovery Agent

**Output to user:**
```
Agent: "Of course, Sir. May I know what business you are currently running?"
```

**Business value:** Lead enters pipeline, starts qualification.

---

### Scenario B: Spammer

**Input:**
```
User: "NEED FAST LOAN? LOW INTEREST 0.1% TRANSFER NOW TO ACCOUNT 1234567890!!!"
```

**Router works:**
1. Spam score? 110 (off-topic +10, scam pattern +50, urgency manipulation +50)
2. Spam score ≥ 100 → **BLACKLIST**
3. No response sent
4. Save to blacklist

**Output to user:**
```
(no response)
```

**Business value:** Sales not disturbed. No team wastes time replying to spammers.

---

### Scenario C: Angry Person / Complaint

**Input:**
```
User: "I'm angry! Terrible service, I want my money back!"
```

**Router works:**
1. Spam score? 0 → not spam
2. Escalation? Keywords "angry" + "refund" → **ESCALATE = true**
3. Priority: high
4. Decision: **HUMAN_ESCALATION** → delegate to human, not AI

**Output to user:**
```
Agent: "We sincerely apologize for the inconvenience. I will connect you with our team who can assist directly."
```

**Business value:** Sensitive issues handled by humans. No wrong AI response making things worse.

---

### Scenario D: Returning Lead

**Input:**
```
User: "Hi, I asked about digital marketing packages yesterday. Any price update?"
```

**Router works:**
1. Spam score? 0
2. Escalation? No
3. Returning lead? Yes, lead_id found in CRM
4. Previous state: DISCOVERY (not finished yesterday)
5. Decision: **DISCOVERY** (re-entry) → delegate to Discovery Agent with old data

**Output to user:**
```
Agent: "Hello Mr. [name], glad to chat again. Yesterday we discussed your business in Jakarta. Let me continue — may I know, how many target customers per month do you expect?"
```

**Business value:** No need to ask name, location, business again. Continue from yesterday. Sales not seen as "forgetting" customers.

---

### Scenario E: Off-topic (Prank Chat)

**Input:**
```
User: "Hello beautiful, who are you?"
```

**Router works:**
1. Spam score? 10 (light off-topic)
2. Spam score < 100 → not blocked
3. Escalation? No
4. Decision: **DISCOVERY** but redirect back

**Output to user:**
```
Agent: "Hello! I'm Ucok, assistant from NuxHub. I can help with your digital marketing needs. Is there anything I can assist you with?"
```

**Business value:** Prank chat doesn't reach sales. Redirected back to business topic. If still pranking, spam score rises.

---

## 5. How to Use Router Agent (Step by Step)

### Step 1: Install Skill

Copy skill file to Hermes folder:
```bash
mkdir -p ~/.hermes/skills/nuxhub-router
cp agents/router/SKILL.md ~/.hermes/skills/nuxhub-router/
```

### Step 2: Ensure Supporting Files Exist

Router needs 2 configuration files:
```
/shared/spam_gate.yaml        ← spam scoring rules
/shared/escalation_gate.yaml   ← escalation rules
```

Ensure these files exist in your project folder.

### Step 3: Send Input to Router

Send input in this format:
```yaml
lead_id: null                   # null = new lead, "xxx" = old lead
raw_message: "Hello, I need help..."
spam_score: 0                   # from Spam Gate (run before Router)
spam_flags: []
escalate_flag: false            # from Escalation Gate
escalate_reason: null
long_memory: null               # from CRM (if returning lead)
```

### Step 4: Read Router Output

Router generates artifact:
```yaml
state_assignment: "DISCOVERY"   # or BLACKLIST, HUMAN_ESCALATION, etc.
delegated_agent: "discovery"     # which agent should run next
reason: "New lead, spam score 0, no escalation"
is_returning_lead: false
```

### Step 5: Run Next Agent

Based on `delegated_agent`, run next agent:
- `discovery` → load skill nuxhub-discovery
- `null` → stop (for BLACKLIST or HUMAN_ESCALATION)

---

## 6. Configurable Settings (No Coding Required)

### 6.1. Change Spam Threshold

Edit `shared/spam_gate.yaml`:
```yaml
blacklist:
  score: 100    # ← change this number. Default 100. Lower = more sensitive.
```

### 6.2. Add Escalation Keywords

Edit `shared/escalation_gate.yaml`:
```yaml
angry:
  keywords: ["angry", "upset", "disappointed", "terrible"]
  # ← add new keywords here
```

### 6.3. Change Escalation Response

Edit `shared/escalation_gate.yaml`:
```yaml
angry:
  message_to_lead: "We apologize, I will connect you..."
  # ← change this text to match your brand voice
```

### 6.4. Change Initial State for New Leads

Edit `agents/router/SKILL.md` in the "New Lead" section:
```
IF lead_id == null:
    → state_assignment: DISCOVERY    # ← change to another state if needed
```

---

## 7. Metrics & KPIs to Monitor

| Metric | How to Calculate | Target |
|---|---|---|
| **Spam Block Rate** | Blacklisted / total chats | < 5% (if too high, spam gate too sensitive) |
| **Escalation Rate** | Escalated to human / total chats | < 15% (if high, too many issues or AI not smart enough) |
| **Returning Lead Recognition** | Recognized returning / returning who chatted | > 90% (if low, CRM not working) |
| **Routing Accuracy** | Correct routing / total routing | Measure manually via sample review |
| **Time to Route** | Router input to output time | < 2 seconds |

---

## 8. FAQ (Business Questions)

### Q: Does Router understand English? Mixed languages?
**A:** Yes. Keywords in spam gate and escalation gate can be edited to add any language. Typos and mixed languages are tolerated.

### Q: If someone chats just "hi", is it spam?
**A:** No. Exception rule: "Short message (1-3 words) from new lead = tolerance." So "hi" goes to Discovery, not blocked.

### Q: If an elderly person types weirdly, will they get blocked?
**A:** No. Exception: "Typos or mixed language = non-tech-savvy or elderly, not spam."

### Q: Can this be used for WhatsApp / Telegram / Instagram?
**A:** Yes. Router doesn't care about platform. It only reads `raw_message`. Platform (WA, IG, Telegram) = gateway that sends message to Router. Just install the right gateway.

### Q: If someone is angry in a group chat, will they be escalated?
**A:** Yes, as long as escalation keywords are detected. But for group chats, escalation usually goes to group admin, not sales manager.

### Q: What if someone pretends to want to buy but is actually a spammer?
**A:** Spam score is cumulative. Every turn is counted. Someone can start with "Hello, I want to buy" (score 0), then turn 5 starts spamming. Score accumulates, eventually blocked. So spammers can't stay long.

### Q: Can Router be used for businesses other than digital marketing?
**A:** Yes. Change configuration in `shared/spam_gate.yaml` and `shared/escalation_gate.yaml`. But routing logic (NEW_LEAD → DISCOVERY) stays the same for all businesses.

---

## 9. Summary (One Page)

**Router Agent = the front gate of your online store.**

It does 5 things:
1. **Filter spam** → block spammers, sales not disturbed
2. **Detect problems** → angry people go straight to human
3. **Recognize old customers** → no more "What's your name?" again
4. **Direct to right sales** → hot to closing, warm to nurture, cold to follow-up
5. **Save everything** → every chat logged, auditable

**You don't need coding to change behavior.** Edit YAML files, change keywords, change thresholds. Router will re-read.

**Resume later:**
```
load /home/ubuntu/projects/nuxhub-ai/agents/router/README_EN.md and continue
```
