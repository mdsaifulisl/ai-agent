# 🤖 Aria — Personal AI Agent

> **[আপনার নাম]**-এর ব্যক্তিগত AI সহকারী — যে ২৪/৭ কাজ করে, রিসার্চ করে,
> সোশ্যাল মিডিয়া ম্যানেজ করে, লিড খোঁজে, রিপোর্ট দেয়, এবং কোডিংয়ে সাহায্য করে।

[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue)](https://www.typescriptlang.org/)
[![Node.js](https://img.shields.io/badge/Node.js-22.x-green)](https://nodejs.org/)
[![LangGraph](https://img.shields.io/badge/LangGraph-latest-purple)](https://langchain-ai.github.io/langgraph/)
[![License](https://img.shields.io/badge/license-Private-red)]()

---

## 📖 সূচিপত্র

- [ভূমিকা](#-ভূমিকা)
- [ফিচার](#-ফিচার)
- [আর্কিটেকচার](#-আর্কিটেকচার)
- [প্রযুক্তি স্ট্যাক](#-প্রযুক্তি-স্ট্যাক)
- [প্রয়োজনীয়তা](#-প্রয়োজনীয়তা)
- [ইনস্টলেশন](#-ইনস্টলেশন)
- [কনফিগারেশন](#-কনফিগারেশন)
- [প্রজেক্ট স্ট্রাকচার](#-প্রজেক্ট-স্ট্রাকচার)
- [এজেন্ট পার্সোনালিটি (.agent ফোল্ডার)](#-এজেন্ট-পার্সোনালিটি-agent-ফোল্ডার)
- [ব্যবহার](#-ব্যবহার)
- [উপলব্ধ কমান্ড](#-উপলব্ধ-কমান্ড)
- [দৈনিক ওয়ার্কফ্লো](#-দৈনিক-ওয়ার্কফ্লো)
- [টুল সিস্টেম](#-টুল-সিস্টেম)
- [ডেটাবেস স্কিমা](#-ডেটাবেস-স্কিমা)
- [Docker সেটআপ](#-docker-সেটআপ)
- [টেস্টিং](#-টেস্টিং)
- [ডিপ্লয়মেন্ট](#-ডিপ্লয়মেন্ট)
- [ট্রাবলশুটিং](#-ট্রাবলশুটিং)
- [রোডম্যাপ](#-রোডম্যাপ)
- [নিরাপত্তা](#-নিরাপত্তা)
- [লাইসেন্স](#-লাইসেন্স)

---

## 🎯 ভূমিকা

**Aria** হলো একটি সম্পূর্ণ স্বায়ত্তশাসিত AI এজেন্ট যা:

- 🧠 **LLM-ভিত্তিক মস্তিষ্ক** — Google Gemini / Anthropic Claude
- 🛠️ **টুল কলিং** — ব্রাউজার, ক্যালেন্ডার, সোশ্যাল মিডিয়া, ওয়েবসাইট
- 💬 **মাল্টি-চ্যানেল ইনপুট** — Telegram, Voice, Cron
- 🔊 **ভয়েস ইন্টারফেস** — "Hey Aria" বলে ডাক দিলেই সাড়া দেয়
- 📊 **দৈনিক রিপোর্ট** — Google Sheets-এ অটো-জেনারেটেড
- 🎯 **লিড জেনারেশন** — LinkedIn স্ক্যান করে ক্লায়েন্ট খোঁজে
- 📝 **সোশ্যাল মিডিয়া** — প্রতিদিন LinkedIn + Facebook পোস্ট
- 💻 **কোডিং সহকারী** — VS Code প্রজেক্টে সাহায্য করে
- 🌐 **ওয়েবসাইট কন্ট্রোল** — আপনার সাইটের API-এর মাধ্যমে কাজ করে

---

## ✨ ফিচার

### কমিউনিকেশন
- ✅ Telegram বট — যেকোনো জায়গা থেকে কমান্ড
- ✅ Voice wake word — "Hey Aria" বলে কথা বলা
- ✅ TTS ভয়েস রিপ্লাই — বাংলা ও ইংরেজি
- ✅ অটো মেসেজ রিপ্লাই — WhatsApp, Instagram, LinkedIn, Facebook

### বিজনেস অটোমেশন
- ✅ দৈনিক LinkedIn + Facebook পোস্ট
- ✅ LinkedIn লিড হান্ট (স্কোরিং সহ)
- ✅ কাস্টমাইজড আউটরিচ মেসেজ
- ✅ ক্লায়েন্ট ফলো-আপ রিমাইন্ডার

### প্রোডাক্টিভিটি
- ✅ Google Calendar ইন্টিগ্রেশন
- ✅ মিটিং নোটিফিকেশন
- ✅ দৈনিক Google Sheets রিপোর্ট
- ✅ সাপ্তাহিক স্ট্র্যাটেজি অ্যাডভাইস
- ✅ কোড রিভিউ ও Bug ফিক্স

### ইন্টেলিজেন্স
- ✅ RAG — আপনার ওয়েবসাইট ও ডকুমেন্ট থেকে তথ্য
- ✅ Long-term memory — PostgreSQL + pgvector
- ✅ Pattern recognition — কী কাজ করছে, কী করছে না
- ✅ Proactive suggestions — নিজে থেকে পরামর্শ

---

## 🏗️ আর্কিটেকচার

```
┌─────────────────────────────────────────────────────────────────┐
│                       INPUT LAYERS                                │
│  🎤 Voice (Porcupine)  │  📱 Telegram  │  ⏰ Cron Scheduler      │
└────────────┬────────────┬──────────────┬────────────────────────┘
             │            │              │
             ▼            ▼              ▼
┌─────────────────────────────────────────────────────────────────┐
│                       AGENT CORE                                  │
│  ┌──────────────┐  ┌────────────┐  ┌────────────────────────┐  │
│  │ LLM Engine   │  │ LangGraph  │  │ Memory (Postgres +     │  │
│  │ Gemini/Claude│  │ State Graph│  │         pgvector)      │  │
│  └──────────────┘  └────────────┘  └────────────────────────┘  │
│                          │                                       │
│              ┌───────────┴───────────┐                          │
│              ▼                       ▼                          │
│     ┌──────────────┐        ┌──────────────┐                    │
│     │ Tool Router  │        │  RAG Engine  │                    │
│     └──────┬───────┘        └──────────────┘                    │
└────────────┼────────────────────────────────────────────────────┘
             │
             ▼
┌─────────────────────────────────────────────────────────────────┐
│                    TOOL EXECUTION LAYER                           │
│  🌐 Browser  │ 📅 Calendar │ 📊 Sheets │ 💻 System │ 📱 Social   │
│  🌍 Website  │ 📧 Email    │ 🔍 Search │ 🧮 Utils  │ 📁 Files    │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│                       OUTPUT LAYERS                               │
│  🔊 Voice  │  💬 Telegram  │  📝 Sheets Report  │  📱 Posts       │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🧰 প্রযুক্তি স্ট্যাক

| লেয়ার | টেকনোলজি |
|-------|-----------|
| **Runtime** | Node.js 22+, TypeScript 5.x |
| **Agent Framework** | LangChain + LangGraph |
| **LLM** | Google Gemini 2.5 Pro / Anthropic Claude |
| **Database** | PostgreSQL 16 + pgvector |
| **Cache** | Redis 7 |
| **Telegram** | Telegraf |
| **Voice** | Picovoice Porcupine + Piper/ElevenLabs |
| **Browser** | Playwright |
| **Social** | Ayrshare / OmniSocials SDK |
| **Google APIs** | googleapis (Calendar, Sheets) |
| **Search** | Tavily API |
| **Scheduler** | node-cron |
| **Container** | Docker + Docker Compose |
| **Testing** | Vitest |

---

## 📋 প্রয়োজনীয়তা

### সিস্টেম
- Node.js **22.x** বা তার উপরে
- PostgreSQL **16+** (pgvector extension সহ)
- Redis **7+**
- Docker ও Docker Compose (রেকমেন্ডেড)
- Git

### API Keys
| সার্ভিস | কী | কোথায় পাবেন |
|--------|-----|------------|
| Google AI | `GOOGLE_API_KEY` | [aistudio.google.com](https://aistudio.google.com) |
| Telegram | `TELEGRAM_BOT_TOKEN` | [@BotFather](https://t.me/BotFather) |
| Picovoice | `PICOVOICE_ACCESS_KEY` | [console.picovoice.ai](https://console.picovoice.ai) |
| Tavily | `TAVILY_API_KEY` | [tavily.com](https://tavily.com) |
| Google Cloud | `GOOGLE_CLIENT_ID/SECRET` | [console.cloud.google.com](https://console.cloud.google.com) |
| Ayrshare | `AYRSHARE_API_KEY` | [ayrshare.com](https://ayrshare.com) |
| ElevenLabs (optional) | `ELEVENLABS_API_KEY` | [elevenlabs.io](https://elevenlabs.io) |

---

## 🚀 ইনস্টলেশন

### ১. ক্লোন ও ইনস্টল

```bash
git clone https://github.com/[your-username]/aria-agent.git
cd aria-agent
npm install
```

### ২. Environment সেটআপ

```bash
cp .env.example .env
# .env ফাইলটি এডিট করে সব API key বসান
```

### ৩. Docker সার্ভিস চালু

```bash
docker compose up -d
# PostgreSQL ও Redis চালু হবে
```

### ৪. ডেটাবেস মাইগ্রেশন

```bash
npm run db:migrate
```

### ৫. এজেন্ট চালু

```bash
npm run dev
```

Terminal-এ দেখবেন:

```
🤖 Aria চালু হয়েছে!
✅ PostgreSQL connected
✅ Redis connected
✅ Telegram bot listening
✅ Voice wake word active
✅ Cron jobs scheduled
📊 Dashboard: http://localhost:3000
```

---

## ⚙️ কনফিগারেশন

### `.env.example`

```env
# ===== CORE =====
NODE_ENV=development
PORT=3000
TIMEZONE=Asia/Dhaka

# ===== LLM =====
GOOGLE_API_KEY=your_google_ai_key
LLM_MODEL=gemini-2.5-pro
LLM_TEMPERATURE=0.7

# ===== DATABASE =====
DATABASE_URL=postgresql://aria:aria@localhost:5432/aria
REDIS_URL=redis://localhost:6379

# ===== TELEGRAM =====
TELEGRAM_BOT_TOKEN=your_bot_token
MY_TELEGRAM_CHAT_ID=your_chat_id

# ===== VOICE =====
PICOVOICE_ACCESS_KEY=your_key
WAKE_WORD_PATH=./assets/hey-aria.ppn
TTS_PROVIDER=piper
ELEVENLABS_API_KEY=optional

# ===== GOOGLE =====
GOOGLE_CLIENT_ID=your_client_id
GOOGLE_CLIENT_SECRET=your_client_secret
GOOGLE_REDIRECT_URI=http://localhost:3000/auth/google/callback
GOOGLE_SHEET_ID=your_sheet_id

# ===== SOCIAL =====
AYRSHARE_API_KEY=your_key

# ===== SEARCH =====
TAVILY_API_KEY=your_key

# ===== WEBSITE =====
WEBSITE_URL=https://your-website.com
WEBSITE_API_KEY=your_secret_key

# ===== SECURITY =====
ENCRYPTION_KEY=random_32_char_string
```

### `.env` নিয়ম
- 🔒 কখনো Git-এ commit করবেন না
- 🔒 Production-এ secrets manager ব্যবহার করুন
- 🔒 নিয়মিত key rotate করুন

---

## 📁 প্রজেক্ট স্ট্রাকচার

```
aria-agent/
├── .agent/                          # এজেন্টের পার্সোনালিটি (.md ফাইল)
│   ├── 00-identity.md
│   ├── 01-user-profile.md
│   ├── 02-personality.md
│   ├── 03-capabilities.md
│   ├── 04-workflows.md
│   ├── 05-social-media.md
│   ├── 06-lead-generation.md
│   ├── 07-communication.md
│   ├── 08-reporting.md
│   ├── 09-advice-engine.md
│   ├── 10-code-assistant.md
│   ├── 11-voice-interface.md
│   ├── 12-website-control.md
│   ├── 13-security.md
│   ├── 14-error-handling.md
│   └── 15-memory-rules.md
│
├── src/
│   ├── core/
│   │   ├── agent.ts                 # LangGraph এজেন্ট
│   │   ├── llm.ts                   # LLM কনফিগারেশন
│   │   ├── memory.ts                # Memory manager
│   │   ├── system-prompt.ts         # .agent লোডার
│   │   ├── rag.ts                   # RAG engine
│   │   └── tools/
│   │       ├── index.ts             # Tool registry
│   │       ├── social.ts            # Social media
│   │       ├── calendar.ts          # Google Calendar
│   │       ├── sheets.ts            # Google Sheets
│   │       ├── browser.ts           # Playwright
│   │       ├── system.ts            # Local system
│   │       ├── website.ts           # আপনার ওয়েবসাইট
│   │       ├── search.ts            # Tavily
│   │       └── code.ts              # Code assistant
│   │
│   ├── inputs/
│   │   ├── telegram.ts              # Telegram bot
│   │   ├── voice.ts                 # Wake word + STT
│   │   └── webhook.ts               # HTTP webhooks
│   │
│   ├── outputs/
│   │   ├── tts.ts                   # Text-to-speech
│   │   └── notifications.ts
│   │
│   ├── schedulers/
│   │   ├── daily-report.ts          # রাত ১০টা
│   │   ├── social-post.ts           # দুপুর ১২টা
│   │   ├── lead-hunt.ts             # সকাল ১০টা
│   │   ├── morning-brief.ts         # সকাল ৯টা
│   │   └── inbox-cleanup.ts         # সন্ধ্যা ৭টা
│   │
│   ├── db/
│   │   ├── client.ts
│   │   ├── schema.ts
│   │   └── migrations/
│   │
│   ├── utils/
│   │   ├── logger.ts
│   │   ├── errors.ts
│   │   └── validators.ts
│   │
│   ├── config/
│   │   └── index.ts
│   │
│   └── index.ts                     # Entry point
│
├── tests/
│   ├── unit/
│   └── integration/
│
├── assets/
│   ├── hey-aria.ppn                 # Wake word model
│   └── voices/                      # TTS voices
│
├── docker/
│   ├── Dockerfile
│   └── docker-compose.yml
│
├── .env.example
├── .gitignore
├── package.json
├── tsconfig.json
├── vitest.config.ts
└── README.md
```

---

## 🧠 এজেন্ট পার্সোনালিটি (.agent ফোল্ডার)

`.agent/` ফোল্ডারের প্রতিটি `.md` ফাইল এজেন্টের একটি নির্দিষ্ট দিক নিয়ন্ত্রণ করে:

| ফাইল | কাজ |
|------|-----|
| `00-identity.md` | এজেন্ট কে, তার নাম, ভাষা |
| `01-user-profile.md` | আপনি কে, আপনার পছন্দ |
| `02-personality.md` | এজেন্টের টোন ও স্টাইল |
| `03-capabilities.md` | এজেন্ট কী কী করতে পারে |
| `04-workflows.md` | দৈনিক কাজের নিয়ম |
| `05-social-media.md` | পোস্টিং গাইডলাইন |
| `06-lead-generation.md` | লিড স্কোরিং ও আউটরিচ |
| `07-communication.md` | মেসেজ রিপ্লাই স্টাইল |
| `08-reporting.md` | রিপোর্ট ফরম্যাট |
| `09-advice-engine.md` | পরামর্শ দেওয়ার নিয়ম |
| `10-code-assistant.md` | কোডিং সহায়তা |
| `11-voice-interface.md` | ভয়েস কমান্ড |
| `12-website-control.md` | ওয়েবসাইট কন্ট্রোল |
| `13-security.md` | নিরাপত্তা নিয়ম |
| `14-error-handling.md` | এরর হ্যান্ডলিং |
| `15-memory-rules.md` | কী মনে রাখবে |

### আপডেট করবেন কীভাবে?
শুধু `.md` ফাইল এডিট করুন। কোড ছোঁয়ার দরকার নেই। এজেন্ট পরের বার চালু হলে নতুন নিয়ম পড়বে।

```bash
# উদাহরণ: টোন আরও ফরমাল করতে
nano .agent/02-personality.md
```

---

## 🎮 ব্যবহার

### Telegram-এ

```
আপনি: আজকের মিটিং কী?
Aria: আজ ৩টা মিটিং আছে:
      • ২:০০ PM — [ক্লায়েন্ট A] (Zoom)
      • ৪:৩০ PM — [ক্লায়েন্ট B] (Google Meet)
      • ৭:০০ PM — Team standup

আপনি: LinkedIn-এ আজকের পোস্ট লেখো
Aria: [পোস্ট ড্রাফট পাঠাল] অ্যাপ্রুভ করবেন?

আপনি: ✅
Aria: LinkedIn-এ পোস্ট হয়ে গেছে! ✅
```

### Voice-এ

```
আপনি: "Hey Aria"
Aria: "হ্যাঁ, বলুন।"
আপনি: "আজকের রিপোর্ট দাও"
Aria: "আজ ১২টা মেসেজ রিপ্লাই দিয়েছি, ৩টা নতুন লিড পেয়েছি। 
       বিস্তারিত Telegram-এ পাঠালাম।"
```

### সরাসরি কমান্ড

```bash
# Development
npm run dev

# Production build
npm run build && npm start

# Report জেনারেট
npm run report:daily

# Post তৈরি
npm run post:linkedin

# লিড স্ক্যান
npm run leads:hunt
```

---

## 🛠️ উপলব্ধ কমান্ড

### Telegram কমান্ড
| কমান্ড | কাজ |
|--------|-----|
| `/start` | এজেন্ট চালু |
| `/stop` | সব কাজ বন্ধ (জরুরি) |
| `/status` | সিস্টেম স্ট্যাটাস |
| `/report` | দৈনিক রিপোর্ট |
| `/today` | আজকের মিটিং |
| `/post` | সোশ্যাল পোস্ট তৈরি |
| `/leads` | নতুন লিড |
| `/memory` | কী মনে আছে |

### Voice কমান্ড
- "Hey Aria" — জাগানো
- "Hey Aria, থামো" — বন্ধ
- "Hey Aria, রিপোর্ট" — রিপোর্ট

### NPM Scripts
```bash
npm run dev              # Development mode
npm run build            # Production build
npm start                # Production run
npm run db:migrate       # DB migration
npm run db:seed          # Seed data
npm test                 # Unit tests
npm run test:e2e         # E2E tests
npm run lint             # ESLint
npm run format           # Prettier
npm run report:daily     # Manual daily report
```

---

## 📅 দৈনিক ওয়ার্কফ্লো

| সময় | টাস্ক | আউটপুট |
|------|-------|--------|
| **৯:০০** | মর্নিং ব্রিফ | Telegram-এ আজকের সারাংশ |
| **১০:০০** | লিড হান্ট | LinkedIn স্ক্যান → DB |
| **১২:০০** | সোশ্যাল পোস্ট | LinkedIn + Facebook |
| **১৫:০০** | মেসেজ রিপ্লাই | সব প্ল্যাটফর্ম |
| **১৯:০০** | ইনবক্স ক্লিনআপ | লগ + রিমাইন্ডার |
| **২২:০০** | দৈনিক রিপোর্ট | Google Sheets + Telegram |
| **২২:৩০** | স্ট্র্যাটেজি অ্যাডভাইস | পরামর্শ |

সব সময় **`Asia/Dhaka`** টাইমজোনে।

---

## 🔧 টুল সিস্টেম

### একটি টুল তৈরি করা

```typescript
// src/core/tools/example.ts
import { z } from "zod";
import { tool } from "@langchain/core/tools";

export const myTool = tool(
  async ({ query }) => {
    // এখানে কাজ করুন
    return `Result for: ${query}`;
  },
  {
    name: "my_tool",
    description: "কখন এই টুল ব্যবহার করবে তার বর্ণনা",
    schema: z.object({
      query: z.string().describe("সার্চ কোয়েরি"),
    }),
  }
);
```

### টুল রেজিস্ট্রি

```typescript
// src/core/tools/index.ts
import { myTool } from "./example";
import { socialTools } from "./social";
import { calendarTools } from "./calendar";
// ...

export const allTools = [
  myTool,
  ...socialTools,
  ...calendarTools,
  // ...
];
```

---

## 🗄️ ডেটাবেস স্কিমা

### মূল টেবিল

```sql
-- কথোপকথন
CREATE TABLE conversations (
  id UUID PRIMARY KEY,
  channel VARCHAR(50),
  user_id VARCHAR(100),
  content TEXT,
  role VARCHAR(20),
  created_at TIMESTAMPTZ DEFAULT NOW()
);

-- লিড
CREATE TABLE leads (
  id UUID PRIMARY KEY,
  name VARCHAR(200),
  company VARCHAR(200),
  role VARCHAR(200),
  linkedin_url TEXT,
  score INTEGER,
  status VARCHAR(50),
  notes TEXT,
  created_at TIMESTAMPTZ DEFAULT NOW()
);

-- পোস্ট
CREATE TABLE posts (
  id UUID PRIMARY KEY,
  platform VARCHAR(50),
  content TEXT,
  engagement JSONB,
  posted_at TIMESTAMPTZ
);

-- মেমোরি (pgvector)
CREATE TABLE memories (
  id UUID PRIMARY KEY,
  content TEXT,
  embedding vector(1536),
  metadata JSONB,
  created_at TIMESTAMPTZ DEFAULT NOW()
);

-- অ্যাকশন লগ
CREATE TABLE action_logs (
  id UUID PRIMARY KEY,
  action VARCHAR(100),
  tool VARCHAR(100),
  input JSONB,
  output JSONB,
  success BOOLEAN,
  created_at TIMESTAMPTZ DEFAULT NOW()
);
```

---

## 🐳 Docker সেটআপ

```yaml
# docker-compose.yml
version: '3.9'

services:
  postgres:
    image: pgvector/pgvector:pg16
    environment:
      POSTGRES_USER: aria
      POSTGRES_PASSWORD: aria
      POSTGRES_DB: aria
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data

  redis:
    image: redis:7-alpine
    ports:
      - "6379:6379"
    volumes:
      - redis_data:/data

  aria:
    build: .
    depends_on:
      - postgres
      - redis
    env_file: .env
    ports:
      - "3000:3000"
    volumes:
      - .:/app
      - /app/node_modules

volumes:
  postgres_data:
  redis_data:
```

```bash
docker compose up -d        # সব চালু
docker compose logs -f aria # লগ দেখুন
docker compose down         # বন্ধ
```

---

## 🧪 টেস্টিং

```bash
# সব টেস্ট
npm test

# Unit test
npm run test:unit

# Integration test
npm run test:e2e

# Coverage
npm run test:coverage
```

### একটি টেস্ট লেখা

```typescript
// tests/unit/agent.test.ts
import { describe, it, expect } from "vitest";
import { agent } from "../../src/core/agent";

describe("Agent", () => {
  it("সাধারণ প্রশ্নের উত্তর দিতে পারে", async () => {
    const result = await agent.invoke({
      messages: [{ role: "user", content: "2+2 কত?" }],
    });
    expect(result.messages.at(-1)?.content).toContain("4");
  });
});
```

---

## 🚢 ডিপ্লয়মেন্ট

### VPS-এ (রেকমেন্ডেড)

```bash
# ১. VPS-এ clone
git clone https://github.com/[you]/aria-agent.git
cd aria-agent

# ২. Setup
cp .env.example .env
nano .env  # প্রোডাকশন key বসান

# ৩. Docker
docker compose up -d

# ৪. Systemd service (auto-restart)
sudo nano /etc/systemd/system/aria.service
```

```ini
[Unit]
Description=Aria AI Agent
After=docker.service
Requires=docker.service

[Service]
Type=oneshot
RemainAfterExit=yes
WorkingDirectory=/root/aria-agent
ExecStart=/usr/bin/docker compose up -d
ExecStop=/usr/bin/docker compose down

[Install]
WantedBy=multi-user.target
```

```bash
sudo systemctl enable aria
sudo systemctl start aria
```

### Cloud Options
- **Railway** — সহজ, সস্তা
- **Fly.io** — ভালো ফ্রি টিয়ার
- **AWS EC2** — স্কেলেবল
- **DigitalOcean** — সিম্পল

---

## 🔧 ট্রাবলশুটিং

### সমস্যা: Telegram bot সাড়া দিচ্ছে না
```bash
# চেক করুন
curl https://api.telegram.org/bot<TOKEN>/getMe
# Webhook conflicts থাকলে
curl https://api.telegram.org/bot<TOKEN>/deleteWebhook
```

### সমস্যা: Voice wake word কাজ করছে না
- মাইক্রোফোন পারমিশন চেক করুন
- `.ppn` ফাইল path ঠিক আছে কি না দেখুন
- Picovoice key valid কি না চেক করুন

### সমস্যা: LLM response slow
- `gemini-2.5-flash` ব্যবহার করুন
- Memory cache বাড়ান
- Tavily-র বদলে local cache

### সমস্যা: PostgreSQL connection error
```bash
docker compose ps           # কন্টেইনার চলছে?
docker compose logs postgres
psql $DATABASE_URL -c "SELECT 1"
```

### লগ দেখা
```bash
tail -f logs/aria.log
# অথবা
docker compose logs -f aria
```

---

## 🗺️ রোডম্যাপ

### ✅ Phase 1 — Foundation (সম্পন্ন)
- [x] LangGraph এজেন্ট সেটআপ
- [x] Telegram ইন্টিগ্রেশন
- [x] PostgreSQL + pgvector মেমোরি
- [x] .agent পার্সোনালিটি সিস্টেম

### 🚧 Phase 2 — Automation (চলমান)
- [ ] Browser automation (Playwright)
- [ ] Google Calendar + Sheets
- [ ] Social media posting
- [ ] Voice wake word + TTS

### 🔜 Phase 3 — Intelligence
- [ ] LinkedIn লিড স্কোরিং ML মডেল
- [ ] RAG — আপনার ডকুমেন্ট থেকে সার্চ
- [ ] Proactive suggestions
- [ ] Email অটোমেশন

### 🔮 Phase 4 — Scale
- [ ] Mobile app (React Native)
- [ ] Web dashboard
- [ ] Multi-user support
- [ ] Self-hosted LLM option

---

## 🔒 নিরাপত্তা

- 🔐 সব credentials `.env`-এ, কখনো কোডে নয়
- 🔐 Telegram bot শুধু আপনার ID থেকে কমান্ড নেয়
- 🔐 সেনসিটিভ অ্যাকশনে আপনার অ্যাপ্রুভাল লাগে
- 🔐 সব অ্যাকশন `action_logs`-এ লগ
- 🔐 Encryption at rest for sensitive data
- 🔐 Rate limiting সব external API-তে

### Vulnerabilities রিপোর্ট
সিকিউরিটি ইস্যু পেলে সরাসরি ইমেইল করুন: **[আপনার ইমেইল]**

---

## 🤝 কনট্রিবিউশন

এটি একটি ব্যক্তিগত প্রজেক্ট, তবে আইডিয়া শেয়ার করতে পারেন:

1. Fork করুন
2. Feature branch: `git checkout -b feature/amazing`
3. Commit: `git commit -m 'Add amazing feature'`
4. Push: `git push origin feature/amazing`
5. Pull Request খুলুন

---

## 📄 লাইসেন্স

**Private** — এই প্রজেক্টটি ব্যক্তিগত ব্যবহারের জন্য। অনুমতি ছাড়া বিতরণ, পরিবর্তন বা ব্যবহার নিষিদ্ধ।

---

## 🙏 কৃতজ্ঞতা

- [LangChain](https://langchain.com) — Agent framework
- [Google Gemini](https://ai.google.dev) — LLM
- [Picovoice](https://picovoice.ai) — Voice wake word
- [Ayrshare](https://ayrshare.com) — Social media API

---

## 📞 যোগাযোগ

- **ডেভেলপার**: [আপনার নাম]
- **ইমেইল**: [আপনার ইমেইল]
- **GitHub**: [@your-username](https://github.com/your-username)
- **ওয়েবসাইট**: [আপনার সাইট]

---

<div align="center">

**🤖 Aria — আপনার ব্যক্তিগত AI সহকারী**

বাংলাদেশে ❤️ দিয়ে তৈরি

</div>