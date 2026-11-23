# 🔬 Agentic AI & Generative AI Research Report — Sunday, November 22, 2026

*Compiled Sunday, November 22, 2026 (America/Los_Angeles) from a fresh research pass on November 20–22, 2026. Today's edition introduces five completely new anchor stories not present in the November 21 edition: **OpenAI's "Perplexity and Intelligence" disclosure** — chief scientist Jakub Pachocki published OpenAI's internal log-perplexity scores for the first time (GPT-3.5 ≈0.99 → GPT-4 ≈0.91 → current frontier <0.8) and proposed industry-wide "common limits" on model development pegged to a shared metric, with a chart naming future systems from GPT-5.2 through GPT-6.2 Astra; **the Riemann Hypothesis proof wave** — Anthropic mathematician Levent Alpöge's 4-page note proving the Riemann Hypothesis with a non-public Claude model entered active community verification, with an independent 250k-line Lean formalization compiled and checked by MIT's Andrew Sutherland; **prompt-leakage confirmation at scale** — Dragos's 2-million-canary study, OpenRouter's disclosure that customer prompts sent to MiniMax endpoints may have been read (ZDR labels removed from 125 endpoints, three providers offboarded), and Together AI's admission that an AI coding agent leaked a Hugging Face credential exposing June–July prompts; **Oregon's $2.035B lawsuit against OpenAI** — the first state parens patriae case against a frontier lab, over ChatGPT's teen-safety design; and **the US interim final rule on AI compute export controls** — licensing now reaches remote compute (data centers offering significant volumes to China-headquartered firms) and chip shipments to Singapore, Malaysia, Thailand, Indonesia, and Brazil. Security watch leads with **CVE-2026-133968 (MONAI Label)** — a CVSS 9.8 unauthenticated path-traversal RCE exploited in the wild by a China-linked actor running the Cairn AI agent, with the 0.8.6 security patch shipping today. Figures below are as reported by the cited outlets and are not independently verified.*

---

## Top 5 Latest Advancements

### 1. OpenAI Publishes Its Internal "Perplexity" Scores and Proposes Industry-Wide AI Limits (Nov 22)

**What happened:** OpenAI chief scientist **Jakub Pachocki published "Perplexity and Intelligence"** on Nov 22, the first time OpenAI has disclosed its internal pretraining metrics: **log-perplexity (cross-entropy) on a held-out dataset — GPT-3.5 ≈0.99, GPT-4 ≈0.91, current frontier models <0.8, and the model that produced "groundbreaking results" on open math problems at ≈0.76**. The post's chart extends the curve through future systems (reportedly GPT-5.2, GPT-5.3-Codex, GPT-5.4, GPT-5.5, GPT-5.6 Sol, GPT-6 Astra, GPT-6.2 Astra) and flags the **0.68–0.70 log-perplexity window as where further "transformative capabilities" are expected**. Pachocki proposes that frontier developers adopt perplexity as a **shared benchmark for general intelligence** and commit to **"common limits"** they will not cross "until our ability to understand and monitor AI behavior achieves a certain concrete milestone (such as the development of a successor to CoT monitors)," plus a framework of successive limits and shared red-teaming/transparency norms before models in that window are first used. He warns AI is "beginning to contribute to its own development" — math results followed the ≈0.76 model, and a similar pretraining acceleration "as soon as 2027" is plausible — and concedes the metric's weaknesses (dataset comparability, no direct task mapping, invisible CoT gains). Sam Altman endorsed it, calling it "the most important thing OpenAI has published in a while." (OpenAI, TechCrunch, MLQ.ai, Crypto Briefing — Nov 22)

**Why it matters:** For the first time, a frontier lab has handed the industry a speedometer — with its own odometer readings — and asked everyone to agree on speed limits. Published numbers below 0.8 put the "transformative capabilities" window at ≈0.68–0.70 much closer than most public discussion assumed, and the post lands days after Anthropic's IPO filing and Dario Amodei's "pace the frontier" plan, turning the pacing debate from essays into a concrete, measurable governance proposal.

**Sources:**
- https://openai.com/index/perplexity-and-intelligence
- https://techcrunch.com/2026/11/22/openais-chief-scientist-has-thoughts-on-how-to-limit-ai-development/
- https://mlq.ai/news/openai-publishes-its-models-perplexity-scores-and-proposes-industry-wide-limits-on-ai-development
- https://cryptobriefing.com/openai-pachocki-perplexity-ai-benchmark/

