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
network actually behaves. On top of that, a machine-learning model learns what normal looks like
across many signals at once, so it catches unusual patterns a single metric would miss. The moment
your SIEM flags something, it investigates on its own: it checks the alert against that baseline,
pulls the device's history, decides whether the behavior is normal, and returns an auto-close or
escalate verdict with plain-English evidence in seconds.

[![CerberusAI console](https://raw.githubusercontent.com/justinbarrow30/cerberus-ai/main/docs/console.png)](https://github.com/justinbarrow30/cerberus-ai)

**For the more technical, here is how it actually works:**

Bottom line: CerberusAI runs three independent detection layers, a deterministic baseline of the
network, a machine-learning model of normal behavior, and an LLM agent that investigates each alert
and weighs the other two into one grounded verdict. Different layers catch different attacks, so no
single one has to be right on its own.

- **Read-only and one-way.** You connect it with a credential you control, and it only ever reads.
  There is no write path in the code, so it can never change your SIEM, hosts, or network gear, which
  makes the security sign-off easy.
- **It learns your environment (the deterministic core).** As it runs, it builds a picture of your
  network: what each machine is, which machines normally talk to each other, and what a normal day
  looks like for each one. Every new alert is checked against that picture. So when a machine opens a
  connection it has never made before, especially to a critical system, that break from its normal
  pattern surfaces right away. All of this is plain math and a map of the network, not a black box, so
  every decision can be traced.
- **Machine-learning anomaly layer.** The hard part of detection is behavior that looks normal on
  every individual signal but is anomalous in combination. To catch that, I trained unsupervised models
  (they learn from normal activity alone, with no labeled attacks) on normal behavior across all of
  these features at once, so they score how unusual the overall pattern is rather than any single
  number. This is the standard UEBA approach (user and entity behavior analytics). Under the hood:
  - An **Isolation Forest** (scikit-learn) isolates statistical outliers; a small **PyTorch
    autoencoder** flags behavior it cannot reconstruct. Each model's raw score becomes a percentile
    against normal, and the ensemble is their mean.
  - On a synthetic benchmark (normal traffic plus injected brute-force, lateral-spread and off-hours
    attacks) the ensemble reaches **0.996 ROC-AUC**, beating either model alone. That validates the
    method, not real-world performance; a harness to evaluate it on the Los Alamos auth + red-team
    dataset ships in the repo.
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
