# 🔬 Agentic AI & Generative AI Research Report — Monday, November 23, 2026

*Compiled Monday, November 23, 2026 (America/Los_Angeles) from a fresh research pass on November 22–23, 2026. Today's edition introduces five completely new anchor stories not present in the November 22 edition: **Z.ai's GLM-5.4 "Loop Transformer"** — a 750-billion-parameter flagship that runs 28 shared layers twice to match 2–3T-parameter models, the first big-lab deployment of the looped-architecture line OpenAI has used since GPT-6 Astra; **NVIDIA's board reinstating Jensen Huang** as president, CEO, and board director (unanimous, effective immediately, +30% stock pop) after a 10-day interim period, with the foreign-intelligence investigation and a new National Security & Export Control Oversight Committee still running; **the Riemann Hypothesis proof clearing its first major verification gate** — the Lean and Mathlib communities formally certified the statement and proof correct on Nov 21, and MIT's Sutherland ledger shows a byte-identical sandbox rebuild plus a zeta-free Robin/Lagarias cross-check passing, while Stanford's all-human Masullo draft sits in parallel; **Anthropic's Claude Code "one agent beats many subagents"** guidance and the claim that Claude now writes over 90% of Anthropic's own code; and **METR's Q4 capability warning** that AI systems are improving faster than experts can reliably evaluate their safety. Security watch leads with **CVE-2026-133968 (MONAI Label)** — the AI-agent-driven in-the-wild exploitation now confirmed patched — and a fresh **CISA KEV batch** added Nov 21. Figures below are as reported by the cited outlets and are not independently verified.*

---

## Top 5 Latest Advancements

### 1. Z.ai Ships GLM-5.4, a 750B "Loop Transformer" Flagship That Matches 2–3T Models (Nov 23)

**What happened:** Z.ai (Zhipu) launched **GLM-5.4** on Nov 23, its first flagship built on a **Loop Transformer** architecture. Rather than adding parameters, the model **runs a block of 28 shared layers (layers 27–54) twice**, retraining the GLM-5 base (released in February) so each pass refines the previous pass's intermediate results — making the network effectively deeper without new weights. According to Z.ai, the **750B-parameter** model reaches performance comparable to **2–3 trillion-parameter** models, deliberately targeting the tier of **Kimi K3.1 Pro (2.8T)** and **Qwen3.8-Max (2.4T)**. To keep the second pass stable, GLM-5.4 uses **dedicated per-token, per-pass gates** that control how much of the new output flows back (the first pass builds context cautiously, the second writes changes back in full, and the first pass intervenes more strongly on difficult tokens). Both passes **share the KV cache**, with the second pass storing only a small local window of extra values, so overhead stays manageable even at a **1-million-token context**. Sparse attention picks the most relevant tokens up front, and the second pass reuses that selection. Z.ai reports **up to 200 tokens/sec off-peak and 70–80 tokens/sec under load**. Because no 750B benchmark has been published, the evidence rests on a same-parameter **30B loop test model** (~10% more training compute than its baseline): **AIME25 19.2 → 30.4, GPQA-Diamond 47.6 → 56.3, AA-LCR 40.3 → 47.7**, with ~3-point gains on MMLU-Pro and IFBench and **shorter responses** (−14.9% MMLU-Pro, −11.7% GPQA-Diamond, −2% AIME25). Z.ai frames GLM-5.4 as the start of **"Generalized Coding"** — code as the substrate for video, games, FreeCAD robot-arm designs, and custom-shader 3D scenes. The model is available via the GLM Coding Plan, ZCode, and Z.ai Chat; an API and open weights are planned after further safety testing, and a much larger model is "expected soon." Notably, **OpenAI has used a similar loop architecture since GPT-6 Astra**, and Z.ai concedes the architecture's biggest weakness is overly long reasoning phases where the model gets stuck. (Z.ai, The Decoder, MLQ.ai, Investing.com — Nov 23)