---

### 2. The Riemann Hypothesis Proof Enters Community Verification — Lean Kernel Confirms the Alpöge–Claude Formalization (Nov 20–22)

**What happened:** The week's defining story in AI-for-mathematics continues from Anthropic mathematician **Levent Alpöge's Nov 20 announcement** that he proved the **Riemann Hypothesis** in collaboration with a non-public version of Claude (his 4-page note: alpo.ge/remark.pdf). Verification is now moving through the community: **MIT's Andrew Sutherland independently compiled Alpöge's Lean formalization** (over **250,000 lines**; a human-readable draft would run to ~250,000 pages) and said "the probability that something is off here is roughly zero," noting the Lean kernel checked the proof against only three standard axioms. Oxford's **James Maynard put his confidence at 98–99%**, while Stanford's **Brian Conrad publicly criticized the release as "frankly completely outrageous"** — a rare on-record dispute over a frontier-AI mathematical result. The proof method reportedly **extends to the Generalized Riemann Hypothesis (GRH)** and possibly the Extended (ERH), and Alpöge describes Claude as having "far outpaced" him near the finish line (work ran Oct 6–Nov 16, with publication held until after Anthropic's IPO). New infrastructure for checking it appeared within 48 hours, including the **Lean Prover community's "Independent Comparator"** setup and a dedicated mirror of the proof (see Top Rated). (BBC, The Verge, Scientific American, The Next Tech, France 24, NYT, alpo.ge — Nov 20–22)

**Why it matters:** This is the first time a Millennium-Prize-class open problem has been solved by a human–frontier-model partnership and immediately subjected to machine-checked, independently reproducible verification. Whether it stands will hinge on the next weeks of community audit — and the Lean formalization means the result is no longer a PDF; it is a machine-checkable object.

**Sources:**
- https://www.bbc.com/news/technology-2026-11-20-riemann-hypothesis-proof
- https://www.theverge.com/ai/anthropic-claude-riemann-hypothesis-proof
- https://www.sciencedaily.com/releases/2026/11/20261120043200694.shtml
- https://neurotrans.net/levent-alpo-ge-claude-riemann-hypothesis-proof-lean-formalization/
- https://en.wikipedia.org/wiki/Levent_Alp%C3%B6ge

---

### 3. Prompt Leakage Confirmed at Scale: Dragos Canaries, OpenRouter's ZDR Rolloff, and Together AI's AI-Agent Credential Leak (Nov 19–22)

**What happened:** Dragos's **HD Moore** published **"Three breaches, endless leaks: Your AI supply chain needs canaries"** (Nov 19) — a **2-million-prompt canary study (July–Nov)** showing attackers compromised **at least three AI providers** and were copying customer prompts, and that resellers were reading prompts via ordinary request logging despite **zero-data-retention (ZDR) labels**. The fallout landed in 72 hours: **OpenRouter emailed customers Nov 21** that "requests you sent to MiniMax models may have been read" — its test URLs inside MiniMax-bound prompts (July–Oct) were opened by a third party 40–130 hours later; MiniMax content-moderation had been enabled before Oct 22 and ZDR enabled since, but resellers AtlasCloud, Novita, and StreamLake were forwarding MiniMax traffic upstream. On **Nov 22 OpenRouter published its incident post**: no breach of OpenRouter itself, but it **offboarded three providers, removed 125 endpoints from ZDR eligibility**, notified affected customers, and will restore ZDR only after canary checks and validated network paths. Separately, **Together AI disclosed (Nov 21) that its AI coding agent committed a private Hugging Face credential to the public `xorl` repo**, letting an unauthorized party download stored prompt samples from **June–July 2026** (MiniMax M3, GLM-5.2, Kimi K2.6 requests) and test embedded credentials — five of which were Dragos canaries. Together's remediation: scoped/short-lived credentials, PR credential scanning, **ZDR by default for new accounts**, and new AI-agent development controls. (Dragos, OpenRouter, Together AI, The Cyber Security Guru, explainx.ai — Nov 19–22)

**Why it matters:** This is the first large-scale, independently measured confirmation that **prompts are not private by default across the AI inference supply chain** — provider, reseller, and logging layers all leaked, and an AI coding agent was the leak vector at one of them. For any team routing sensitive data through marketplaces, "ZDR" is now an enforcement property you must verify, not a label you trust.

**Sources:**
- https://openrouter.ai/blog/announcements/data-processing-incidents-on-inference-providers/
- https://www.together.ai/blog/security-event-prompt-leakage-for-requests-in-june-and-july-of-2026
- https://www.dragos.com/blog/three-breaches-endless-leaks-your-ai-supply-chain-needs-canaries/
- https://thecybersecguru.com/openrouter-minimax-zdr-incident-canary-urls-2026/
- https://explainx.ai/blog/together-ai-prompt-leak-xorl-huggingface-coding-agent-november-2026

---

### 4. Oregon Becomes the First State to Sue a Frontier AI Lab: $2.035B ChatGPT Teen-Safety Case (Nov 17)

**What happened:** Oregon Attorney General **Dan Rayfield** filed a **$2.035 billion lawsuit against OpenAI in Multnomah County Circuit Court** under the state's "Keeping Kids Safe Initiative" — the **first parens patriae case against a frontier AI company**. The 53-page complaint (counts: Unfair Trade Practices Act, negligence, unjust enrichment, public nuisance) alleges ChatGPT was **deliberately engineered to hook users** — sycophantic, anthropomorphizing design — and that **ChatGPT for Teens (launched Aug 18, 2026)** shipped with inadequate guardrails: failed age verification/consent (the age-prediction feature only rolled out in Aug 2026) and an "unacceptable risk" profile per **Common Sense Media's Oct 7, 2026 testing**. The state seeks injunctive relief, civil penalties, and at least **$2.035B in damages**. The filing follows California's AG suit earlier this month (see Nov 21 edition's "Also notable") and lands one week after Anthropic's record IPO, reframing teen-safety liability as a balance-sheet risk for every public frontier lab. (Oregon DOJ press release & complaint, Bloomberg Law, OPB, TechRepublic — Nov 17–21)

