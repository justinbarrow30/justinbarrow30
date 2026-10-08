### Justin Barrow

I build autonomous AI systems that do real operational work — with a focus on security.

I like taking an LLM past the chatbot stage: giving it tools, memory, and a job to own end to end.
My main project, **CerberusAI**, is an agentic SOC that investigates alerts by itself and gets
sharper the longer it watches a network.

---

#### 🛡️ CerberusAI — an agentic SOC that investigates alerts on its own
**[github.com/justinbarrow30/cerberus-ai →](https://github.com/justinbarrow30/cerberus-ai)**

An open-source, read-only agentic SOC. You connect it to your SIEM over its API and it investigates
each alert autonomously — then returns an auto-close / escalate verdict with plain-English evidence,
instead of just adding to the queue.

Some of the engineering I am proud of:

- **Read-only by design.** It connects with a credential *you* control and only ever reads — a
  one-way API pull. There is no write path in the code: it never changes your SIEM, hosts, or
  network gear. That is what makes it safe to approve in a security or government environment.
- **It gets sharper over time.** A self-growing memory records your network's topology (who talks
  to whom) and each asset's normal baselines, so it catches lateral movement — a machine reaching
  something it never has — that a static rule would miss.
- **Explainable, not a black box.** The decisions rest on deterministic statistics plus a graph, so
  every verdict is auditable rather than a mystery score.
- **Bring-your-own-LLM, SIEM-agnostic.** Provider-agnostic via LiteLLM; each SIEM sits behind a
  small adapter, so the reasoning engine never changes when you swap platforms.

[![CerberusAI console](https://raw.githubusercontent.com/justinbarrow30/cerberus-ai/main/docs/console.png)](https://github.com/justinbarrow30/cerberus-ai)

Python · FastAPI · Pydantic structured outputs · Model Context Protocol · SQLite memory · Docker.

#### ⚽ MECA — 7v7 football tournament app
**[github.com/justinbarrow30/meca-app →](https://github.com/justinbarrow30/meca-app)**

A full-stack mobile app — React Native / Expo front end, Node.js back end.

---

#### Tooling I reach for

Python · TypeScript / JavaScript · React Native · FastAPI / Node · LLM agent patterns (MCP,
structured outputs, tool use) · Docker · SQLite / Postgres

#### Connect

GitHub [@justinbarrow30](https://github.com/justinbarrow30) · LinkedIn — _add your link here_
