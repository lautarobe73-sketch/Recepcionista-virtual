Recepcionista-virtual
Agente autonomo que agenda citas
[Uploading READ# 🤖 Virtual Receptionist Agent — WhatsApp

> Autonomous AI-powered receptionist built with n8n + GPT-4o.  
> Handles appointment scheduling, reminders, and customer queries **24/7 via WhatsApp** — zero human intervention.

**Status:** ✅ Production (active clients: barbershop, dental clinic, aesthetic center)  
**Messages processed:** ~30/day per client  
**Node count:** 39 nodes

---

## 📊 Impact

| Metric | Result |
|---|---|
| Admin workload reduction | 80% |
| Operation hours | 24/7 autonomous |
| Message types handled | Text + Audio (voice notes) |
| Human intervention required | None (escalation only for edge cases) |
| Active clients | 3 (barbershop · dental · aesthetic center) |

---

## 🛠️ Stack

- **Automation:** n8n (self-hosted)
- **AI:** OpenAI GPT-4o (main agent) · GPT-4o-mini (guardrails)
- **Voice:** OpenAI Whisper (audio transcription)
- **Messaging:** Evolution API (WhatsApp Business)
- **Calendar:** Google Calendar API (CRUD)
- **CRM:** Google Sheets
- **Database:** PostgreSQL (persistent conversation memory)
- **Notifications:** Automated escalation to owner via WhatsApp

---

## ⚙️ How it works

```
Client message (text or audio)
        │
        ▼
[Evolution API Webhook] ──► n8n receives message
        │
        ▼
[Message Router] ── audio? ──► [Whisper] ── transcription ──┐
        │                                                     │
        └─────────────────────────────────────────────────────┘
        │
        ▼
[PostgreSQL] ◄── load conversation memory
        │
        ▼
[GPT-4o] analyzes intent
        │
        ├── Schedule appointment ──► Google Calendar API (create)
        ├── Check availability  ──► Google Calendar API (read)
        ├── Modify appointment  ──► Google Calendar API (update)
        ├── Cancel appointment  ──► Google Calendar API (delete)
        ├── Lookup client       ──► Google Sheets CRM (search)
        └── Out of scope        ──► Escalate to owner (WhatsApp)
        │
        ▼
[GPT-4o-mini Guardrails] validates response
        │
        ▼
[Evolution API] sends reply to client
        │
        ▼
[PostgreSQL] saves updated conversation memory
```

---

## 🏗️ Architecture highlights

- **39-node n8n workflow** with multi-branch conditional logic
- **Persistent memory** in PostgreSQL — agent remembers previous interactions per client
- **Full CRUD** on Google Calendar: create, read, update, delete appointments
- **Guardrail layer** with GPT-4o-mini to prevent off-topic or harmful responses
- **Automatic escalation** to business owner when query is out of scope
- **Global error handling** with operator notification on flow failure
- **Dual input support:** text messages and WhatsApp voice notes (transcribed via Whisper)

---

## 📁 Repository contents

```
📁 virtual-receptionist-whatsapp/
│
├── README.md
├── flow/
│   └── recepcionista_virtual_v3.json    # n8n exported workflow
├── docs/
│   ├── architecture_diagram.png         # Full flow screenshot
│   └── demo_screenshot.png              # n8n canvas view
└── .gitignore
```

---

## 🔒 Privacy note

All client data has been anonymized. The exported n8n flow contains no real credentials, phone numbers, or personal information. A live demo is available upon request.

---

## 📫 Contact

**Lautaro Benelli** — AI Automation Developer  
[linkedin.com/in/lautaro-benelli-681819335](https://www.linkedin.com/in/lautaro-benelli-681819335/) · lautarobe73@gmail.com
ME_recepcionista_virtual.md…]()
