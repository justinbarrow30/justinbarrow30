### Justin Barrow

I build autonomous AI systems that do real operational work, with a focus on security.

I like taking an LLM past the chatbot stage: giving it tools, memory, and a job to own end to end.
My main project, CerberusAI, is an agentic SOC that investigates alerts by itself and gets sharper
the longer it watches a network.

---

#### 🛡️ CerberusAI, an agentic SOC that investigates alerts on its own
**[github.com/justinbarrow30/cerberus-ai →](https://github.com/justinbarrow30/cerberus-ai)**

Most enterprises already own the tools for a strong SOC. What they lack is the people and expertise
to run them at full strength. CerberusAI closes that gap. It plugs into your SIEM, works with any
LLM you choose, and continuously reads your alert traffic to build a live baseline of how your
network actually behaves. The moment your SIEM flags something, it investigates on its own: it
checks the alert against that baseline, pulls the device's history, decides whether the behavior is
normal, and returns an auto-close or escalate verdict with plain-English evidence in seconds. It
becomes the most knowledgeable analyst on the team, one that never sleeps and never forgets.

[![CerberusAI console](https://raw.githubusercontent.com/justinbarrow30/cerberus-ai/main/docs/console.png)](https://github.com/justinbarrow30/cerberus-ai)

**For the more technical, here is how it actually works:**

- **Read-only and one-way.** You connect it with a credential you control, and it only ever reads.
  There is no write path in the code, so it can never change your SIEM, hosts, or network gear, which
  makes the security sign-off easy.
- **It learns your environment (deterministic core).** It keeps a memory of your assets, which
  machines normally talk to which, and each host's own normal activity, then weighs every new alert
  against that history. A connection a device has never made before, especially to a critical asset,
  is how it catches lateral movement a static rule would miss. This core is deterministic statistics
  plus a graph, so it is fully auditable.
- **Machine-learning anomaly layer (UEBA).** On top of that core, an optional unsupervised **ensemble**
  learns the environment's normal *multivariate* behavior and flags unusual combinations of behavior
  that single-metric rules miss:
  - An **Isolation Forest** (scikit-learn) isolates statistical outliers; a small **PyTorch
    autoencoder** flags behavior it cannot reconstruct. Each model's raw score becomes a percentile
    against normal, and the ensemble is their mean.
  - On a held-out evaluation (normal traffic plus synthetic attacks across brute-force, lateral-spread
    and off-hours patterns) it reaches **0.996 ROC-AUC** and **0.97 F1**, beating either model alone.
  - Every score ships with **feature attributions** (the behaviors that drove it), so it stays
    explainable, and it is **one signal the agent weighs, never the judge**. The deterministic core
    still makes the verdict. It trains on the behavior the tool accumulates, so it sharpens on your
    real traffic.
- **Built for real networks.** It keys its memory on a stable identity, so a host's history is not
  lost when its IP changes through DHCP, containers, or autoscaling.
- **Your stack.** Bring-your-own-LLM, and a small adapter per SIEM, so swapping either one never
  touches the core.
- **Roadmap.** Optional network-traffic ingestion via port mirroring (SPAN / ERSPAN), to enrich the
  baseline with live traffic instead of only what the SIEM already flags.

Python · FastAPI · Pydantic structured outputs · Model Context Protocol · scikit-learn · PyTorch ·
SQLite memory · Docker.

#### ⚽ MECA, a 7v7 football tournament app
**[github.com/justinbarrow30/meca-app →](https://github.com/justinbarrow30/meca-app)**

A full-stack mobile app: React Native / Expo front end, Node.js back end.

---

#### Tooling I reach for

Python · TypeScript / JavaScript · React Native · FastAPI / Node · LLM agent patterns (MCP,
structured outputs, tool use) · Docker · SQLite / Postgres

#### Connect

GitHub [@justinbarrow30](https://github.com/justinbarrow30) · LinkedIn, add your link here
