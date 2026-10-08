### Justin Barrow

I build autonomous AI systems that do real operational work, with a focus on security.

I like taking an LLM past the chatbot stage: giving it tools, memory, and a job to own end to end.
My main project, CerberusAI, is an agentic SOC that investigates alerts by itself and gets sharper
the longer it watches a network.

---

#### 🛡️ CerberusAI, an agentic SOC that investigates alerts on its own
**[github.com/justinbarrow30/cerberus-ai →](https://github.com/justinbarrow30/cerberus-ai)**

An open-source, read-only agentic SOC. You connect it to your SIEM over its API and it investigates
each alert on its own, then returns an auto-close or escalate verdict with plain-English evidence
instead of just adding to the queue.

**How it gets smarter over time.** It does not use machine learning or any black-box model. Instead
it keeps a memory (a local database) of everything it has investigated. Every case it works adds
facts: which assets exist and how critical each one is, a map of which machines normally talk to
which, and each asset's usual activity levels. When a new alert comes in, it reads that memory
before it decides, and connects the dots. Is this a connection the network has never made before?
Is this login volume far above what is normal for this specific host? Has this source caused
trouble already? Each of those is a real signal it weighs instead of looking at the alert in
isolation. The longer it runs, the more complete that picture of "normal" becomes, so its read on
normal versus suspicious keeps getting more accurate. On day one it is cautious because it has
little history; after a week on your real traffic it knows your network the way a veteran analyst
would, except every call is backed by recorded facts and plain math you can audit.

**Why it is easy to adopt:**

- **Quick to integrate.** You connect it to your SIEM in a browser wizard: paste the address and a
  read-only key, test the connection, done. No agents to roll out and no code to write.
- **Safe to approve.** It is read-only and one-way, with no path to change anything it touches, so
  the security sign-off is far easier than for a tool that can act on your systems.
- **Anyone can read it.** The dashboard explains each incident in plain English, so you do not have
  to be a seasoned analyst to understand what happened and why.
- **Use your own AI and SIEM.** Bring whichever LLM your org already approved, and point it at
  whatever SIEM you run. Swapping either one never touches the core.

[![CerberusAI console](https://raw.githubusercontent.com/justinbarrow30/cerberus-ai/main/docs/console.png)](https://github.com/justinbarrow30/cerberus-ai)

Python · FastAPI · Pydantic structured outputs · Model Context Protocol · SQLite memory · Docker.

#### ⚽ MECA, a 7v7 football tournament app
**[github.com/justinbarrow30/meca-app →](https://github.com/justinbarrow30/meca-app)**

A full-stack mobile app: React Native / Expo front end, Node.js back end.

---

#### Tooling I reach for

Python · TypeScript / JavaScript · React Native · FastAPI / Node · LLM agent patterns (MCP,
structured outputs, tool use) · Docker · SQLite / Postgres

#### Connect

GitHub [@justinbarrow30](https://github.com/justinbarrow30) · LinkedIn, add your link here