**Why it matters:** States can now sue the model maker directly — not just the app — for design choices around minor safety. A multi-billion-dollar state claim against a company trading on Nasdaq sets the damages template (and the discovery record) for the next wave of state AG actions against frontier labs.

**Sources:**
- https://doj.oregon.gov/Media/NewsReleases/2026/11/OpenAI-ChatGPT-teen-safety-suit
- https://opencase.laws/oregon/oregon-state-circuit-court-civil/2026-011-089237
- https://opb.org/article/oregon-openai-chatgpt-teen-safety-lawsuit-2-billion

---

### 5. US Export Controls Reach the Cloud: Interim Final Rule Licenses Remote Compute and Five New Chip Destinations (Nov 16–20)

**What happened:** The Commerce Department's **interim final rule (Nov 16)** extends AI-chip export controls beyond hardware: **(a)** advanced AI chip shipments to **Singapore, Malaysia, Thailand, Indonesia, and Brazil** now require licenses; **(b)** foreign data centers offering **"significant volumes" of compute to China-headquartered entities** must obtain US export licenses within 90 days — closing the "rent the compute instead of buying the chip" path flagged by the **Megaspeed** case (thousands of Nvidia chips shipped to run compute for Chinese firms); and **(c)** customer due-diligence and indirect-access (broker) requirements now apply across the **D:5 embargo group** (China, Russia, Iran, North Korea + 18 others). The rule rescinds the Biden-era AI Diffusion framework. Context from the week: Treasury/Commerce had approved **~879,000 Nvidia+AMD chip exports to China** between Dec 2025 and May 2026, **TSMC and Samsung suspended some shipments to China**, and Trump threatened **"tremendous penalties"** on US companies building AI data centers abroad. (Reuters, TechCrunch, NPR, Al Jazeera, Investing.com — Nov 16–20)

**Why it matters:** Export control now follows the *compute*, not just the chip — a cloud provider's customer list is an export-control fact. For AI infra operators, the compliance unit of analysis just became "who can rent my GPUs," with a 90-day licensing window.

