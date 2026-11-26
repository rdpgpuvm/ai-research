# 🔬 Agentic AI & Generative AI Research Report — Thursday, November 26, 2026

*Compiled Thursday, November 26, 2026 (America/Los_Angeles) from a fresh research pass on November 25–26, 2026. Today's edition introduces five completely new anchor stories not present in the November 25 edition: **Reuters reporting that US chip curbs and a distillation crackdown are now threatening Chinese AI model development** — with Z.AI's GLM-5.5 flagship slipping to Q1 2027 and Moonshot AI expecting its release cadence to double from six months to a year or more if it loses overseas compute; **Microsoft's Ignite 2026 pivot to Copilot as an "operating system for work"** — chat, coding and autonomous agents unified under one vision, with agent identity, governance and cost controls spanning Azure, Foundry, Entra and Defender, plus an AI Transparency Initiative aligned to NIST's Agent Standards Initiative; **Amazon Transcribe Turbo entering public preview** — a next-gen speech-to-text model with semantic turn-taking and runtime ASR hints built specifically for voice agents; **Meta's Muse agent launching in the UK** with 14 British brand deals even as the ICO and financial regulators warn on privacy and consumer protection; and **SenseTime's full release of SenseNova-RoboRSI-27B** — an open-weights embodied agent that outscored GPT-6 Astra on RoboDojo and moved from simulation to real robot arms with no real-robot training. Security watch leads with **CISA's Nov 25 KEV batch of ten** (five Mitel MiCollab RCE-class flaws, three Danfoss AK-SM 800A entries, HPE Juniper Session Smart root command injection, and Vates Xen Orchestra auth bypass) and **F5 NGINX active exploitation** (CVE-2026-123007 / CVE-2026-123633) flagged by Singapore's CSA. Figures below are as reported by the cited outlets and are not independently verified.*

---

## Top 5 Latest Advancements

### 1. Reuters: US Chip Curbs and Distillation Crackdown Threaten Chinese AI Model Development (Nov 26)

**What happened:** Reuters reported on Nov 26, citing people familiar with the matter, that **China's Z.AI (Zhipu AI) has fallen behind schedule on its next flagship model** — GLM-5.5 was planned for release this month (the company shipped GLM-5.4, built on a 750B-parameter base, on Monday) and now **may not launch until Q1 2027 or later** as new US computing restrictions bite. Rival **Moonshot AI expects the interval between major releases could double from six months to a year or longer if it loses access to overseas computing power**. The story pairs two pressure points: (1) hardware — US chip curbs limiting access to the accelerators frontier training runs on, and (2) a **crackdown on distillation** — the practice of training models against the API outputs of US frontier labs, which had been a workaround for hardware gaps. Sources described to Reuters that Z.AI had hoped to complete training and release GLM-5.5 by year-end. (Reuters — Nov 26)

**Why it matters:** This is the first credible reporting that the **combined effect of export controls and anti-distillation enforcement is measurably slowing Chinese frontier release cadence** — not just raising costs. If a 6-month release cycle stretches to 12+ months, the US/China capability gap widens on the schedule axis, even if per-run performance keeps converging. It also reframes the distillation channel as a strategic asset: labs that built "learn from the API" pipelines are now discovering the pipeline is a choke point.

**Sources:**
- https://www.reuters.com/world/china/us-chip-curbs-distillation-crackdown-threaten-chinese-ai-model-development-2026-11-26/

---

### 2. Microsoft Ignite 2026: Copilot Becomes the "Operating System for Work" — With Agent Identity, Governance and Cost Controls (Nov 25–26)

**What happened:** At Ignite 2026, Microsoft presented **Copilot as a shared experience for chat, coding and autonomous agents** — an "operating system for work" (Microsoft's product positioning, per InfoQ's recap). The substance is in the governance layer: Microsoft is **extending agent identity, governance and cost controls across Azure, Foundry, Entra and Defender**, so an organization can establish whose identity an agent acts under, oversee its activity, and meter its spend. Alongside that, Microsoft announced an **AI Transparency Initiative aligned with NIST's Agent Standards Initiative**, and CEO Satya Nadella — acknowledging the November 12 Microsoft 365 outage in his opening keynote — argued that customers should be able to **examine and independently verify what AI does**. Infrastructure announcements included **generally available Cobalt 200 virtual machines** (ARM), with some other releases remaining in preview. (InfoQ, techand.space — Nov 25–26)