**Why it matters:** Looped/shared-weight training (dating to the 2018 Universal Transformer) has long underperformed same-compute non-looped baselines. GLM-5.4 is the first flagship-scale deployment that claims to close that gap at 750B — a credible signal that **compute depth, not parameter count, is the new scaling axis** — and it lands from a Chinese lab, in the same week OpenAI published its internal perplexity curve. The 30B test results are a strong architectural proof-of-concept, but the 750B figures remain unaudited (no independent evals yet).

**Sources:**
- https://the-decoder.com/z-ai-follows-openai-into-loop-transformer-territory-with-its-new-750b-flagship-model/
- https://mlq.ai/news/zai-launches-glm-54-a-750-billion-parameter-model-built-on-a-looped-transformer/
- https://www.investing.com/news/stock-market-news/zai-unveils-glm54-model-with-loop-transformer-design-93CH-5045609
- https://z.ai/blog/glm-5.4

---

### 2. NVIDIA Board Reinstates Jensen Huang as President, CEO, and Board Director (Nov 23)

**What happened:** NVIDIA's board of directors **unanimously reinstated Jensen Huang as president, CEO, and board member, effective immediately**, ending the ~10-day interim period in which CFO **Colette Kress** had run the company after Huang's Nov 12 resignation amid the espionage scandal that wiped out **$1.4 trillion** in market value. Per NVIDIA's press release, the decision followed talks with Huang and **feedback from senior US government officials who concluded his return poses no national security risk**. President Trump praised the move on Truth Social, saying the US Attorney General found **no evidence of wrongdoing** by Huang; **NVIDIA's stock jumped more than 30 percent** on the news. The reinstatement comes with conditions: an **independent board committee is still investigating** the foreign-intelligence targeting with outside counsel, the US government is reviewing NVIDIA's business dealings, and Trump urged the company to keep probing its **export-control compliance** — for which NVIDIA has created a **dedicated National Security & Export Control Oversight Committee** and is searching for a **Chief Compliance Officer**. Simultaneously, the **New York Times** reported (Nov 22) that **Alice Huang** kept in contact with an official of China's Ministry of State Security from spring 2025 through this fall, and that her business partner **Kang Wei** is believed to have cooperated with the ministry; federal investigators are probing whether the pair used a web of Southeast Asian companies (including her firm **Megaspeed**) to funnel NVIDIA AI chips into China. Huang is set to **testify behind closed doors before the US House on December 1**. (NVIDIA, The Decoder, NYT, Reuters — Nov 22–23)

**Why it matters:** The single largest market-cap story of the quarter resolved in a single board vote, but the governance scaffolding (oversight committee, CCO search, closed-door House testimony) means the export-control and national-security questions stay live through year-end — directly intersecting the Nov 16 interim final rule on AI compute export controls (see Nov 22 edition).

**Sources:**
- https://nvidianews.nvidia.com/news/nvidia-board-reinstates-jensen-huang-as-president-ceo-and-board-director
- https://nvidianews.nvidia.com/news/nvidia-board-of-directors-establishes-national-security-and-export-control-oversight-committee
- https://www.nytimes.com/2026/11/22/us/politics/alice-huang-china-spy-agency-nvidia.html
- https://the-decoder.com/jensen-huang-resigns-as-nvidia-ceo-after-espionage-scandal-wipes-out-1-4-trillion-in-market-value/

---

### 3. Riemann Hypothesis Proof Clears First Major Verification Gate — Lean/Mathlib Certification, Byte-Identical Rebuild, and a Zeta-Free Cross-Check (Nov 21–23)

