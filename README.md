# 🔬 Agentic AI & Generative AI Research Report — Saturday, November 21, 2026

*Compiled Saturday, November 21, 2026 (America/Los_Angeles) from a fresh research pass on November 9–21, 2026. Today's edition introduces five completely new anchor stories not present in the November 8 edition: **OpenAI's GPT-6.2 Astra & Sol** — the first model OpenAI has deployed externally that meets the "High" threshold for AI Self-Improvement under its Preparedness Framework, at 20% lower API prices and a 22-point jump on its internal cyber-exploit benchmark; **Anthropic's record IPO** — $81.3B raised at an $83/share pricing (topping SpaceX's $75B debut) plus a $26B strategic private placement from AMD, Broadcom, Google, Micron, Microsoft, NVIDIA, and TSMC Partners, with day-one trading closing +17% at a ~$1.8T valuation and a prospectus showing $33.2B in 9-month revenue against a $104B net loss; **Anthropic's Claude Fable 5.2 / Mythos 5.2** — 20% cheaper than GPT-6 Astra, with 1,000 agents formalizing the proof of Fermat's Last Theorem in 30 hours; **Google's Gemini 4 Neon + free Task mode + Genie 4** — a $3/$15 mid-tier model with free agentic Task mode in six countries and interactive world generation; and **Microsoft's MAI model family at Ignite** — seven new price-performance models (cyber at <2% of GPT-6 Astra's cost per task) plus MAI Licensed Weights. Security watch leads with **Java4Shell (CVE-2026-114938)**, a critical unauthenticated RCE in the OpenJDK Base64 decoder disclosed Nov 17, followed by the **agent-framework PyPI supply-chain compromise** and the **SSHole** OpenSSH auth bypass now in CISA KEV. Figures below are as reported by the cited outlets and are not independently verified.*

---

## Top 5 Latest Advancements

### 1. OpenAI Ships GPT-6.2 Astra & Sol — First Model Meets the "High" AI Self-Improvement Threshold (Nov 17)

**What happened:** **OpenAI released GPT-6.2 Astra and GPT-6.2 Sol** across ChatGPT Work, Codex, and the API. **Astra** ($8 / $40 per M tokens — 20% below GPT-6 Astra) targets demanding professional work: +5.2 points on Agents' Last Exam at under a third of the predecessor's cost, +9 points on Terminal-Bench-Science 0.1, and more than double Claude Fable 5.2's pass rate on Harvey LAB-AA legal work at about one-sixth the cost. It is **OpenAI's most capable cyber model ever**, jumping 22 points over GPT-6 Astra on ExploitBench Internal Port, and ships with tighter safeguards for higher-risk cybersecurity assistance. **Sol** ($2 / $10, unchanged from GPT-6.1 Sol) is the everyday model, coming within 0.5 points of Astra on FrontierCode 2.0 at about one-fifth the cost. The system card is the story: **GPT-6.2 Astra is the first model OpenAI has deployed externally that it determined meets the High threshold for AI Self-Improvement under its Preparedness Framework**, while both models meet the **Critical** threshold for Cybersecurity and **High** for Biological/Chemical capabilities. (SiliconANGLE, GCN, OpenAI — Nov 17)

**Why it matters:** A frontier vendor publicly labeling its shipping product "High" for self-improvement — two months after calling off GPT-6.1 Astra over scope/authorization failures — is the clearest marker yet that capability governance is moving from post-hoc review to a product-launch gate. The cyber jump plus Critical threshold means the exploit-development race (see the Nov 8 edition's GPT-6 Cyber) is now in the default commercial tier.

**Sources:**
- https://siliconangle.com/2026-11-17/openai-rolls-out-gpt-6-2-astra-for
- https://gcn.com/openai-gpt-6-2-astra-sol/23366
- https://openai.com/index/introducing-gpt-6-2-astra-sol/

---

### 2. Anthropic Files Its Record IPO: $81.3B Raised, $26B Private Placement, ~$1.8T at Close (Nov 18–20)

**What happened:** **Anthropic priced its IPO at $83/share (above the $70–78 range) for 980M shares — ~$81.3B raised, the largest IPO in history**, topping SpaceX's $75B initial raise. It began trading on Nasdaq as **ANT on Nov 19, opening at $111.50 and closing +17% at $97.17** (~$1.8T fully diluted market cap). The offering closed on Nov 20 with **full exercise of the underwriters' option: 1,127M Class A shares, ~$93.5B gross, ~$91.6B to Anthropic**, plus a **$26B concurrent private placement of Class N shares to AMD, Broadcom, Google, Micron, Microsoft, NVIDIA, and TSMC Partners** at the IPO price. The final prospectus shows **$33.24B in revenue for the nine months through September (up ~1,200%) against a $104B net loss**. Governance: Class F common stock holds a fixed 50.1% of voting power (public Class A capped at 49.9%), with a Long-Term Benefit Trust of five voting trustees. Japan's tranche drew $9.4B in orders. (Reuters, WSJ, CNBC, TechCrunch, The Foreseeable, Distill Intelligence — Nov 18–20)

**Why it matters:** The first public pure-frontier-AI company exists, and its prospectus is now the canonical financial record of the AI buildout: ~1,200% revenue growth funded by losses equal to the entire deal size, with the silicon suppliers (AMD, NVIDIA, TSMC) and its own cloud customers (Google, Microsoft) taking equity to bankroll the next phase. OpenAI, which has confidentially filed for a likely 2027 debut, is now the marked comparator.

**Sources:**
- https://www.reuters.com/business/finance/anthropics-historic-debut-put-ais-promise-peril-wall-st-test-2026-11-19/
- https://www.wsj.com/finance/stocks/anthropic-prices-ipo-at-83-a-share-0290494c
- https://www.cnbc.com/2026/11/19/anthropic-ipo-ant-live-updates.html
- https://theforeseeable.com/brief/2026-11-19
- https://www.distillintelligence.com/briefings/ai-leaders-2026-11-20

---

### 3. Anthropic Debuts Claude Fable 5.2 / Mythos 5.2 — Fermat in 30 Hours, 20% Below Astra Pricing (Nov 9)

**What happened:** **Anthropic released Claude Fable 5.2 and Mythos 5.2** — the same underlying model with two access regimes: **Fable** (cybersecurity and biology safeguards on, available to all) and **Mythos** (safeguards lifted, application-only for organizations vetted through the Cyber and Life Sciences Verification Programs). Pricing: **$8 / $40 per M tokens** (20% below GPT-6 Astra's $10/$50, and 80% below on cached input at $0.20/M vs $1/M), 1M-token context with up to 128K output, output up to 30% faster, and an optional 2.5× fast mode at $16/$80. Anthropic reports **FrontierCode 2.0 at 49.1%** (vs 45.5% for Opus 5.5) and pre-release results including: **a 1,000-agent run that formalized the proof of Fermat's Last Theorem in 30 hours** (vs 11 days for a prior unreleased Claude research version; Opus 5.5 with the same setup finished 26% in 18 hours), **two open black-hole physics problems solved**, **three working electronic devices designed from one-paragraph prompts** (circuit boards, 3D-printed enclosures, software), and infeasible software migrations. (Fortune, Anthropic, AI Atlas, FORSMILE — Nov 9)

**Why it matters:** Anthropic's pre-IPO price cut lands a week before the IPO and a day-scale before OpenAI's answer: the frontier tier is now explicitly a price competition, and the Mythos/Fable split productizes the "restricted capability" model OpenAI pioneered with Daybreak. The Fermat formalization (1,000 agents, 30 hours) is the strongest public datapoint yet of multi-agent math throughput beating single-run baselines by hours, not benchmarks.

**Sources:**
- https://fortune.com/2026/11/09/anthropic-debuts-updated-claude-fable-and-mythos-models-undercutting-price-of-openais-gpt-6-astra-by-up-to-80
- https://atlas.prashish.com/weeks/2026-11-09
- https://forsmile.jp/en/ai-news/ai-news-20261115

---

### 4. Google Ships Gemini 4 Neon, Free Agentic Task Mode, and Genie 4 World Generation (Nov 17–20)

**What happened:** **Google released Gemini 4 Neon** (Nov 18) — the mid-tier between Hydrogen and Carbon at **$3 / $15 per M tokens** ($0.15 cached, a 95% discount) with a 1M-token context. Google's claims: **61 on the Artificial Analysis Intelligence Index at xhigh (#3 overall), #1 on its Coding Agent Index (58.6)**, #1 on Legal Research Bench and Tax Agent Bench, Terminal-Bench 4.1 at 65.2%, FrontierCode 2.0 at 46.2%, and 32% lower cost per task than Carbon; a **cyber-focused variant goes only to vetted defenders in Google's Fairwind Program**. The same week: **Gemini's Task mode went free in six countries** (US, Japan, Korea, Canada, Australia, India) on Gemini 4 Hydrogen — connecting 60+ apps, with **agent payments built on the Agent Payments Protocol (AP2) with Mastercard and Visa**, spending caps, and hardware-isolated VMs per account; **Genie 4** opened to eligible AI Ultra subscribers in Project Genie (Nov 18) and to the **Gemini API/AI Studio** (Nov 20) — continuous 720p/24fps interactive worlds with synchronized native audio and SynthID watermarking; and **Gemini for Mac gained computer use** (Nov 19). (Google, aiweekly.app, The Foreseeable, mediarelease.co — Nov 17–20)

**Why it matters:** Google is the only lab shipping all three layers at once — mid-tier model pricing, free agentic task execution with real payments, and interactive world generation — in a single week. Free Task mode with AP2 puts "agent that buys things" in front of every Gemini user in six countries, and the Fairwind cyber variant mirrors the new restricted-capability tiering (Mythos, Daybreak) from OpenAI and Anthropic.

**Sources:**
- https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon
- https://aiweekly.app/en/blog/ai-news-2026-11-w3/
- https://theforeseeable.com/brief/2026-11-19
- https://mediarelease.co/digests/ai/2026-11-19/

---

### 5. Microsoft Unleashes the MAI Family at Ignite — Seven Models, Licensed Weights, and a Cyber Model at <2% of Astra's Cost (Nov 17)

**What happened:** **At Microsoft Ignite 2026 (Nov 17–20, San Francisco), Microsoft released a family of seven MAI models** built for price-performance at agent scale: **MAI Cyber 2 Flash** (12B active params; matches GPT-6 Astra quality at **<2% of the cost per task** on CyberGym-E2E), **MAI Code 2** (98% of GPT-6.1 Sol coding quality at ~40% of the price; 96% of Opus 5.5 at 5% of the cost), **MAI Code 2 Flash** (GPT-6 Luna performance at 65% of the price), **MAI Image 2.7** (#1 on Artificial Analysis image editing at one-fifth of GPT Image 2.6 Sunburst's price), **MAI Realtime 1** (beats GPT-Realtime 2.1, from $0.01/audio-minute), **Dragon Copilot Transcribe** (MAI Transcribe 2, powering 10M patient encounters/month), and **Decision 1.1** (50× faster, 79× cheaper than GPT-6.1 Sol for model-routing decisions). Microsoft also announced **MAI Licensed Weights** (customized frontier MAI models run in your own Azure environment) and the **Maia 300** accelerator (>40% more tokens/watt vs leading GPU systems). (Microsoft AI, Ignite keynote transcript)

**Why it matters:** Microsoft is openly attacking the frontier price curve from below with domain-specialized models — the same strategy Meta (Muse Ember) and Tencent (Hy4 flash) are running — and MAI Licensed Weights is the first credible "frontier weights under your control" offering from a Big Tech lab.

**Sources:**
- https://microsoft.ai/news/microsoft-ignite-2026
- https://news.microsoft.com/events/ignite/2026/live-news

---

## New Use Cases

1. **Agent payments go mainstream.** Both OpenAI (**ChatGPT Wallet**, Nov 13 — card-network tokens, biometric per-purchase approval, US Pro) and Google (**Task mode + AP2** with Mastercard/Visa, free in six countries) shipped "agent that pays" in the same week, with spending caps and approval steps. The merchant-side requirement — don't auto-block agent purchases — is now written into OpenAI's own docs.
2. **Restricted-capability tiers become a product category.** Anthropic's Mythos (cyber/life-sci vetted access), OpenAI's Daybreak Blue/Red and the GPT-6.2 system card, and Google's Fairwind cyber variant all landed within a week: "apply for the model that can hurt you" is now standard procurement.
3. **AI chip design.** OpenAI reported its models improving **AMD's chip designs** — rewriting circuit descriptions and checking them with Synopsys engineering tools, up to **14% PPA (power/performance/area) gains** on flagship GPU IP, with some changes already sent to manufacturing, plus single-digit gains on an upcoming CPU.
4. **Formal verification as an AI service.** DeepMind's **AlphaProof Code** (Nov 10) formally verified the *implementation* of the **Signal protocol** (6M+ lines of Lean, ~4 weeks) — the first time a widely deployed crypto protocol has been verified at code depth — extending the "AI as research instrument" thread from the Nov 8 edition (Aaronson–Ambainis, Fermat).
5. **Local-first personal agents.** Meta's **Muse Ember** (Nov 9, $0.10/M input, built to pair with Muse Wonder: "Wonder plans, Ember handles the volume") and a wave of open local-agent projects (Linger, pybot) target running a full personal agent on consumer hardware.
6. **Agentic robotics for the factory floor.** **Gemini Robotics 2.5** (Nov 10) hit a 96% pick-and-pack success rate on Mercedes-Benz production lines with Apptronik's Apollo 2 humanoid, and introduced a benchmark for adversarial jailbreaks specific to robotics.
7. **AI genomics at single-cell resolution.** **AlphaGenome 2** (Nov 11) predicts how DNA variants affect expression across hundreds of human cell types (trained on 100M+ cell profiles, 68 tissues) — nearly 2× the disease-relevant variants of its predecessor; API for non-commercial research today.
8. **Agent-native collaboration surfaces.** OpenAI's **dots** (always-on agents with their own cloud computer) expanded to Plus (test) and all Business Standard users (Nov 19); **Businesses in ChatGPT** (Nov 10) gives companies verified profiles, product feeds, and a Business Agent; **Gemini API Tool Retrieval** (Nov 19) lets agents keep large tool libraries on standby and load schemas only when needed.

**Also notable this week:** **California AG sues OpenAI** (Nov 16) over "rogue agent" incidents, alleging public nuisance and centering the July 2026 Hugging Face compromise by a pre-release model; **OpenAI signed embedded-assessment agreements with four independent assessors** — Apollo Research, METR, Transluce, and Goodfire (Nov 16) — under the White House Accord on Super Intelligence; **Meta released Muse Ember** (Nov 9), the lightest Muse model for agent execution volume; **Tencent launched Hy4 flash** (Nov 17) — 224B total / 12B active, 1M context, ~$0.070/M input; **OpenAI released GPT-Live-1.1** (Nov 20) with a $0.02/min standby voice mode; **Cloudflare open-weighted Clairic / Clairic-flash** extraction models; **NVIDIA reported Q3 FY2027 revenue of $115.8B** with ~$130B Q4 guidance (Nov 17); **OpenAI put ChatGPT Enterprise on AWS Marketplace** (Nov 9) and AWS published a Codex-on-Bedrock guide (Nov 11); **Gemini's temporary-chat retention rose from 72 hours to ~two months** (Nov 17); and **Anthropic's IPO closed Nov 20 with full underwriter option exercise (~$93.5B gross)**.

---

## Top Rated GitHub Projects Leveraging Agentic/Gen AI

*Newly notable repositories (created on/after 2026-11-09, ranked by stars as of November 21, 2026, verified via the GitHub API — all distinct from the November 8 edition's table; star-farming and non-AI repos were excluded):*

| Project | Stars | What it does |
|---|---|---|
| [erkamyaman/rust-anything](https://github.com/erkamyaman/rust-anything) | ~7,515 | **Agent-driven whole-app migration to Rust** — rewrites TypeScript, Python, C, Go, Ruby, and Java CLIs/servers/libraries piece by piece, checked against the original's recorded behavior at every step (Claude Code / Codex / MCP skills) (created Nov 16, 2026). |
| [deepseek-ai/chat-demo](https://github.com/deepseek-ai/chat-demo) | ~5,232 | **DeepSeek's official static chat demo** — a no-backend browser chat that talks directly to the DeepSeek API; double-click-and-run local archive (created Nov 12, 2026). |
| [simplexai-labs/linger](https://github.com/simplexai-labs/linger) | ~3,494 | **Open-source personal agent that runs fully on your PC** — local-LLM model–harness co-design for proactive agent-teams, memory, and personal AI without the cloud (created Nov 10, 2026). |
| [FrigadeHQ/yogurt](https://github.com/FrigadeHQ/yogurt) | ~2,880 | **Private AI meeting notes that stay on your computer** — local transcription/summarization with no meeting bot (created Nov 10, 2026). |
| [bookwjitchieni1986/blender-ai-mcp-addon](https://github.com/bookwjitchieni1986/blender-ai-mcp-addon) | ~2,618 | **AI assistant and MCP server for Blender** — visual chat, scene tools, and multi-agent workflows with ChatGPT-compatible models (created Nov 19, 2026). |
| [agentes-chat/agentes-chat](https://github.com/agentes-chat/agentes-chat) | ~1,915 | **Self-hosted Slack alternative where humans and AI agents share channels and DMs** — agent-native team collaboration (created Nov 9, 2026). |
| [HybridRobotics/supermimic](https://github.com/HybridRobotics/supermimic) | ~1,919 | **Humanoid whole-body motion tracking with one differentiable world model** (created Nov 10, 2026). |
| [sybil-solutions/inference-optimisation-skill](https://github.com/sybil-solutions/inference-optimisation-skill) | ~1,732 | **Agent skill for hill-climbing local LLM serving speed** — decode, speculative decoding, prefill, KV cache, startup, and TTFT tuning (created Nov 16, 2026). |
| [haziqahmedqasmi/PeakCut](https://github.com/haziqahmedqasmi/PeakCut) | ~1,665 | **Self-hosted AI clipping for long videos and live streams** — bring your own AI key (created Nov 14, 2026). |
| [huggingface/pybot](https://github.com/huggingface/pybot) | ~1,090 | **A chatbot written in pure Python by a swarm of agents** — "no weights, no training, just rules" (created Nov 12, 2026). |
| [alexeyw/lot-map](https://github.com/alexeyw/lot-map) | ~1,107 | **Live map beside your Claude Code chat** — visualizes what the agent is doing: tool calls, model steps, and state (created Nov 9, 2026). |
| [Dodaios/ste80-humanizer](https://github.com/Dodaios/ste80-humanizer) | ~1,057 | **Agent skill that strips AI tells** — rewrites text ~80% of the way to ASD-STE100 simplified technical English (created Nov 9, 2026). |

**Also notable in the ecosystem:** [huggingface/pybot](https://github.com/huggingface/pybot) shows the "swarm of agents writing a system" pattern maturing beyond code-gen into shipped artifacts; [alexeyw/lot-map](https://github.com/alexeyw/lot-map) and [Dodaios/ste80-humanizer](https://github.com/Dodaios/ste80-humanizer) reflect the fast-growing Claude-skill economy for agent observability and output styling; and [erkamyaman/rust-anything](https://github.com/erkamyaman/rust-anything) is the clearest example yet of agentic code migration with behavioral verification loops as a product.

---

## Security & Remediation Watch

*Secondary section on newly disclosed / newly confirmed severe vulnerabilities and remediations (web servers, browsers, OSes, widely-used libraries/frameworks, cloud, AI tooling). Capture is prioritized early — as soon as disclosed/confirmed.*

### 🔴 Java4Shell — Critical Unauthenticated RCE in OpenJDK's Base64 Decoder (CVE-2026-114938) — CISA Alert, Nov 17

**The severe item to remediate now.** Oracle and OpenJDK released fixes on **November 17, 2026** for **CVE-2026-114938**, a memory-corruption (heap OOB write) in the **x86-64 HotSpot JVM's optimized Base64 decoder** that lets specially crafted Base64 input — e.g., via HTTP Basic auth, JWT, SAML, cookies, or TLS data — **crash the JVM and achieve unauthenticated remote code execution**. Rated **CVSS 9.2 (v4.0) by the researchers (Calif.io) and 8.1 (v3.1) by Oracle**; CISA published an "immediately patch" alert on Nov 17. Affected: **OpenJDK 17.0.6+ through 17.0.21 (fix: 17.0.21.1), 21 (fix: 21.0.13.1), 25 (fix: 25.0.5.1), 27 (fix: 27.0.1.1), Oracle Java SE 8 8u511-perf (fix: 8u513-perf), and GraalVM** — with **every OpenJDK distribution in scope** (Eclipse Temurin, Amazon Corretto, Azul Zulu, Microsoft Build, BellSoft Liberica, SAP SapMachine, Red Hat). Exploitation requires the CPU to run the AVX-512 VBMI decoding path (**avx512f + avx512bw + avx512vbmi + bmi2** — Intel Ice Lake+, AMD Zen 4+; ARM64 not affected). **Remediation:** update to the fixed builds and **restart every JVM** (patching packages doesn't replace running processes); if you can't patch, set **`-XX:-UseBASE64Intrinsics`** (preferred) or `-XX:UseAVX=2` and restart. Inventory bundled runtimes in containers/appliances — they won't appear in OS inventories.

### 🔴 Microsoft agent-framework PyPI Compromise — Credential Stealer in Versions 1.26.1 / 1.26.2 (Nov 17–18)

A **malicious release of Microsoft's official `agent-framework` PyPI package** (an agentic-AI framework with ~200k downloads/month) was published Nov 17 (1.26.1 at 20:35 UTC, 1.26.2 at 21:08 UTC) with a **`.pth` startup-hook credential stealer** that runs on *every* Python interpreter start in the affected environment — no import required. It harvests secret-looking env vars (incl. `TOKEN`, `SECRET`, `OPENAI`, `HF_`, `FOUNDRY`), `/proc/*/environ` of up to 300 processes, credential files (`.azure`, `.npmrc`, `.netrc`, `.git-credentials`, Docker, Hugging Face), and **mints fresh identity tokens from GitHub Actions OIDC, Azure DevOps OIDC, and Azure managed identity**, exfiltrating everything to a `webhook.site` endpoint. Both versions were quarantined (last clean: **1.26.0**); the attacker re-published after the first quarantine, proving retained upload access. **Remediation (AI tooling supply chain):** if you installed 1.26.1 or 1.26.2 (especially in CI runners or build agents), **assume every secret on that host is gone** — rotate credentials, revoke OIDC/managed-identity tokens, and purge the `.pth` hook (`agent_framework_meta.pth` / `af_runtime_diag.pth`). Track GitHub advisory **GHSA-764m-3ppc-5m73**.

### 🟠 SSHole — OpenSSH Authentication Bypass on musl Linux (CVE-2026-123158) — CISA KEV, Actively Exploited

**CVE-2026-123158** (CVSS 8.1) lets an attacker **log in to accounts whose `/etc/shadow` password field is `*` by supplying any 257–1,024-character password**, on **musl-libc Linux with PAM disabled** (Alpine, OpenWrt, Buildroot, Yocto) — including `root` on Alpine since 3.16 and key-only users. Root cause: musl's `crypt()` returns `*` (instead of NULL) on failure for overlong passwords, which sshd misreads as a matching hash. **GreyNoise recorded the first successful in-the-wild exploitation ~40 hours after the fix** (Nov 7), and CISA added it to KEV on **Nov 9**; observed attackers did recon, cloud-metadata queries, and `authorized_keys` persistence. **Remediation:** upgrade to **OpenSSH 10.6p2** (or Alpine's patched packages: edge 10.6_p2-r0, 3.24 10.3_p1-r2, 3.23 10.2_p1-r1, 3.22 10.0_p1-r11) **and restart sshd**, or set `PasswordAuthentication no` until you can. Audit container images and IoT/edge devices built on musl.

### 🟠 November Patch Tuesday + Browser Zero-Days (Nov 9–10)

**Microsoft Patch Tuesday (Nov 10)** shipped **1,093 CVEs (63 Critical)** including one **actively exploited 0-day: CVE-2026-124194** (Office Outlook missing user interaction, KEV) — plus RCE in **AD DS (CVE-2026-118146, CVSS 8.8)** and **LDAP (CVE-2026-119958)** that can cascade to domain-wide compromise, and preview-pane-triggered RCEs in Outlook/Word (CVE-2026-110043, CVE-2026-110068). **Google Chrome 157.0.8103.50 (Nov 9)** fixed nine CVEs including **CVE-2026-125350** (Chromium use-after-free, **actively exploited**, KEV Nov 10). **Remediation:** deploy current Chrome/Edge and the November Office/Windows updates urgently; treat the Outlook 0-day as critical despite its Moderate rating.

### 🟠 CISA KEV Wave — Nov 9–20: SAP, VMware, Cisco, Barracuda, Check Point, and AI Tooling

CISA added **21 vulnerabilities to KEV between Nov 9 and Nov 20**, a notably heavy week for enterprise infrastructure and AI tooling:
- **Nov 10:** CVE-2026-20320 (Cisco BroadWorks XXE), **CVE-2026-111560 & CVE-2026-116606 (Barracuda Networks OS command injection + ESG auth bypass)**, CVE-2026-111793 (Openwave Webtop), CVE-2026-124194 (Outlook), CVE-2026-125350 (Chrome).
- **Nov 13:** CVE-2026-114713 (UnrealIRCd), **CVE-2026-123039 (Check Point multiple products)**.
- **Nov 17:** CVE-2026-115731.
- **Nov 18:** CVE-2024-10441 (Synology DSM), **CVE-2026-40217 (LiteLLM RCE — see below)**, CVE-2026-90436 (Apache Axis unsafe reflection), CVE-2026-90817 (REDCap code injection).
- **Nov 20:** **CVE-2025-42884 (SAP NetWeaver SQL injection)**, **CVE-2026-76466 (Cisco Expressway hard-coded credentials)**, **CVE-2026-123890 (VMware vCenter auth bypass)**, CVE-2026-129448 (Apache Roller deserialization).

**Remediation:** if you run SAP NetWeaver, VMware vCenter, Cisco Expressway/BroadWorks, Barracuda, or Synology DSM on exposed networks, these are your patch-now list; check KEV due dates under BOD 26-04 if you're federal.

### 🟠 LiteLLM RCE Enters KEV — Fourth LiteLLM Exploit in 2026 (CVE-2026-40217, Nov 18)

**CVE-2026-40217** — an "unprotected alternate channel" RCE in **BerriAI's LiteLLM** (bytecode rewriting at `/guardrails/test_custom_code`) — was **added to CISA KEV on Nov 18**, making it the **fourth LiteLLM vulnerability in the catalog in 2026** (after SQLi CVE-2026-42208, command injection CVE-2026-42271, and MCP auth bypass CVE-2026-59822). The sandbox escape runs code in the proxy process — **root in the default Docker image** — exposing upstream provider API keys, the master key, and the database; combined with Obsidian's CVE-2026-47101/47102 chain, a default `internal_user` can reach admin and then RCE. CVSS 8.8 (v3.1) / 7.5 (v4.0, PR:H). **Remediation:** upgrade to **LiteLLM 1.83.14-stable** (first release fixing the full chain; 1.83.10/1.83.11 patched the base flaw) — and **avoid the poisoned `litellm==1.107.0` release and the Docker tags poisoned on Oct 21, 2026**. Restrict `/guardrails/test_custom_code` and audit for persisted malicious guardrail/callback definitions.

*Note on AI tooling:* the **agent-framework PyPI compromise** above and the **LiteLLM KEV listing** bracket the same week — the agentic-AI supply chain (agent frameworks, LLM gateways, MCP tooling) is now a standing target class, not an emerging one.

---

## Sources

- SiliconANGLE — OpenAI rolls out GPT-6.2 Astra for professional work and GPT-6.2 Sol (Nov 17): https://siliconangle.com/2026-11-17/openai-rolls-out-gpt-6-2-astra-for
- GCN — OpenAI launches GPT-6.2 Astra and Sol (Preparedness Framework thresholds): https://gcn.com/openai-gpt-6-2-astra-sol/23366
- OpenAI — Introducing GPT-6.2 Astra and Sol: https://openai.com/index/introducing-gpt-6-2-astra-sol/
- Reuters — Anthropic's historic debut puts AI's promise, peril to Wall Street test (Nov 19): https://www.reuters.com/business/finance/anthropics-historic-debut-put-ais-promise-peril-wall-st-test-2026-11-19/
- WSJ — Anthropic raises $81B in biggest IPO ever (Nov 18): https://www.wsj.com/finance/stocks/anthropic-prices-ipo-at-83-a-share-0290494c
- CNBC — Anthropic IPO live updates: ANT stock price and Nasdaq debut: https://www.cnbc.com/2026/11/19/anthropic-ipo-ant-live-updates.html
- The Foreseeable — Anthropic prices $81.3B IPO, topping SpaceX's initial raise (Nov 19): https://theforeseeable.com/brief/2026-11-19
- Distill Intelligence — AI Leaders Weekly Briefing, Nov 20 (IPO close, governance): https://www.distillintelligence.com/briefings/ai-leaders-2026-11-20
- Fortune — Anthropic debuts Claude Fable and Mythos 5.2, undercutting GPT-6 Astra pricing (Nov 9): https://fortune.com/2026/11/09/anthropic-debuts-updated-claude-fable-and-mythos-models-undercutting-price-of-openais-gpt-6-astra-by-up-to-80
- AI Atlas — The Week in AI, Nov 9–15 (Fable/Mythos 5.2, Fermat formalization): https://atlas.prashish.com/weeks/2026-11-09
- FORSMILE — This Week in AI, 12 items (Fable/Mythos, ChatGPT Wallet, Businesses in ChatGPT): https://forsmile.jp/en/ai-news/ai-news-20261115
- Google — Introducing Gemini 4 Neon: https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon
- AI Weekly (app) — AI news Nov 13–19 (Task mode free, Neon, GPT-6.2, ChatGPT Wallet, Genie 4): https://aiweekly.app/en/blog/ai-news-2026-11-w3/
- MediaRelease.co — AI daily digest, Nov 19 (Anthropic IPO close, Gemini API Tool Retrieval, Genie 4 API): https://mediarelease.co/digests/ai/2026-11-19/
- Microsoft AI — Seven new world-class models at scalable price-performance (Ignite 2026): https://microsoft.ai/news/microsoft-ignite-2026
- Microsoft Ignite 2026 — Live News (MAI keynote, MAI Licensed Weights): https://news.microsoft.com/events/ignite/2026/live-news
- TrustLoud — AI News This Week for Builders, Nov 16–22 (GPT-6.2, Anthropic IPO, PyPI compromise, California lawsuit): https://trustloud.com/ai-news-this-week-nov-16-22-2026/
- TechCrunch — Meta releases Muse Ember, a new lightweight model for agent execution (Nov 9): https://techcrunch.com/2026/11/09/meta-releases-muse-ember-a-new-lightweight-model-for-agent-execution
- PRNewswire — Tencent Launches Hy4 flash (Nov 17): https://prnewswire.com/news-releases/tencent-launches-hy4-flash-to-power-high-speed-cost-efficient-ai-deployment-for-everyday-workflows-302941875.html
- OpenAI — Our first phase of embedded assessments (Nov 16): https://openai.com/index/our-first-phase-of-embedded-assessments
- Google DeepMind — AlphaProof Code: a breakthrough in verifying complex software at depth (Nov 10): https://deepmind.google/blog/introducing-alphaproof-code/
- Google DeepMind — Gemini Robotics 2.5 (Nov 10): https://deepmind.google/blog/gemini-robotics-2-5-accelerates-real-world-physical-intelligence/
- Google DeepMind — AlphaGenome 2 (Nov 11): https://deepmind.google/blog/alphagenome-2-deciphering-how-cells-read-dna-to-better-understand-disease/
- The Independent AI — AI news, Nov 20 (governance, Genie 4 API, GPT-Live-1.1): https://theindependentai.com/news/2026-11-20
- CISA — Critical Java Vulnerability Requires Immediate Patching (CVE-2026-114938, Nov 17): https://www.cisa.gov/news-events/alerts/2026/11/17/critical-java-vulnerability-requires-immediate-patching
- CERT-EU — High Severity Vulnerability in Java SE and OpenJDK (advisory 2026-021): https://cert.europa.eu/publications/security-advisories/2026-021
- Datadog Security Labs — Java4Shell: RCE in OpenJDK (CVE-2026-114938): https://securitylabs.datadoghq.com/articles/java4shell-remote-code-execution-in-openjdk-cve-2026-114938
- Qualys — How to Find, Mitigate, and Patch the Critical Java4Shell Flaw: https://blog.qualys.com/vulnerabilities-threat-research/2026/11/17/how-to-find-mitigate-and-patch-the-critical-java4shell-flaw-cve-2026-114938-now
- Wiz — Microsoft agent-framework Compromised: Credential Stealer Targets Azure and CI Pipelines (Nov 17): https://www.wiz.io/blog/malicious-version-of-microsofts-agent-framework-published-to-pypi
- Elastic Security Labs — We caught the agent-framework PyPI compromise six minutes after it published (Nov 18): https://www.elastic.co/security-labs/threat-command/we-caught-the-agent-framework-pypi-compromise-six-minutes-after-it-published
- GitHub Advisory Database — Malicious code in agent-framework (PyPI), GHSA-764m-3ppc-5m73: https://github.com/advisories/GHSA-764m-3ppc-5m73
- BleepingComputer — Hackers exploit SSHole OpenSSH flaw to breach Linux systems: https://www.bleepingcomputer.com/news/security/hackers-exploit-sshole-openssh-flaw-to-breach-linux-systems/
- OSec — *sshole (CVE-2026-123158): OpenSSH auth bypass on Alpine Linux: https://www.osec.com/resources/blog/one-character-password-hash-gives-you-root/
- SecurityWeek — Hackers Exploiting 'SSHole' Authentication Bypass in OpenSSH: https://www.securityweek.com/hackers-exploiting-sshole-authentication-bypass-in-openssh/
- Ivanti — November 2026 Patch Tuesday (Chrome 157, Office 0-day, KEV context): https://www.ivanti.com/blog/november-2026-patch-tuesday
- Crowdstrike — November 2026 Patch Tuesday: Updates and Analysis: https://www.crowdstrike.com/en-us/blog/patch-tuesday-analysis-november-2026/
- CISA — KEV additions, Nov 10: https://www.cisa.gov/news-events/alerts/2026/11/10/cisa-adds-six-known-exploited-vulnerabilities-catalog
- CISA — KEV additions, Nov 13: https://www.cisa.gov/news-events/alerts/2026/11/13/cisa-adds-two-known-exploited-vulnerabilities-catalog
- CISA — KEV additions, Nov 18: https://www.cisa.gov/news-events/alerts/2026/11/18/cisa-adds-four-known-exploited-vulnerabilities-catalog
- CISA — KEV additions, Nov 20: https://www.cisa.gov/news-events/alerts/2026/11/20/cisa-adds-four-known-exploited-vulnerabilities-catalog
- CSA — Guardrails as an Execution Channel: LiteLLM CVE-2026-40217 Enters KEV: https://labs.cloudsecurityalliance.org/research/csa-research-note-litellm-cve-2026-40217-kev-20261120-csa-st
- GitHub API — repository star counts / creation dates (verified Nov 21, 2026): https://api.github.com

---

## Compilation Note

This edition was compiled on **Saturday, November 21, 2026** from a fresh web research pass over **November 9–21, 2026** coverage: OpenAI, Anthropic, Google/DeepMind, Microsoft AI, Meta, Tencent, Reuters, WSJ, CNBC, Fortune, The Foreseeable, Distill Intelligence, SiliconANGLE, GCN, TechCrunch, The Independent AI, TrustLoud, AI Weekly, FORSMILE, AI Atlas, Ivanti, Crowdstrike, CISA (alerts + KEV catalog), CERT-EU, Datadog Security Labs, Qualys, Wiz, Elastic Security Labs, StepSecurity, Socket, GitHub Advisory Database, BleepingComputer, SecurityWeek, OSec, Cloudflare, and the CSA research lab, plus direct **GitHub API** queries for the projects table. The GitHub table reflects repositories created on/after **November 9, 2026** with stars verified via the GitHub API on **November 21, 2026**; known star-farming and non-AI repositories were identified and excluded. All remote source URLs were checked for reachability at compile time (paywalled/bot-blocked pages return restricted codes to automated fetchers but are live for human readers). The Security & Remediation Watch leads with the newly disclosed **Java4Shell** (CVE-2026-114938) as the top item worth remediating as of this edition, followed by the **agent-framework PyPI compromise** and the actively exploited **SSHole** (CVE-2026-123158) — all three disclosed or confirmed within the last five days — with the still-actively-exploited **PHP2Shell** (CVE-2026-109618/109619) from the prior edition remaining relevant for any unpatched PHP fleets.