**Why it matters:** The race for enterprise agentic AI is moving from *capability* to **control plane**. Agent identity (which Entra principal does an agent act as), per-agent cost metering, and verifiable audit trails are the features that let a CISO sign off on autonomous agents — and aligning with NIST's Agent Standards Initiative signals Microsoft wants the governance layer to be interoperable rather than proprietary. The "verify what AI does" framing, delivered days after a major outage, is a direct answer to the trust gap that has capped enterprise agent adoption.

**Sources:**
- https://www.infoq.com/news/2026/11/microsoft-ignite-2026-recap/
- https://techand.space/article/ai/2026-11-26-recap-of-microsoft-ignite-2026-copilot-as-the-work-os-and-agent-governance

---

### 3. Amazon Transcribe Turbo Enters Public Preview — Semantic Turn-Taking and Runtime ASR Hints for Voice Agents (Nov 25)

**What happened:** On Nov 25, AWS announced **Amazon Transcribe Turbo**, its next-generation speech-to-text model, in **public preview in US East (Ohio)** for batch and streaming (batch English is already generally available in most regions; additional batch languages in preview). Turbo improves accuracy out-of-the-box — **~14% lower word error rate in streaming English** (and ~11% in Portuguese, French, Italian, German, Spanish), ~16% lower WER across batch languages, and **~78% exact formatting** of numbers, dates, phone numbers and addresses (up from ~53%) — with no API or SDK changes. The two new voice-agent features launch in English (other languages by end of December): **Semantic Turn-Taking** detects when a caller is done speaking from *what they said and how they said it*, not silence alone — it won't cut off mid-sentence ("I'd like to transfer… $250 to savings") or make short answers wait on silence timeouts, responding in **~615 ms with a 5% interruption rate** via tunable `EndOfTurnThreshold`/`EagerEndOfTurnThreshold`/`EndOfTurnTimeout` events; and **Runtime ASR Hints** let the application send menu options, expected names and entity types (date, phone, currency) in a `ConfigureEvent` before each turn — on English customer-service data, hints raise **menu-routing accuracy from 87% to 97%**. Both features come at no additional charge. (AWS What's New, AWS Builder Center, Writeble — Nov 25–26)

**Why it matters:** Voice agents have been bottlenecked on the *conversation layer* of ASR — premature cutoffs and mishearing context-specific terms. Turbo pushes turn-taking from a fixed silence timer to a **semantic signal with per-question tunability**, and turns custom vocabulary into a per-turn API. This is infrastructure-level progress for the agent economy: every phone-based customer service, IVR and voice-agent product on AWS inherits the improvement for free.

**Sources:**
- https://aws.amazon.com/about-aws/whats-new/2026/11/transcribe-turbo-preview/
- https://builder.aws.com/content/3MbnTQKvOMxTZQbm34D6XV7hv8q/getting-started-with-amazon-transcribe-turbo-and-voice-agent-features
- https://writeble.com/2026/11/26/amazon-transcribe-turbo-semantic-turn-taking-runtime-asr-hints-voice-agents-preview-ohio/

---

### 4. Meta's Muse Agent Launches in the UK — 14 Brand Deals, Instagram Integration, and Regulator Warnings (Nov 25–26)