**What happened:** The week's defining AI-for-mathematics story advanced past the announcement phase into **formal community certification**. On **Nov 21 at 13:55 UTC**, the **Lean and Mathlib communities** (endorsed by the Lean FRO and the Mathlib Initiative) published a joint statement: **"We hereby certify that both the statement and the proof of the Riemann Hypothesis are correct… We have full confidence that Alpöge's proof of the Riemann Hypothesis is correct."** The certification rests on four criteria: (1) the statement is Mathlib's own vetted definition; (2) the **175,187-module / ~17.4M-line** library compiles with zero errors (dozens reproduced the same raw proof export); (3) an isolated statement file importing only Mathlib was confirmed — by two independent statement-matching tools — to be exactly what Alpöge's library proves; and (4) the exported raw proof was accepted by Lean's official kernel plus independent checkers **con-leche** and **con-ron** (which carry a formal proof they cannot accept a false proof). MIT's **Andrew Sutherland** ledger (updated Nov 22) shows an **independent sandboxed `lake build` on a separate, no-network machine reproducing the 61,570,595,788-byte export byte-for-byte**, all **175,187 modules replayed through the Lean kernel** (175,187/175,187, zero rejections), and — critically — a **cross-check that does not depend on Mathlib's zeta-function definition at all**: combined with independent formalizations of **Robin's and Lagarias's criteria**, the proof yields zeta-free theorems, and a `lake comparator` pass completed **Nov 22 at 04:16 UTC** with the verdict **"Your solution is okay!"** (Lean paranoid kernel, nanoda, and the default kernel all accept). Still in progress as of the last update: the end-to-end `lake comparator` run and the Lean-kernel replay of the full export. In parallel, **Stanford's Ravi Vakil** (AMS president) published a **"hurried announcement"** of an **all-human, no-AI competing GRH draft by Alessandro Masullo**, reviewed for months by Brian Conrad — with several problems reported within ~8 hours (identified with AI assistance), and Vakil explicitly claiming no correctness. Alpöge's method extends Stepanov's idea by chaining transformations (the LLM supplied the insight that a length-X sequence needs exactly √X chained transformations); printed out, Claude's argument would run **over 250,000 pages**. (Lean community blog, math.mit.edu, riemannhypothesissolved.com, The Decoder — Nov 21–23)

**Why it matters:** This is the first time a Millennium-Prize-class result has cleared a **community-endorsed, machine-checked verification gate** — the bar that separates "AI produced a plausible proof" from "the mathematical community certifies it." The zeta-free Robin/Lagarias cross-check is the strongest independent signal yet that the Lean object is proving the real theorem, not a mistranslated one. The Masullo draft keeps a human-only fallback in play while the audit continues.

**Sources:**
- https://leanprover-community.github.io/blog/posts/riemann-hypothesis
- https://math.mit.edu/~drew/grh
- https://riemannhypothesissolved.com/status
- https://the-decoder.com/hours-after-anthropic-claims-a-claude-proof-of-the-riemann-hypothesis-stanford-releases-an-all-human-competing-draft/

---

### 4. Anthropic: Claude Now Writes Over 90% of Its Code — and "One Agent Beats Many Subagents" (Nov 22–23)

**What happened:** Anthropic published two practitioner-level disclosures this week. First, the company says **Claude now writes over 90% of its own code** — a concrete, internal codebase-level adoption figure for frontier-model self-modification, paired with the company's public call for an **"AI pause button"** for the industry. Second, Anthropic's engineering guidance now argues that, **now that models can handle complexity alone, one well-scoped agent beats many subagents**: the prior "orchestrator spawns N subagents" pattern is being retired in favor of a single agent with strong context management, since modern models can carry the complexity that used to require decomposition. Together these are a rare, quantitative look at how a frontier lab is actually using its own model internally — and a direct course-correction on the multi-agent orchestration pattern the broader agentic-AI ecosystem has been building on. (Anthropic, The Decoder — Nov 22–23)

**Why it matters:** The 90%-of-own-code figure is the most concrete "AI writes the AI company" data point published so far, and the subagents retreat is a practical signal that **context engineering, not agent fan-out, is the current scaling lever** — relevant to anyone building agentic pipelines on Claude or similar models.

