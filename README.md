# 🤖 Multi-Agent Workflow Automation with n8n

> AI-driven workflow orchestration system that automates repetitive business operations across CRM, email, calendar, and communication tools using specialized agent architecture.

## 🎯 Problem Statement

Business teams lose significant productivity switching between disconnected tools:

**Typical workflow:**
1. Receive customer email → Check CRM for context
2. Update deal stage → Schedule follow-up meeting  
3. Notify account manager in Slack → Trigger backend APIs

## 💡 Solution

An intelligent multi-agent system that orchestrates end-to-end workflows autonomously:

- ✅ Triages incoming emails and drafts contextual replies
- ✅ Updates CRM records automatically with fuzzy matching
- ✅ Schedules meetings across multiple calendars
- ✅ Notifies team members in Slack with rich context
- ✅ Triggers backend APIs for fulfillment workflows

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    n8n Workflow Platform                    │
│                      (Self-Hosted)                          │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                   Manager Workflow                          │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  1. Intent Detection (GPT-4)                        │   │
│  │  2. Task Decomposition                              │   │
│  │  3. Agent Selection & Routing                       │   │
│  │  4. State Management (Redis)                        │   │
│  │  5. Error Handling & Retry Logic                    │   │
│  └─────────────────────────────────────────────────────┘   │
└───────┬─────────────┬─────────────┬─────────────┬───────────┘
        │             │             │             │
   ┌────▼────┐   ┌───▼────┐   ┌────▼─────┐  ┌───▼─────┐
   │  Mail   │   │Calendar│   │   CRM    │  │  Slack  │
   │ Agent   │   │ Agent  │   │  Agent   │  │  Agent  │
   └────┬────┘   └───┬────┘   └────┬─────┘  └───┬─────┘
        │            │              │             │
        ▼            ▼              ▼             ▼
   ┌─────────────────────────────────────────────────────┐
   │              External Integrations                  │
   │  • IMAP/SMTP    • Google Calendar  • HubSpot CRM   │
   │  • OAuth2       • Zoom API         • Slack Web API │
   └─────────────────────────────────────────────────────┘
```

## 🤖 Agent Architecture

### **1. MailAgent** - Email Triage & Response

### **2. CalendarAgent** - Meeting Scheduling

### **3. CRM-Agent** - Customer Record Management

### **4. SlackAgent** - Team Communication

## 🧠 Central Manager Logic

### **2. Task Decomposition**
Complex requests → Sequential subtasks:
```
"Schedule demo and update CRM" 
  → CalendarAgent: create_event
  → CRM-Agent: update_deal_stage  
  → SlackAgent: notify_account_manager
```

## 🛠️ Tech Stack

| Component | Technology | Purpose |
|-----------|-----------|---------|
| **Orchestration** | n8n (self-hosted) | Workflow automation, visual editor |
| **AI/ML** | OpenAI GPT-4 | Intent classification, entity extraction, text generation |
| **Email** | IMAP/SMTP nodes | Inbox monitoring, email sending |
| **CRM** | Airtable REST API | Contact & deal management |
| **Calendar** | Google Calendar API | Availability checking, event creation |
| **Video** | Zoom API | Meeting link generation |
| **Chat** | Slack Web API | Team notifications, Block Kit messages |
| **Deployment** | Docker + PostgreSQL | Containerized n8n with persistent storage |
| **Monitoring** | n8n webhooks + Slack | Error notifications, execution logs |



⭐ **If you find this project useful, please star the repository!**