**What happened:** Meta's **Muse** AI agent became available in Britain on Tuesday (Nov 25), taking to a new market a product the company presents as able to search out a cheaper energy deal or sort a school calendar. Agentic systems of this kind carry out tasks rather than simply answer questions, which places Muse squarely in the contested territory of AI products, personal data and oversight. Meta has staked heavily on the shift: the BBC reported that **much of the $145bn Meta will spend this year goes to building out the technology**, and that Meta hopes **Muse will do for AI agents what WhatsApp did for messaging**. The mechanics are built around consent: per The Guardian, Muse cannot make a purchase or send an email without the user's permission, has **no visibility into passwords or payment methods**, does not share conversations with advertisers, and a separate **"security agent" checks its actions against granted permissions**. The Guardian reported Meta has signed deals with **14 British businesses** — among them **Marks & Spencer, Sainsbury's, easyJet and Trainline** — letting the agent navigate their websites more easily; the BBC also listed **Currys and Ocado** among UK firms working with the company. In parallel, **Instagram users in five markets gain an in-app assistant** and saved-post Collections in the US and Canada. The launch drew immediate regulatory attention: the **UK Information Commissioner's Office (ICO) is monitoring the rollout** over privacy and consumer protection, and the **UK financial watchdog warned that AI agents offering financial services could face regulatory action** as Meta moves to connect Muse to UK banking services. (The Independent AI, MarketScreener, BBC, The Guardian — Nov 25–26)

**Why it matters:** This is the first major **consumer agentic-AI launch in a regulated market with explicit regulator oversight from day one** — the ICO monitoring and the FCA's financial-services warning are the template for how the US, EU and UK will handle consumer agents. The "security agent checks actions against permissions" architecture and the consent-based design are the reference implementation for the trust layer every consumer agent will need.

**Sources:**
- https://theindependentai.com/briefing/meta-launches-muse-agent-in-uk-as-privacy-regulator-urges-consumer-cauti-0d6b6039-02d753dc
- https://ca.marketscreener.com/news/uk-financial-watchdog-delivers-ai-warning-as-meta-launches-adapted-muse-ce7851dbd98cf02c
- https://hk.marketscreener.com/news/regulators-issue-warnings-after-uk-brands-sign-up-to-meta-ai-assistant-ce7851dad081f025

---

### 5. SenseTime Ships SenseNova-RoboRSI-27B Full Release — An Open Embodied Agent That Outscored GPT-6 Astra and Moved to Real Robots (Nov 25)

**What happened:** SenseTime published the **full release of SenseNova-RoboRSI-27B** on Nov 25 — an open-weights **27B vision-language model for robot manipulation** that sits one level above a vision-language-action (VLA) policy. It looks at camera views and robot state, then decides whether to **request a motion from a VLA policy, review a proposed trajectory, or write code to compute and execute a gripper target pose ("Code as Policy")**, re-deciding after every action. In the released agent's runs, VLA motions were 41.9% of environment steps and code 58.1%. On the **RoboDojo** robotics simulation benchmark it averaged **34.7** (up from 10.0 for Preview), **surpassing the 27.6 recorded for GPT-6 Astra by the RoboDojo team** — though that is a distillation result (the teacher was GPT-6 Astra) and the 34.7 comes from a single seed/layout run by SenseTime's own harness. The headline sim-to-real claim: **the same weights, with no real-robot training or fine-tuning** (only camera, state and control interfaces adapted), achieved **6/10 (60%) pick-and-place on a Piper arm** (code-only) and **9/10 (90%) block stacking on Piper X** (VLA × code). It also uses **multi-round RSI** (recursive self-improvement — model and Harness co-evolved over three rounds) and a **VLA2Agent** technique that lifts end-effector predictions within 50 mm of target from 24.9% to 49.2%. Weights are on Hugging Face; the repo is `OpenSenseNova/SenseNova-RoboRSI`. (SenseTime, Hugging Face, i10x, GitHub — Nov 25–26)

**Why it matters:** This is a concrete, reproducible recipe for **open embodied agents that beat a frontier API model on a robotics benchmark** — and the "decision layer above the VLA" architecture (VLA for dynamic maneuvers, code for spatial precision) is the pattern likely to generalize. The sim-to-real transfer with zero real-robot data is the most important claim to watch, even at 10 trials per task.

**Sources:**
- https://www.sensetime.com/en/news/sensenova-roborsi-27b-full-release-20261126-1138
- https://huggingface.co/sensenova/SenseNova-RoboRSI-27B
- https://github.com/OpenSenseNova/SenseNova-RoboRSI
- https://i10x.ai/news/sensenova-roborsi-27b-open-robot-model-sim-to-real

---

## New Use Cases