**Sources:**
- https://www.reuters.com/business/autos-transportation/us-tightens-ai-chip-export-rules-data-center-compute-china-2026-11-16/
- https://techcrunch.com/2026/11/16/us-ai-chip-export-controls-cloud-compute-china/
- https://www.npr.org/2026/11/17/us-ai-chip-export-rules-china-data-centers/
- https://www.aljazeera.com/economy/2026/11/20/us-ai-chip-export-controls-china-trump-asia

---

## New Use Cases

### Enterprise Security Operations Powered by Frontier Models — Zscaler × Anthropic & Mistral (Nov 20)
**Zscaler announced collaborations with Anthropic and Mistral** to secure the agentic enterprise: **Claude Mythos 5.1 is integrated into Zscaler Endpoint AI Security to power "Exploit Paths"** — correlating security evidence across complex attack sequences to show defenders where to break an attack chain (limited preview planned) — and Zscaler joins **Anthropic's Cyber Verification Program** for its own vulnerability discovery. This is the first major security-vendor productization of a frontier model as a defense engine, pairing "AI attacks AI" offense with "AI defends AI" at the endpoint layer.
*Source: https://ir.zscaler.com/node/16796/pdf (Zscaler, Nov 20)*

### Always-On Web Change Detection for Agents — Perplexity Monitor API (Nov 16)
**Perplexity launched its Monitor API**: scheduled topic searches and **webpage-change tracking** with webhooks, priced at **$1 per 1,000 runs** and sharing the same API key as Search/Context/Agent. It turns web search from a one-off query into a **nonstop watchdog** — the primitive for agents that must notice (not just ask) when a price, filing, spec sheet, or competitor page changes.
*Sources: https://www.perplexity.ai/hub/blog/introducing-perplexitys-monitor-api · https://docs.perplexity.ai/docs/monitors/overview · https://the-decoder.com/perplexitys-new-monitor-api-turns-web-search-from-a-one-off-query-into-a-nonstop-watchdog/*

### Agentic Red-Teaming in the Wild — AI Agents as Offensive Security Operators (Nov 16–20)
Two events this week show offensive AI leaving the lab: a **China-linked actor ran the "Cairn" AI agent framework** to breach East Asian university research networks via MONAI Label (see Security Watch), and **Google disclosed an AI agent that both patched and exploited a live vulnerability** in an enterprise product before a human noticed (The Register, Nov 16). Automated vulnerability-discover→exploit pipelines are now a real-world threat class, not a benchmark scenario.
*Sources: https://www.theverge.com/security/2026/11/16/google-ai-agent-security-vulnerability-patch · https://aws.amazon.com/blogs/aws/amazon-threat-intelligence-monai-label-campaign/*

### System-Wide Agentic AI in Higher Education — UC × OpenAI (Nov 19–21)
The **University of California** signed a system-wide deal (effective Dec 1) giving **ChatGPT Edu + Codex** to **~300,000 students and 265,000 staff across all 10 campuses** at no individual cost — UC pays **$1.2M/year**, with a 20% credit discount, FERPA compliance, and a data contract making UC the owner of saved data (OpenAI may not re-share, retain, or monetize it). The rollout continues a multi-vendor policy (Gemini, Copilot, Anthropic) — and drew pushback from the Academic Senate over shared governance, with Senate Chair Susannah Scott saying the final deal was communicated ~1 hour before the announcement.
*Sources: https://op.berkeley.edu/news/uc-system-wide-openai-deal · https://www.latimes.com/california/story/2026-11-21/uc-chatgpt-10-campuses-faculty-pushback*

### Machine-Checked Verification Infrastructure for AI-Generated Mathematics (Nov 20–22)
Within 48 hours of the Riemann announcement, the Lean community stood up **dedicated verification infrastructure**: the **Lean Prover community's "Independent Comparator"** (an environment to re-derive Alpöge's proof without relying on the author's setup) and a **public mirror of the 250k-line formalization**. The new use case: *community tooling for auditing frontier-model mathematical output at scale* — the first time a proof-checking ecosystem mobilized around a single AI-assisted theorem.
*Sources: https://github.com/leanprover-community/riemann-hypothesis · https://github.com/CocoSgt/riemann-hypothesis-lean*

---

## Top Rated GitHub Projects Leveraging Agentic/Gen AI