**Sources:**
- https://the-decoder.com/anthropic-says-claude-now-writes-over-90-of-its-code-and-wants-the-world-to-have-an-ai-pause-button/
- https://the-decoder.com/anthropic-says-one-ai-agent-beats-many-subagents-now-that-models-can-handle-complexity-alone/
- https://the-decoder.com/anthropic-wants-you-to-know-claude-leads-a-quarter-of-its-research-but-lead-doesnt-mean-what-you-think/

---

### 5. METR: AI Is Improving Faster Than We Can Reliably Test Its Safety (Nov 20–23)

**What happened:** **METR** (the model evaluation and threat research lab) published its **Q4 2026 capability update**, warning that **AI systems are getting better faster than experts can reliably test whether new systems are safe** — i.e., the evaluation and safety-testing pipeline is the lagging constraint, not model capability. In the same window, **Meta's Chief AI Officer Alexandr Wang** framed the AI-assisted Riemann proof as "a clear sign that superintelligence is right around the corner," arguing that **raw intelligence is no longer the bottleneck** — current models only lack domain-specific knowledge and practical infrastructure to outperform humans in nearly every field, including AI research itself — and warning that the industry "isn't thinking hard enough about what comes next," needing to ensure AI "gives people more agency rather than taking control of society." (METR, The Decoder — Nov 20–23)

**Why it matters:** Two independent signals — a capability-lab's own evals and a frontier-lab executive — converging on the same point: **the safety/evaluation infrastructure is not keeping pace with capability growth.** For teams deploying frontier models, this is an argument to treat evals and guardrails as the binding constraint, not an afterthought.

**Sources:**
- https://metr.org/blog/2026-11-20-q4-2026-capability-update/
- https://the-decoder.com/ai-is-getting-better-faster-than-experts-can-reliably-test-whether-new-systems-are-safe-metr-warns/
- https://the-decoder.com/frontier-radar-5-if-agi-is-so-close-why-is-everyone-leaving-the-neolabs-and-their-bets/

---

## New Use Cases

### AI-Assisted Proof Verification as a Research Discipline — Lean/Comparator Ecosystem (Nov 20–23)
The Riemann episode turned formal verification into a live research workflow: the community stood up **independent statement-matching tools (`comparator`, `con-leche --compare`)**, **byte-identical sandboxed rebuilds**, **kernel-replay harnesses (leanchecker, nanoda, con-leche, con-ron, lean4lean)**, and a **zeta-free Robin/Lagarias cross-check** — all within ~48 hours. The reusable use case: **a machine-verifiable, independently reproducible audit pipeline for frontier-model mathematical output**, now documented as a replicable method rather than a one-off.
*Sources: https://math.mit.edu/~drew/grh · https://leanprover-community.github.io/blog/posts/riemann-hypothesis*

### Agentic Codebases as a First-Class Security Surface (Nov 19–23)
Following the Dragos/OpenRouter/Together AI prompt-leakage disclosures (Nov 22 edition), the emerging use case is **treating agentic code and prompts as a first-class security surface**: canary tokens in sensitive prompts, ZDR enforced at the account level (not trusted as a label), `allow_fallbacks: false` / provider pinning, and PR-level credential scanning for AI coding agents. Anthropic's "one agent beats many subagents" guidance reinforces the pattern — **concentrate context and minimize the number of autonomous write-capable agents** to shrink the attack surface.
*Sources: https://openrouter.ai/blog/announcements/data-processing-incidents-on-inference-providers/ · https://the-decoder.com/anthropic-says-one-ai-agent-beats-many-subagents-now-that-models-can-handle-complexity-alone/*

### Generalized Coding — Code as a Substrate for Video, Games, CAD, and Robotics (Nov 23)
Z.ai's GLM-5.4 "Generalized Coding" positioning extends code generation beyond software into **model-scored music videos, FreeCAD robot-arm designs, complete games, and custom-shader interactive 3D scenes** — i.e., code as the unified intermediate representation across creative and physical domains. This is a concrete use-case expansion of the "agentic coding" category into **multimodal and physical-asset generation**.
*Source: https://the-decoder.com/z-ai-follows-openai-into-loop-transformer-territory-with-its-new-750b-flagship-model/*