### Direct-Answer "Fast Worker" Coding Models (Nov 25)
JetBrains released **Mellum2.1 Instruct** — a 12B MoE (2.5B active) coding model that **answers directly without a chain of thought**, generating **~half the tokens** of its Thinking sibling on repository-level tasks while resolving **40.4% of SWE-bench Verified** (up from 20.2%). Apache 2.0, with GGUF and MTP heads. The reusable pattern: a **fast, non-reasoning sub-agent** for tool loops, small fixes and code questions, paired with a stronger reasoning model for hard problems — a cost/latency tier for agentic software engineering.
*Source: https://blog.jetbrains.com/ai/2026/11/mellum2-1-instruct-is-out-bringing-faster-answers-for-coding-agents/*

### Safety Benchmarks for Money-Moving AI Agents (Nov 26)
Valory launched **OnchainBench**, the first open benchmark for AI agents that use crypto wallets, across nine EVM chains. In ~1,800 attack tests agents **lost funds in ~0.7%** of cases (13 of 1,793), with task-completion scores of 88.4–96.2%. Notably, **Anthropic's Claude Code and OpenAI's Codex met the safety bar when running DeepSeek V4.1 Flash but missed it on their makers' own frontier models** — an early signal that agent safety is a property of the harness-model pairing, not the model alone.
*Source: https://markets.businessinsider.com/news/currencies/valory-unveils-onchainbench-first-open-benchmark-to-test-how-safely-and-reliably-ai-agents-use-crypto-wallets-1036802704*

### Sovereign / On-Prem Enterprise AI as a Product Category (Nov 26)
Concierto AI went generally available, positioning **sovereign AI "at the rack level"** — frontier-grade assistants and a coding agent (C/Composer, C/Code) running entirely inside the customer's own VPC or data center, with data, IP and prompts never leaving the perimeter and no token-based pricing. This crystallizes the **on-prem agentic AI** use case that Sakana Namazu Small and Baidu ERNIE 5.5 Flash Preview (open-base + proprietary post-training, self-hostable) make technically feasible.
*Source: https://prnewswire.com/news-releases/concierto-ai-is-now-live-sovereign-ai-for-every-employee-inside-the-enterprises-own-cloud-or-data-center-302951168.html*

### State-Backed Consumer Agents With Mandatory Safeguards (Nov 26)
South Korea's National IT Industry Promotion Agency (NIPA) said its free state-backed **"AI for All"** service will add agent functions (e.g., **KTX train booking**, public-benefit alerts) next year, operated by SK Telecom, KT and Kakao consortia — with **stronger safeguards pledged** after the Pickle agent app drew complaints of placing unrequested calls to users' acquaintances and restaurants. The use case: **government-operated consumer agents with guardrails as a first-class design constraint**.
*Source: https://ajupress.com/view/20261126154432904*

### Unified Compute Allocation for Agents (Nov 25)
OpenAI began merging **ChatGPT Chat and Work into a single usage meter** for Pro subscribers (Nov 25), after admitting a billing mistake means heavy users burn limits **up to 40% faster**; Instant-model conversations stay unlimited. The use case: **a single budget envelope across chat + agentic work** as the default unit of compute allocation for agent products.
*Source: https://techcrunch.com/2026/11/25/openai-says-heavy-chatgpt-users-may-hit-limits-sooner-as-it-merges-chat-and-work/*

---

## Top Rated GitHub Projects Leveraging Agentic/Gen AI