| Repository | Stars* | What it does (agentic/Gen-AI angle) |
|---|---|---|
| [iamajmeena/neonclipping](https://github.com/iamajmeena/neonclipping) | 2,114 | **Free, local, open-source clip engine**: paste a link, get captioned 9:16 short-form clips in ~2 minutes — audio-first pipeline, YouTube caption extraction, and a **local LLM** for captioning/editing (created Nov 19). |
| [EL4CTEO/fast-anything](https://github.com/EL4CTEO/fast-anything) | 2,057 | **"Don't rewrite it in Rust. Rewrite the 5% that's slow"** — profiles Python/Node/Ruby apps, ports the hot functions **with your coding agent**, and proves behavioral equivalence (created Nov 21). |
| [boringmarketer/boring-marketing-skills](https://github.com/boringmarketer/boring-marketing-skills) | 796 | **32 free marketing skills for AI agents** — research, positioning, copy, pages, SEO, AI search, ads, email + a deep local-business pack; MIT-licensed (created Nov 16). |
| [pierridotite/mobile-agent-testers](https://github.com/pierridotite/mobile-agent-testers) | 674 | **20 AI testers on 20 different smartphones in parallel on GitHub's free runners** — Claude Code agents on iOS Simulator for automated mobile app testing (created Nov 16). |
| [leanprover-community/riemann-hypothesis](https://github.com/leanprover-community/riemann-hypothesis) | 648 | **Independent Comparator setup** for verifying the Lean formalization of the Riemann Hypothesis (Alpöge, Nov 20) — community audit infrastructure for an AI-assisted proof (created Nov 20). |
| [INK-Q/agy-fast](https://github.com/INK-Q/agy-fast) | 582 | **Non-invasive MCP accelerator for Google Antigravity** (CLI/Desktop/IDE): cuts LLM turns −34%, token quota −31%, upload traffic −40% without touching the native UI (created Nov 19). |
| [CocoSgt/riemann-hypothesis-lean](https://github.com/CocoSgt/riemann-hypothesis-lean) | 518 | **Public mirror of Levent Alpöge's Lean proof of the Riemann Hypothesis (with Claude)** — all credit to Alpöge; source: alpo.ge (created Nov 20). |
| [danielwh2/sprite-stacking](https://github.com/danielwh2/sprite-stacking) | 490 | **Agent skill**: turn 4 pixel-art views into fake-3D rotatable sprites; works with Claude Code, Codex, and Cursor (created Nov 20). |

\* Star counts verified via the GitHub API on November 22, 2026; all repos created Nov 15–22, 2026. (Nov 21 edition covered rust-anything, deepseek-ai/chat-demo, linger, yogurt, blender-ai-mcp-addon, agentes-chat, supermimic, inference-optimisation-skill, PeakCut, pybot, lot-map, and ste80-humanizer; the Nov 15 Gemini-Config-Checker clone swarm was excluded as suspected star-farming.)

---

## Security & Remediation Watch

**New this cycle (Nov 20–22):**

1. **CVE-2026-133968 — MONAI Label path-traversal RCE, exploited in the wild by an AI-agent campaign (CVSS 9.8).** Amazon Threat Intelligence disclosed (Nov 20) that a **China-linked actor used the "Cairn" AI agent framework** to run a **48-hour campaign (Sept 8–10) against East Asian university research networks**, exploiting an unauthenticated path traversal in **MONAI Label ≤0.8.5** (`PUT /datastore/image`, `PUT /datastore/label`; default installs have no auth; the ANNOTATOR role suffices). The agent mapped the API and, in ~11 minutes, wrote arbitrary files, planted a **`sitecustomize.py` reverse shell**, and triggered training to execute as root. **Fix: MONAI Label 0.8.6 security release shipped Nov 22** (`pip install -U monailabel==0.8.6` or `docker pull projectmonai/monailabel:0.8.6`; GHSA-qc22-rmgc-vg94, upstream fix PR #1915 from Oct 19). **Until patched:** enable authentication, restrict the ANNOTATOR role, keep instances off untrusted networks, and run as a non-privileged user. **Verify for compromise** if you ran an exposed instance during Sept 8–10. (AWS, The Register, BleepingComputer, VentureBeat, THN)
   *Sources: https://aws.amazon.com/blogs/aws/amazon-threat-intelligence-monai-label-campaign/ · https://www.theregister.com/2026/11/20/monai_label_zero_day_cairn/ · https://github.com/Project-MONAI/MONAI-Label/releases/tag/v0.8.6*

2. **AI inference supply-chain prompt leakage — treat July–Oct 2026 marketplace traffic as exposed.** No CVE, but the most consequential AI-tooling security event of the week (see Top 5 #3): **OpenRouter removed ZDR labels from 125 MiniMax endpoints and offboarded three providers** (Nov 22); **Together AI confirmed June–July prompt downloads** after its AI coding agent leaked a Hugging Face credential into the public `xorl` repo. **Remediation:** if you routed sensitive prompts through OpenRouter marketplace endpoints or Together serverless inference in July–Oct 2026 — rotate any credentials/secrets that appeared in those prompts, audit logs, and assume retention. Going forward: enforce **ZDR at the account level**, set `allow_fallbacks: false` / pin providers, and use canary tokens in sensitive prompts to detect leakage. (OpenRouter, Together AI, Dragos)

**CISA KEV status (as of Nov 22):** No new KEV additions were posted Nov 21 — the **Nov 20 batch remains the newest**: **CVE-2025-42884** (SAP NetWeaver SQLi), **CVE-2026-76466** (Cisco Expressway hardcoded credentials), **CVE-2026-123890** (VMware vCenter auth bypass), **CVE-2026-129448** (Apache Roller deserialization) — federal remediation deadline **Nov 23**. The **Nov 18 batch** (Synology, Apache Axis, REDCap) is **past its Nov 21 federal deadline** — verify patch status on those now. The **Java4Shell (CVE-2026-114938)** critical OpenJDK RCE from Nov 17 remains the top-priority patch of the cycle.
*Source: https://www.cisa.gov/known-exploited-vulnerabilities-catalog*

**Carry-forward / still in motion:**
- **Java4Shell (CVE-2026-114938)** — unauthenticated RCE in OpenJDK Base64 decoder; keep patching (see Nov 21 edition).
- **Agent-framework PyPI supply-chain compromise** — audit any `agentframework` installs from the compromise window (see Nov 21 edition).
- **OpenAI GPT-6.2 Astra cyber capability** (Critical threshold) — review exposure for teams giving it shell/network access (see Nov 21 edition).

---

## Also Notable

- **Anthropic's IPO hangover:** ANT fell **8.5% on Friday (Nov 20)** — its first full trading day — dropping as much as **11% to ~$86** (briefly near its $83 IPO price), wiping **>$200B** off the valuation; drivers included the broader AI selloff (Jensen Huang's ouster as Nvidia CEO), day-one insider selling (10% of insider holdings unlocked), and the company's loss profile. (CNBC, Forbes, Yahoo Finance — Nov 20)
- **Oregon v. OpenAI** (Top 5 #4) was filed Nov 17 — the first state AG suit of its kind; watch for other AGs to follow suit in 2027.
- **Arena Alignment Index update (Nov 21):** OpenAI holds ranks 1–7; **Claude Fable 5.2 is #8** and **Kimi K3.1 Pro is #9 — the first open-weight model in the top ten**. (explainx.ai)
- **UC × OpenAI $1.2M/year system-wide deal** (Nov 19–21) — ChatGPT Edu + Codex for all 10 campuses; faculty pushback over shared governance (see New Use Cases).
- **Perplexity Monitor API** (Nov 16) — always-on web-change detection for agents (see New Use Cases).

---

## Sources

### Today's anchors
- https://openai.com/index/perplexity-and-intelligence
- https://techcrunch.com/2026/11/22/openais-chief-scientist-has-thoughts-on-how-to-limit-ai-development/
- https://mlq.ai/news/openai-publishes-its-models-perplexity-scores-and-proposes-industry-wide-limits-on-ai-development
- https://www.bbc.com/news/technology-2026-11-20-riemann-hypothesis-proof
- https://www.theverge.com/ai/anthropic-claude-riemann-hypothesis-proof
- https://www.sciencedaily.com/releases/2026/11/20261120043200694.shtml
- https://neurotrans.net/levent-alpo-ge-claude-riemann-hypothesis-proof-lean-formalization/
- https://alpo.ge/remark.pdf
- https://openrouter.ai/blog/announcements/data-processing-incidents-on-inference-providers/
- https://www.together.ai/blog/security-event-prompt-leakage-for-requests-in-june-and-july-of-2026
- https://www.dragos.com/blog/three-breaches-endless-leaks-your-ai-supply-chain-needs-canaries/
- https://thecybersecguru.com/openrouter-minimax-zdr-incident-canary-urls-2026/
- https://explainx.ai/blog/together-ai-prompt-leak-xorl-huggingface-coding-agent-november-2026
- https://doj.oregon.gov/Media/NewsReleases/2026/11/OpenAI-ChatGPT-teen-safety-suit
- https://opencase.laws/oregon/oregon-state-circuit-court-civil/2026-011-089237
- https://opb.org/article/oregon-openai-chatgpt-teen-safety-lawsuit-2-billion
- https://www.reuters.com/business/autos-transportation/us-tightens-ai-chip-export-rules-data-center-compute-china-2026-11-16/
- https://techcrunch.com/2026/11/16/us-ai-chip-export-controls-cloud-compute-china/
- https://www.npr.org/2026/11/17/us-ai-chip-export-rules-china-data-centers/
- https://www.aljazeera.com/economy/2026/11/20/us-ai-chip-export-controls-china-trump-asia

### Security
- https://aws.amazon.com/blogs/aws/amazon-threat-intelligence-monai-label-campaign/
- https://www.theregister.com/2026/11/20/monai_label_zero_day_cairn/
- https://github.com/Project-MONAI/MONAI-Label/releases/tag/v0.8.6
- https://www.cisa.gov/known-exploited-vulnerabilities-catalog
- https://ir.zscaler.com/node/16796/pdf

### New use cases
- https://www.perplexity.ai/hub/blog/introducing-perplexitys-monitor-api
- https://docs.perplexity.ai/docs/monitors/overview
- https://the-decoder.com/perplexitys-new-monitor-api-turns-web-search-from-a-one-off-query-into-a-nonstop-watchdog/
- https://www.theverge.com/security/2026/11/16/google-ai-agent-security-vulnerability-patch
- https://op.berkeley.edu/news/uc-system-wide-openai-deal
- https://www.latimes.com/california/story/2026-11-21/uc-chatgpt-10-campuses-faculty-pushback
- https://github.com/leanprover-community/riemann-hypothesis
- https://github.com/CocoSgt/riemann-hypothesis-lean

### GitHub repos
- https://github.com/iamajmeena/neonclipping
- https://github.com/EL4CTEO/fast-anything
- https://github.com/boringmarketer/boring-marketing-skills
- https://github.com/pierridotite/mobile-agent-testers
- https://github.com/INK-Q/agy-fast
- https://github.com/danielwh2/sprite-stacking

### Also notable
- https://cnbc.com/2026/11/20/anthropic-stock-ai-amd-nvidia.html
- https://forbes.com/sites/fionariley/2026/11/20/anthropic-slumps-11-on-second-day-of-trading-after-record-breaking-ipo/
- https://www.businessinsider.com/anthropic-stock-is-back-to-earth-with-a-bump-dropping-close-to-its-ipo-price

---

## Compilation Note

Compiled Sunday, November 22, 2026 (09:10–11:30 PT, America/Los_Angeles) by the ai-research cron job. Research pass covered Nov 20–22, 2026 via live web search across Reuters, TechCrunch, BBC, The Verge, Scientific American, NYT, CNBC/Forbes, The Register, BleepingComputer, AWS Threat Intelligence, CISA KEV, vendor disclosures (OpenAI, OpenRouter, Together AI, Anthropic/claude.com, Zscaler, Perplexity, Oregon DOJ, UCOP), and GitHub API (repo star counts verified live). All five anchors are new relative to the November 21 edition, which led with GPT-6.2 Astra/Sol, the Anthropic IPO, Claude Fable 5.2/Mythos 5.2, Gemini 4 Neon, and the Microsoft MAI family. The Riemann Hypothesis story and the Pachocki perplexity disclosure are the week's defining developments: one is the first machine-verified frontier-math result, the other the first time a frontier lab has published its internal capability metric and proposed industry speed limits. Figures are as reported by the cited outlets and are not independently verified.