### Sovereign-AI Oversight as a Governance Product (Nov 12–23)
NVIDIA's reinstatement comes with a **dedicated National Security & Export Control Oversight Committee** and a **Chief Compliance Officer search** — a template for how frontier-adjacent companies will institutionalize **export-control and national-security compliance as a board-level governance function**, likely to be replicated across the semiconductor and AI-infra stack as the Nov 16 interim final rule takes effect.
*Source: https://nvidianews.nvidia.com/news/nvidia-board-of-directors-establishes-national-security-and-export-control-oversight-committee*

---

## Top Rated GitHub Projects Leveraging Agentic/Gen AI

| Repository | Stars* | What it does (agentic/Gen-AI angle) |
|---|---|---|
| [EL4CTEO/fast-anything](https://github.com/EL4CTEO/fast-anything) | 2,988 | **"Don't rewrite it in Rust. Rewrite the 5% that's slow"** — profiles Python/Node/Ruby apps and ports the hot functions **with your coding agent**, proving behavioral equivalence (created Nov 21). |
| [iamajmeena/neonclipping](https://github.com/iamajmeena/neonclipping) | 2,279 | **Free, local, open-source clip engine**: paste a link, get captioned 9:16 short-form clips in ~2 minutes — audio-first pipeline with a **local LLM** for captioning/editing (created Nov 19). |
| [leanprover-community/riemann-hypothesis](https://github.com/leanprover-community/riemann-hypothesis) | 802 | **Independent Comparator + verification harness** for Alpöge's Lean Riemann proof — the community audit infrastructure (statement matching, kernel replay, sandbox rebuild) that certified the AI-assisted proof (created Nov 20). |
| [boringmarketer/boring-marketing-skills](https://github.com/boringmarketer/boring-marketing-skills) | 810 | **32 free marketing skills for AI agents** — research, positioning, copy, pages, SEO, AI search, ads, email + a deep local-business pack; MIT-licensed (created Nov 16). |
| [CocoSgt/riemann-hypothesis-lean](https://github.com/CocoSgt/riemann-hypothesis-lean) | 541 | **Public mirror of Alpöge's Lean Riemann proof (with Claude)** — the ~17.4M-line formalization as a browsable repo for the audit effort (created Nov 20). |

\* Star counts verified via the GitHub API on November 22–23, 2026; all repos created Nov 15–22, 2026. (The Nov 22 edition covered rust-anything, deepseek-ai/chat-demo, linger, yogurt, blender-ai-mcp-addon, agentes-chat, supermimic, inference-optimisation-skill, PeakCut, pybot, lot-map, ste80-humanizer, mobile-agent-testers, agy-fast, and sprite-stacking; the Nov 15 Gemini-Config-Checker clone swarm was excluded as suspected star-farming.)

---

## Security & Remediation Watch

**New this cycle (Nov 20–23):**

1. **CVE-2026-133968 — MONAI Label path-traversal RCE, exploited in the wild by an AI-agent campaign (CVSS 9.8) — now PATCHED.** Amazon Threat Intelligence disclosed (Nov 20) that a **China-linked actor used the "Cairn" AI agent framework** to run a **48-hour campaign (Sept 8–10) against East Asian university research networks**, exploiting an unauthenticated path traversal in **MONAI Label ≤0.8.5** (`PUT /datastore/image`, `PUT /datastore/label`; default installs have no auth). The agent mapped the API and, in ~11 minutes, wrote arbitrary files, planted a **`sitecustomize.py` reverse shell**, and triggered training to execute as root. **The 0.8.6 security release shipped Nov 22** — `pip install -U monailabel==0.8.6` or `docker pull projectmonai/monailabel:0.8.6` (GHSA-qc22-rmgc-vg94, upstream fix PR #1915). **Until patched:** enable authentication, restrict the ANNOTATOR role, keep instances off untrusted networks, run as a non-privileged user. **Verify for compromise** if you ran an exposed instance during Sept 8–10 — the reverse-shell payload and root execution make retrospective detection essential. (AWS, The Register, BleepingComputer, VentureBeat, THN)
   *Sources: https://aws.amazon.com/blogs/aws/amazon-threat-intelligence-monai-label-campaign/ · https://www.theregister.com/2026/11/20/monai_label_zero_day_cairn/ · https://github.com/Project-MONAI/MONAI-Label/releases/tag/v0.8.6*

2. **AI inference supply-chain prompt leakage — treat July–Oct 2026 marketplace traffic as exposed (no CVE).** The most consequential AI-tooling security event of the cycle (see Nov 22 edition Top 5 #3): **OpenRouter removed ZDR labels from 125 MiniMax endpoints and offboarded three providers** (Nov 22); **Together AI confirmed June–July prompt downloads** after its AI coding agent leaked a Hugging Face credential into the public `xorl` repo. **Remediation:** if you routed sensitive prompts through OpenRouter marketplace endpoints or Together serverless inference in July–Oct 2026 — rotate any credentials/secrets that appeared in those prompts, audit logs, and assume retention. Going forward: enforce **ZDR at the account level**, set `allow_fallbacks: false` / pin providers, and use canary tokens in sensitive prompts. (OpenRouter, Together AI, Dragos)

**CISA KEV status (as of Nov 23):** A **new KEV batch was added Nov 21** (federal remediation deadline **Nov 30**), joining the **Nov 20 batch** (CVE-2025-42884 SAP NetWeaver SQLi, CVE-2026-76466 Cisco Expressway hardcoded credentials, CVE-2026-123890 VMware vCenter auth bypass, CVE-2026-129448 Apache Roller deserialization — federal deadline **Nov 23**, i.e., **today**). The **Nov 18 batch** (Synology, Apache Axis, REDCap) is **past its Nov 21 federal deadline** — verify patch status now. The **Java4Shell (CVE-2026-114938)** critical OpenJDK RCE from Nov 17 remains the top-priority patch of the cycle.
*Source: https://www.cisa.gov/known-exploited-vulnerabilities-catalog*

**Carry-forward / still in motion:**
- **Java4Shell (CVE-2026-114938)** — unauthenticated RCE in OpenJDK Base64 decoder; keep patching (see Nov 21 edition).
- **Agent-framework PyPI supply-chain compromise** — audit any `agentframework` installs from the compromise window (see Nov 21 edition).
- **OpenAI GPT-6.2 Astra cyber capability** (Critical threshold) — review exposure for teams giving it shell/network access (see Nov 21 edition).
- **NVIDIA export-control compliance review** — the board's new oversight committee and CCO search mean export-control and national-security compliance is now a standing, auditable governance function (see Top 5 #2).

---

## Also Notable

- **NVIDIA stock +30% on reinstatement** — the single largest one-day move tied to the espionage-scandal resolution; watch the Dec 1 closed-door House testimony for export-control fallout (see Top 5 #2).
- **METR Q4 capability update** — the eval/safety pipeline is the lagging constraint (see Top 5 #5).
- **Anthropic Claude self-adoption (90% of own code)** — the most concrete "AI writes the AI company" figure published to date (see Top 5 #4).
- **Z.ai GLM-5.4** — the first flagship-scale loop transformer; 750B figures unaudited pending independent evals (see Top 5 #1).
- **Arena Alignment Index (Nov 21)** — OpenAI holds ranks 1–7; Claude Fable 5.2 is #8, Kimi K3.1 Pro is #9 (first open-weight model in the top ten) (see Nov 22 edition).

---

## Sources

### Today's anchors
- https://the-decoder.com/z-ai-follows-openai-into-loop-transformer-territory-with-its-new-750b-flagship-model/
- https://mlq.ai/news/zai-launches-glm-54-a-750-billion-parameter-model-built-on-a-looped-transformer/
- https://www.investing.com/news/stock-market-news/zai-unveils-glm54-model-with-loop-transformer-design-93CH-5045609
- https://z.ai/blog/glm-5.4
- https://nvidianews.nvidia.com/news/nvidia-board-reinstates-jensen-huang-as-president-ceo-and-board-director
- https://nvidianews.nvidia.com/news/nvidia-board-of-directors-establishes-national-security-and-export-control-oversight-committee
- https://www.nytimes.com/2026/11/22/us/politics/alice-huang-china-spy-agency-nvidia.html
- https://the-decoder.com/jensen-huang-resigns-as-nvidia-ceo-after-espionage-scandal-wipes-out-1-4-trillion-in-market-value/
- https://leanprover-community.github.io/blog/posts/riemann-hypothesis
- https://math.mit.edu/~drew/grh
- https://riemannhypothesissolved.com/status
- https://the-decoder.com/hours-after-anthropic-claims-a-claude-proof-of-the-riemann-hypothesis-stanford-releases-an-all-human-competing-draft/
- https://the-decoder.com/anthropic-says-claude-now-writes-over-90-of-its-code-and-wants-the-world-to-have-an-ai-pause-button/
- https://the-decoder.com/anthropic-says-one-ai-agent-beats-many-subagents-now-that-models-can-handle-complexity-alone/
- https://the-decoder.com/anthropic-wants-you-to-know-claude-leads-a-quarter-of-its-research-but-lead-doesnt-mean-what-you-think/
- https://metr.org/blog/2026-11-20-q4-2026-capability-update/
- https://the-decoder.com/ai-is-getting-better-faster-than-experts-can-reliably-test-whether-new-systems-are-safe-metr-warns/
- https://the-decoder.com/frontier-radar-5-if-agi-is-so-close-why-is-everyone-leaving-the-neolabs-and-their-bets/

### Security
- https://aws.amazon.com/blogs/aws/amazon-threat-intelligence-monai-label-campaign/
- https://www.theregister.com/2026/11/20/monai_label_zero_day_cairn/
- https://github.com/Project-MONAI/MONAI-Label/releases/tag/v0.8.6
- https://www.cisa.gov/known-exploited-vulnerabilities-catalog
- https://openrouter.ai/blog/announcements/data-processing-incidents-on-inference-providers/
- https://www.together.ai/blog/security-event-prompt-leakage-for-requests-in-june-and-july-of-2026
- https://www.dragos.com/blog/three-breaches-endless-leaks-your-ai-supply-chain-needs-canaries/

### GitHub repos
- https://github.com/leanprover-community/riemann-hypothesis
- https://github.com/CocoSgt/riemann-hypothesis-lean
- https://github.com/iamajmeena/neonclipping
- https://github.com/EL4CTEO/fast-anything
- https://github.com/boringmarketer/boring-marketing-skills

---

## Compilation Note

Compiled Monday, November 23, 2026 (09:10–09:40 PT, America/Los_Angeles) by the ai-research cron job. Research pass covered Nov 22–23, 2026 via live web search and direct fetches across NVIDIA newsroom, The Decoder, MLQ.ai, Investing.com, Lean community blog, MIT (Sutherland verification page), riemannhypothesissolved.com, METR, NYT, Reuters, ABC, AWS Threat Intelligence, CISA KEV, OpenRouter, Together AI, Dragos, and the GitHub API (repo star counts verified live). All five anchors are new relative to the November 22 edition, which led with OpenAI's Pachocki perplexity disclosure, the Riemann proof announcement, prompt-leakage confirmation, Oregon's OpenAI suit, and the US export-control interim final rule. Today's edition is dominated by the **verification phase** of the Riemann story (community certification + zeta-free cross-check) and the **resolution of the NVIDIA CEO saga**, with **Z.ai's GLM-5.4** as the week's most significant new model-release architecture. Figures are as reported by the cited outlets and are not independently verified.