| Repository | Stars* | What it does (agentic/Gen-AI angle) |
|---|---|---|
| [morluto/rea](https://github.com/morluto/rea) | 479,507 | **"Reverse engineer anything with agents"** — from app behavior down to native binaries (TypeScript, created Apr 14, 2026; currently the top-starred agentic repo). |
| [openclaw/openclaw](https://github.com/openclaw/openclaw) | 395,283 | **"The AI that really does things. Any OS. Any Platform. The lobster way. 🦞"** — a cross-platform, doer-style agent (TypeScript, created Nov 24, 2025). |
| [mattpocock/skills](https://github.com/mattpocock/skills) | 333,468 | **"Skills for Real Engineers"** — a skills collection straight from the author's `.agents` directory for coding agents (Shell, created Feb 3, 2026). |
| [affaan-m/ECC](https://github.com/affaan-m/ECC) | 311,177 | **Agent harness performance-optimization system** — skills, instincts, memory and search for agentic harnesses (JavaScript, created Jan 18, 2026). |
| [deepseek-ai/deepseek-harness](https://github.com/deepseek-ai/deepseek-harness) | 287,538 | **"Everything is a Plugin"** — DeepSeek's agent harness (TypeScript, created Aug 13, 2026). |

\* Star counts verified live via the GitHub API on November 26, 2026 (top-starred agentic repositories created since Nov 1, 2025). Also trending this week: **multica-ai/andrej-karpathy-skills** (235,895★ — a single CLAUDE.md to improve Claude Code behavior, derived from Andrej Karpathy's notes), **DietrichGebert/ponytail** (199,241★ — makes your agent "think like the laziest senior dev in the room"), and **obra/superpowers** (327,271★ — the agentic skills framework & methodology that has now passed 327k stars).

---

## Security & Remediation Watch

**New this cycle (Nov 25–26):**

1. **CISA KEV Nov 25 — a batch of ten actively exploited flaws, led by five Mitel MiCollab RCE-class entries (federal due Nov 28).** On Nov 25, CISA added **ten** vulnerabilities to its Known Exploited Vulnerabilities catalog (note: secondary sources that claimed "only three" or mixed in the Drupal/Idunno/Optimizely entries were describing the *Nov 24* alert — the official Nov 25 count is ten). The headline cluster is **Mitel MiCollab**, whose Audio/Web/Video Conferencing (AWV) component carries **five** concurrently exploited flaws, all published Nov 19 under MITRE advisory MISA-2026-0012:
   - **CVE-2026-133323 — OS command injection (CVSS 10.0).** Unauthenticated attacker executes arbitrary system commands.
   - **CVE-2026-133303 — XML injection (CVSS 9.8).** Unauthenticated attacker executes arbitrary commands via pre-staged malicious content.
   - **CVE-2026-133324 — not failing securely.** Unauthenticated attacker bypasses authentication controls.
   - **CVE-2026-133275 — unrestricted upload of dangerous file type.** Unauthenticated arbitrary file upload.
   - **CVE-2026-133311 — weak authentication (due Dec 9).** Unauthenticated access to sensitive info via a system-generated random identifier.
   **Remediate:** apply Mitel's MISA-2026-0012 patch immediately; MiCollab is internet-facing by design (conferencing), so treat all exposed AWV endpoints as compromised until patched and audit for unauthorized actions/file uploads.
2. **CISA KEV Nov 25 — HPE Juniper Session Smart root command injection (CVE-2026-103406, CVSS 9.8, due Nov 28).** An OS command-injection flaw that lets a **remote attacker execute arbitrary commands as root via a specially crafted salt minion ID** on Juniper Session Smart Conductor and Router. **Remediate:** apply Juniper's patch; if the Conductor/Router is exposed to untrusted networks, treat the salt channel as compromised until patched and review for prior root-level command execution.
3. **CISA KEV Nov 25 — Vates Xen Orchestra authentication bypass (CVE-2026-133469, CVSS 9.8, due Nov 28).** An **improper-validation-of-input** flaw lets an unauthenticated attacker **bypass authentication and act with administrative privileges via a specially crafted token containing an empty JSON object**. Xen Orchestra is widely deployed as the management UI for XenServer/XCP-ng virtualization stacks, so an exposed instance hands an attacker the hypervisor control plane. **Remediate:** apply Vates' fix (advisory 2026/vates-sa-2026-062); restrict XO to trusted networks/VPN and audit for unauthorized admin actions.
4. **CISA KEV Nov 25 — three Danfoss AK-SM 800A Series entries (OT/ICS).** The Danfoss AK-SM 800A Series (a commercial refrigeration/heat-pump controller) gained three KEV entries: **CVE-2023-25914** (path traversal — read server system files via the XML interface, CVSS 8.8), **CVE-2023-25915** (improper input validation — remote arbitrary command execution, CVSS 9.9), and **CVE-2025-41450** (improper authentication — generate a web report exposing internal IPs, usernames and store names, CVSS 8.2). Federal due dates Nov 28 / Dec 9. **Remediate:** apply Danfoss DSA-2023-08-01 and the 2025 advisory; these are physical-world (cold-chain, HVAC) controllers, so exposure is an OT/ICS supply-chain and physical-security concern.
5. **F5 NGINX — active exploitation of heap-buffer-overflow and use-after-free (CVE-2026-123007, CVE-2026-123633, both CVSS 8.1).** Singapore's Cyber Security Agency (CSA) alerted on Nov 26 that attackers are **actively exploiting** a high-severity F5 NGINX flaw to access sensitive information, modify data and cause denial of service, with a **public PoC**. CVE-2026-123007 is a **heap buffer overflow in NGINX HTTP/2 processing** (flow-control window exceeding the allowed threshold) that can crash/corrupt the worker process or RCE (where ASLR is disabled/bypassed); CVE-2026-123633 is a **use-after-free in the worker process** causing DoS or potential RCE. Affected: **F5 NGINX Open Source 1.9.5–1.30.6 and 1.31.0–1.31.8; NGINX Plus 37.0.0–37.0.8.0, 37.1.0–37.3.0.0, and R34/R35/R36**. **Remediate:** update to the latest F5 NGINX immediately; NGINX is one of the most-deployed web servers/proxies on the internet, so any internet-facing instance should be treated as potentially targeted.
6. **Carry-forward / still-hot (Nov 23–25):** The **hexpm/hex.pm CVSS-10.0 RCE** (CVE-2026-129514, six production servers compromised, personal-data breach reported) and the **Cisco Expressway CVE-2026-76466** (CVSS 9.8, root RCE, clustered deployments, exploited in the wild per F6) remain actively exploited; and the **BerriAI LiteLLM (CVE-2026-40217)**, **VMware vCenter (CVE-2026-123890)** and **Drupal Core (CVE-2026-132165)** flaws are all confirmed under active attack. If you run any of these, patch and hunt for compromise now — these are the "AI tooling + widely-used infrastructure" class that the KEV catalog keeps flagging.

*(CISA KEV catalog v2026.11.25, CISA alerts, CSA Singapore, InfoSecNexus, CVE Brief, BleepingComputer, The Hacker News — Nov 25–26)*

---

## Sources

- Reuters — US chip curbs, distillation crackdown threaten Chinese AI model development (Nov 26): https://www.reuters.com/world/china/us-chip-curbs-distillation-crackdown-threaten-chinese-ai-model-development-2026-11-26/
- InfoQ — Microsoft Ignite 2026 recap (Copilot as work OS, agent governance): https://www.infoq.com/news/2026/11/microsoft-ignite-2026-recap/
- techand.space — Microsoft Ignite 2026 recap (Nov 26): https://techand.space/article/ai/2026-11-26-recap-of-microsoft-ignite-2026-copilot-as-the-work-os-and-agent-governance
- AWS What's New — Amazon Transcribe Turbo public preview (Nov 25): https://aws.amazon.com/about-aws/whats-new/2026/11/transcribe-turbo-preview/
- AWS Builder Center — Getting Started with Transcribe Turbo and Voice Agent Features: https://builder.aws.com/content/3MbnTQKvOMxTZQbm34D6XV7hv8q/getting-started-with-amazon-transcribe-turbo-and-voice-agent-features
- The Independent AI — Meta launches Muse in UK as privacy regulator urges caution: https://theindependentai.com/briefing/meta-launches-muse-agent-in-uk-as-privacy-regulator-urges-consumer-cauti-0d6b6039-02d753dc
- MarketScreener — UK financial watchdog delivers AI warning as Meta launches adapted Muse: https://ca.marketscreener.com/news/uk-financial-watchdog-delivers-ai-warning-as-meta-launches-adapted-muse-ce7851dbd98cf02c
- SenseTime — SenseNova-RoboRSI-27B Full Release: https://www.sensetime.com/en/news/sensenova-roborsi-27b-full-release-20261126-1138
- Hugging Face — sensenova/SenseNova-RoboRSI-27B: https://huggingface.co/sensenova/SenseNova-RoboRSI-27B
- GitHub — OpenSenseNova/SenseNova-RoboRSI: https://github.com/OpenSenseNova/SenseNova-RoboRSI
- i10x — SenseNova-RoboRSI-27B open robot model (Nov 26): https://i10x.ai/news/sensenova-roborsi-27b-open-robot-model-sim-to-real
- JetBrains Blog — Mellum2.1 Instruct Is Out (Nov 25): https://blog.jetbrains.com/ai/2026/11/mellum2-1-instruct-is-out-bringing-faster-answers-for-coding-agents/
- Hugging Face — JetBrains/Mellum2.1-12B-A2.5B-Instruct: https://huggingface.co/JetBrains/Mellum2.1-12B-A2.5B-Instruct
- Valory / Business Insider — OnchainBench, first open benchmark for AI agents using crypto wallets (Nov 26): https://markets.businessinsider.com/news/currencies/valory-unveils-onchainbench-first-open-benchmark-to-test-how-safely-and-reliably-ai-agents-use-crypto-wallets-1036802704
- PRNewswire — Concierto AI is Now Live (sovereign AI, Nov 26): https://prnewswire.com/news-releases/concierto-ai-is-now-live-sovereign-ai-for-every-employee-inside-the-enterprises-own-cloud-or-data-center-302951168.html
- Aju Press — Korea's free AI service to add agents, tighten safeguards (Nov 26): https://ajupress.com/view/20261126154432904
- TechCrunch — OpenAI merges ChatGPT Chat and Work into one usage meter (Nov 25): https://techcrunch.com/2026/11/25/openai-says-heavy-chatgpt-users-may-hit-limits-sooner-as-it-merges-chat-and-work/
- CISA — Adds 10 Known Exploited Vulnerabilities to Catalog (Nov 25): https://www.cisa.gov/news-events/alerts/2026/11/25/cisa-adds-10-known-exploited-vulnerabilities-catalog
- CISA Known Exploited Vulnerabilities Catalog: https://www.cisa.gov/known-exploited-vulnerabilities-catalog
- Cyber Security Agency of Singapore — Active Exploitation of Vulnerability in F5 NGINX (Nov 26): https://www.csa.gov.sg/alerts-and-advisories/alerts/al-2026-168
- InfoSecNexus — Live Cybersecurity Brief, Nov 25: https://infosecnexus.com/live-cybersecurity-brief/
- CVE Brief — Daily Critical Vulnerability Intelligence, Nov 25: https://cvebrief.com/

---

## Compilation Note

Compiled Thursday, November 26, 2026 (09:10–09:45 PT, America/Los_Angeles) by the ai-research cron job. Research pass covered Nov 25–26, 2026 via live web search across Reuters, AWS What's New / AWS Builder Center, InfoQ, techand.space, SenseTime / Hugging Face / i10x, the JetBrains blog, Valory / Business Insider, PRNewswire, Aju Press, TechCrunch, The Independent AI / MarketScreener, and the CISA KEV catalog (v2026.11.25) plus CSA Singapore, InfoSecNexus, CVE Brief, BleepingComputer and The Hacker News. Today's edition is materially distinct from the November 25 edition: **five brand-new anchor stories** (the Reuters Chinese-AI compute-curb story, Microsoft Ignite's Copilot governance pivot, Amazon Transcribe Turbo's voice-agent features, Meta's Muse UK launch with regulator warnings, and SenseTime's RoboRSI-27B embodied-agent release) replace the Nov 25 anchors (the Axios "too powerful to release" story, the OpenAI/Anthropic math week, Baidu ERNIE 5.5 Flash Preview, Sakana Namazu Small, and Claude Ship). The **Security & Remediation Watch** is led by the **Nov 25 KEV batch of ten** (the five Mitel MiCollab flaws, HPE Juniper Session Smart, Vates Xen Orchestra, and three Danfoss AK-SM 800A OT/ICS entries) and **F5 NGINX active exploitation** (CVE-2026-123007 / CVE-2026-123633) — both new relative to the Nov 25 edition, which had led with the Nov 24 KEV batch (Drupal, Idunno AntiCsrf, Optimizely) and the hexpm/hex.pm compromise. GitHub trending figures were re-verified live via the GitHub API on November 26, 2026. Figures and benchmark scores are as reported by the cited outlets and are not independently verified.
