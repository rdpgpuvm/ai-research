# 🔬 Agentic AI & Generative AI Research Report — September 12, 2026

*Compiled September 12, 2026 (America/Los_Angeles) from the arXiv announcement batch of **Friday, September 11, 2026** (cs.AI / cs.LG / cs.CL recent listings, 171+171+91 entries, IDs 2609.11xxx–119xx), live GitHub REST API records verified at compilation time, and industry news from the Sept 10–12 cycle (TechCrunch, OpenAI, DeepSeek, Cognition, Sakana AI, Google Cloud, Anthropic). Preprint results below are author-reported and not independently peer reviewed.*

---

## Top 5 Latest Advancements

### 1. OpenAI Ships the "Agents API" — The Codex Harness, Now a Managed Service

**What happened:** On **September 10**, OpenAI put the orchestration layer behind its own Codex product into a **public-beta Agents API**, alongside **GPT-Live-1** reaching general availability at $0.05/minute (full-duplex speech with custom voices and telephony). The Codex harness — open-sourced under Apache 2.0 in August — is now an operated service: a single API call returns **session orchestration, context compaction, sub-agent delegation, recovery, and durable long-running sessions**, with three sandbox options — an **OpenAI-hosted sandbox** (the same infra behind Codex/ChatGPT Work), your own `codex exec-server`, or a partner sandbox (Blaxel, Cloudflare, Daytona, DigitalOcean, E2B, Modal, Oracle, Runloop, Vercel). There is no extra charge for the harness itself — you pay only for tokens and tools. OpenAI is retiring the older Agent Builder and Evals on Nov 30, pointing code workflows at the Agents SDK/API.

**Why it matters:** This is the clearest signal yet that **the harness — not the model — is becoming the defensible, sellable layer** of the agent stack. OpenAI open-sourced the spec (you can inspect and self-host) and is selling the *operated* version of the exact runtime it runs internally. It reframes "agent framework" from a library you deploy into an infrastructure primitive you can consume or self-host, with MCP-server connections and skill/plugin injection as first-class.

**Sources:** https://openai.com/index/introducing-the-agents-api/ · https://developers.openai.com/api/docs/guides/agents-api/overview · https://runtimewire.com/article/openai-agents-api-managed-codex-harness

---

### 2. DeepSeek V4.1-Flash: 552B Parameters, a 1M-Token Context, and a ~890-Byte KV Cache per Token

**What happened:** DeepSeek released **DeepSeek-V4.1-Flash** on **September 10**, weights on Hugging Face under an MIT license the same day it went live. It is a **552B-parameter causal encoder–decoder MoE** (native vision, 1M-token context) that activates only **8B parameters per input token and 16B per output token**. The headline is the memory footprint: a new **Causal-Encoder-Decoder + compressed sparse attention (CSA2)** design with **FP4 KV caching** and "SWA Bounded Replay" cuts the KV-cache footprint to **~890 bytes per token — roughly a quarter of the prior V4-Flash and ~1/437th of DeepSeek V1 (2023)**. Base scores include 79.4 HumanEval, 74.1 MMLU-Pro; at max reasoning, **90.6 Terminal-Bench 2.1** and **74.2 DeepSWE v1.1**, ahead of leading Opus/GPT models on those agent benchmarks, with a 3,471 Codeforces rating. Priced at **$0.30/M input, $1.20/M output** (halved off-peak), and from **Sept 14 all `deepseek-v4-pro` API traffic routes to V4.1-Flash at Flash prices.**

**Why it matters:** The release lands *the day before* memory-chip investors sold off (Samsung −3.5%, SK Hynix −2.2%) — and it's the concrete data point that reframes the HBM-demand debate: frontier-class agent capability with an order-of-magnitude cache-footprint cut keeps pushing long-running, cache-heavy agent workloads toward being *economically* viable at scale. It's also the clearest case yet of an open-weight model undercutting the proprietary frontier on agentic coding *while* dropping the price.

**Sources:** https://lmstudio.ai/models/deepseek-v4.1-flash · https://rits.shanghai.nyu.edu/ai/deepseek-v4-1-flash-890-byte-kv-cache · https://eu.36kr.com/en/p/3977300285174021

---

### 3. Cognition Unveils SWE-2 — a Kimi K3 Post-Train That Tops Its Own Table on Terminal-Bench 2.1 (92.8) at 64% Lower Cost

**What happened:** Cognition released **SWE-2** on **September 10** (blog byline 09.11), a post-training of Moonshot's 2.8T-parameter **Kimi K3** base using a single-run RL recipe. It reports **50.0 on FrontierCode 1.1 Main** (within ~1 point of Claude Fable 5.1 at 50.9), **73.0 on DeepSWE v1.1**, and a **92.8 on Terminal-Bench 2.1** — the top row of Cognition's own comparison table — while costing **64% less than Fable 5.1** per FrontierCode rollout and cutting mean steps per run from 127 → 53 (medium effort). It ships **only inside Devin** (Desktop/CLI now; Web/Fusion rolling out); no standalone API or weights.

**Why it matters:** The launch is a live case study in **benchmark saturation and benchmaxing**. The same table shows **27.3 on the newer Terminal-Bench 4** (vs. 55.8–57.9 for Fable 5.1 / GPT-6 Astra), and the "64% cheaper" figure is a mean-cost-per-rollout number, not a public token rate. Community reaction — amplified by Cognition's history of demo criticism — centered on the gap between the saturated TB 2.1 headline and the much lower TB 4.0 score. It's the best current example of why single-benchmark "frontier parity" claims now require reading the *entire* table.

**Sources:** https://cognition.com/blog/swe-2 · https://www.orcarouter.ai/blog/cognition-swe-2-release · https://news.ycombinator.com/item?id=49645443

---

### 4. Sakana AI Ships Fugu Max & Fugu Ultra v2 — Orchestration Beats the Frontier Without Using It

**What happened:** On **September 11**, Sakana AI released **Fugu Max** (cost tier: $2/M in, $6/M out) and **Fugu Ultra v2** (capability tier: $5/M in, $30/M out; $10/$45 above 272K). Fugu is not a foundation model — it's a **language model trained to route tasks across a fixed pool of open-weight/specialized models and recursively call instances of itself**. Ultra v2 posts **48.3 on Chartography (visual reasoning) vs. 27.3 for Opus 5 and 29.5 for Fable 5**, and **74.3 on DeepSWE** — *without* Fable 5, Fable 5.1, or GPT-6-Astra in its pool. Max is best/joint-best on 5–6 of its benchmarks and expands the cost-performance Pareto frontier on 7 of 10. Both ship behind one OpenAI-compatible API; a tech report (arXiv:2606.21228) supplies the methodology.

**Why it matters:** Sakana is explicitly selling **"supply-chain resilience"** — the orchestrator's pool is swappable, so the system degrades gracefully when a provider goes down, is rate-limited, or changes terms. Two near-identical DeepSWE scores (Fugu Ultra v2's 74.3 vs. DeepSeek V4.1-Flash's 74.2) from radically different architectures (an orchestrated pool of open models vs. one sparse MoE) landed in the same week — the first clean head-to-head showing *two* routes to the same agentic capability frontier.

**Sources:** https://sakana.ai/fugu-max-release/ · https://openrouter.ai/sakana/fugu-ultra-v2 · https://pondero.ai/news/2026-09-12-sakana-fugu-max-ultra-v2

---

### 5. Google Open-Sources Mantis — a Portable "Find, Reproduce, and Patch" Security Harness for Coding Agents

**What happened:** Google released **Mantis** under Apache 2.0 (repo live; staff-security-engineer writeup on the Google Cloud blog), a **stack-agnostic, modular toolkit of security-review skills** for AI coding agents that runs the *entire vulnerability lifecycle*: scan → filter false positives → reproduce the bug in an isolated sandbox → write a minimal patch → **re-attack the patch** to confirm the fix → score residual risk. A companion `mantis-advise` skill lets coding agents write secure code the first time. It's designed to be invoked from *any* coding agent with a prompt pointing at the repo.

**Why it matters:** Security review is the highest-stakes, hardest-to-automate slice of agentic software engineering, and Mantis is the first credible *open* harness that treats "verified fixed" as a property (sandboxed repro + re-attack), not just "found a bug." It pairs with the academic side of this batch (BenchShield, below) to make **reward/review integrity** — proving a run actually did what it claims — a first-class engineering discipline rather than a prompt trick.

**Sources:** https://github.com/google/mantis · https://cloud.google.com/blog/products/identity-security/getting-started-with-the-mantis-harness-to-find-and-fix-bugs · https://www.marktechpost.com/2026/09/09/google-open-sources-mantis-a-modular-skills-toolkit-that-lets-coding-agents-find-reproduce-and-patch-vulnerabilities/

---

## Also Notable (Friday, Sept 11 arXiv batch + this week's news)

- **Anthropic names names in a Claude-distillation report** (Sept 10–11): a new report alleges roughly **200M Claude exchanges** were harvested to train competitor models, with the largest campaign attributed to **Alibaba (~151M exchanges across ~3,500 accounts, May–July)**, feeding Qwen; a **Moonshot** campaign allegedly routed some queries through **Chinese military infrastructure** (including surveillance-related prompts), and a **DeepSeek** campaign built "censorship-safe" policy-sensitive alternates. The Sept 5 baseline (Feb accusations) is now a *named, quantified* third act, and the US accusation of mass model theft is escalating. Source: https://techcrunch.com/2026/09/10/anthropic-details-distillation-campaigns-from-alibaba-moonshot-ai-and-deepseek/
- **OpenAI's Lean 4 formal-verification result gets a second look.** The Navier-Stokes follow-up shipped with a **Lean 4 formal verification completed in ~17 hours vs. ~132,800 person-hours by hand** (John D. Cook's framing). HN pushed back on the "four orders of magnitude" headline (the 40-hrs/page baseline dates to 2005), but the underlying point — *formal verification is becoming practical as an agent output* — reinforces the Sept 5 Fermat/Lean result (Claude's 13M-line FLT formalization) as a durable theme. Source: https://www.johndcook.com/blog/2026/09/09/formal-method-revolution/
- **The OpenAI math controversy widens** to a **second** researcher (Andreas Thom) accusing OpenAI of using his unpublished work on non-sofic groups, after Tristan Buckmaster; the pattern of generating 300B output tokens from a still-training model right after ingesting a major proof is the hardest claim to explain away. Source: https://www.theverge.com/ai-artificial-intelligence/993263/where-does-openai-get-mathematics-training-data
- **Magenta: closing the informal↔formal math loop** (arXiv:2609.11319): a training-free agentic pipeline that, from a natural-language problem, emits a Lean 4 statement **and a machine-checked proof**, with a statement-judge (formalization preserves the problem) and an error-attribution judge (re-derive vs. local repair). Reports **100% on AIME 2025/2026 and HMMT Feb 2026**, and — paired with the open-weight K2-Horizon-7B — **solves all six IMO 2026 problems.**
- **Ecdysis: training runtime harnesses for agents** (arXiv:2609.11677): distinguishes *model-specific* accommodation from *harness-level* repair via cross-instance failure aggregation, achieving up to **1.84× faster harness training at +18.56% reasoning accuracy** — a direct academic analog to the "harness is the product" story in the Agents API.
- **COBRA-Skills: budgeted skill optimization** (arXiv:2609.11682): frames agent-skill optimization as sequential budgeted optimization over an evolving candidate space, cutting optimization cost **55–58%** vs. SkillOpt with only 50 unique optimization examples per benchmark — continuing this month's "skills going institutional" thread (scientific-agent-skills, AREX).
- **BenchShield: reward-integrity instrumentation for agent evals** (arXiv:2609.11028): a finite-lifecycle model + static taint analysis + runtime attribution over a **456-trajectory, 31,000-run** corpus; lifts full-chain reward-hacking recall from 23–94% to **77–100%** at up to 65% lower per-task cost.
- **DriftNet: prompt-injection localization** (arXiv:2609.10892): a dual-head trajectory Transformer that answers *where* an indirect injection entered, *which steps* it corrupted, and *whether poison was resisted* — trajectory-level F1 **0.983**, 98.7% exact injection-point recovery on the AgentDrift benchmark (12,536 trajectories).
- **T1: Terminal-Agent RL for long-horizon tasks** (arXiv:2609.11042): a 122B MoE trained with RL operating a real cloud shell for 300+ tool-call turns, rewarded by running each task's own verifier; uses **TITO** (train-on-the-exact-sampled tokens + drift repair) and rollout-routing replay to fix the MoE train/inference gap, raising Terminal-Bench 2.1 from 43.8% → **64.0%** on an out-of-distribution corpus disjoint from Terminal-Bench 2.1.
- **The Agent Incident Registry (AIR)** (arXiv:2609.11030): a source-linked catalog of public agent failures with stable IDs, evidence, and missingness-aware labels for causal role/disclosure class/mechanism/outcome — extending last week's "swarm governance" theme from hypotheticals to a **case-retrieval and evaluation-scope-auditing** instrument.
- **terms.txt: a consent-and-compensation protocol for agentic web access** (arXiv:2609.11152): a robots.txt-style per-path/per-purpose machine-access file using Web Bot Auth signatures, signed intent/delegation, and HTTP 402 negotiation; a dependency-free implementation adds **0.20–0.65 ms per request** on one vCPU. A concrete proposal for fixing the bargain the open web broke under AI crawlers.

---

## New Use Cases

1. **Managed agent runtimes go GA.** OpenAI's **Agents API** (Sept 10) lets you spin up durable, long-running, sandboxed agents with sub-agent delegation and MCP connections behind one call — no extra harness fee. The companion **GPT-Live-1** (GA, $0.05/min) puts full-duplex, telephony-grade voice on the same managed plane, making "a phone call that runs an agent" a first-class product surface.
2. **Automated security patching as a workflow.** Google's open **Mantis** harness lets *any* coding agent execute the full vulnerability lifecycle (scan → sandboxed repro → patch → re-attack → residual-risk score), turning "secure by verified fix" into a repeatable, tool-driven use case — a natural complement to AI-discovered zero-days.
3. **Frontier output without frontier-model dependence.** Sakana **Fugu** is the first widely-shipped case of a *swappable pool* of open/specialist models beating the closed frontier on hard benchmarks (Chartography 48.3 vs. Opus 5's 27.3) at 40–60% lower cost — the operational pitch being resilience to any single provider's outage, rate-limit, or terms change.
4. **Cache-footprint economics reshape long-context agents.** DeepSeek V4.1-Flash's ~890-byte/token KV cache (1/437th of V1) makes 1M-token, long-running agentic sessions a *cost* question rather than a memory-wall question — a concrete tailwind for the long-horizon terminal/scientific workloads T1 and SWE-2 are targeting.
5. **Agent web access gets a payment/consent layer.** The **terms.txt** proposal (signed intent + HTTP 402 + receipts) is a practical answer to "the web's bargain is breaking under AI crawlers" — per-purpose, per-path machine terms with machine-checkable consent and compensation.
6. **Formal verification as an agent output keeps compounding.** Two weeks in a row: Claude's Lean FLT formalization (Sept 5 batch) and OpenAI's ~17-hour Lean verification of a Navier-Stokes result. "The agent does the work, the machine checker is the judge" is becoming a standard deliverable for math- and safety-critical agent tasks.
7. **Coding-model economics get sharper.** SWE-2 (50.0 FrontierCode at 64% lower rollout cost) and DeepSeek V4.1-Flash ($0.30/$1.20) both push the "capability-per-dollar" frontier, but each ships *behind a specific harness* (Devin / DeepSeek's API) — reinforcing that in 2026 the *bundled harness*, not the bare weights, is where coding capability is actually purchased.

---

## Top Rated GitHub Projects Leveraging Agentic/Gen AI

Star counts and metadata verified via the GitHub REST API at compilation time (September 12, 2026).

| Project | Stars | What it is |
|---|---|---|
| [anthropics/claude-code](https://github.com/anthropics/claude-code) | ~144.9k | Claude Code — agentic coding tool in the terminal |
| [openai/codex](https://github.com/openai/codex) | ~123.7k | Lightweight terminal coding agent; harness now exposed via the new Agents API |
| [deepseek-ai/deepseek-harness](https://github.com/deepseek-ai/deepseek-harness) | ~222.0k | DeepSeek's "everything-is-a-plugin" agent harness (+10k stars since Sept 5) |
| [punkpeye/awesome-mcp-servers](https://github.com/punkpeye/awesome-mcp-servers) | ~94.9k | The canonical MCP server collection — the de facto map of the agent tool surface |
| [all-hands-ai/openhands](https://github.com/all-hands-ai/openhands) | ~87.7k | OpenHands — AI-driven development / open agent for coding |
| [ChromeDevTools/chrome-devtools-mcp](https://github.com/ChromeDevTools/chrome-devtools-mcp) | ~51.8k | Chrome DevTools for coding agents (Google) |
| [K-Dense-AI/scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills) | ~44.7k | "Turn any AI agent into an AI Scientist" — the #1 agent-skills library for science |
| [openai/openai-agents-python](https://github.com/openai/openai-agents-python) | ~29.4k | OpenAI's multi-agent framework; the SDK layer beneath the new Agents API |
| [letta-ai/letta](https://github.com/letta-ai/letta) | ~24.7k | Platform for stateful agents with advanced memory that learns and self-improves |
| [HKUDS/DeepCode](https://github.com/HKUDS/DeepCode) | ~16.5k | Open agentic coding: harness, loop engineering, multi-agent orchestration |
| [google/mantis](https://github.com/google/mantis) | ~1.5k | **New this week** — Google's modular security-review skills toolkit for coding agents (Apache 2.0) |

**Ecosystem watch:** the week's real story is **the harness becoming a first-class product** — OpenAI open-sourced the Codex harness in August and now sells it managed (Agents API), Cognition shipped SWE-2 *only inside Devin*, Google open-sourced the Mantis security harness, and DeepSeek shipped a 552B open MoE that resets the agentic cost curve. On the academic side the Sept 11 batch answered the Sept 5 "agent stack stress-test" with concrete tools: **BenchShield** (reward integrity), **DriftNet** (injection localization), **Ecdysis** (harness training), **COBRA-Skills** (budgeted skill optimization), and **AIR** (an incident registry). The two competing bets on the agentic frontier — *one sparse MoE* (DeepSeek V4.1-Flash) vs. *an orchestrated pool* (Sakana Fugu) — landed within a tenth of a point on DeepSWE, and both under ~$1.20/M output. The **distillation escalation** (Alibaba's 151M-exchange campaign) is now the week's geopolitical wildcard, and **formal verification as an agent deliverable** (Lean FLT, Navier-Stokes in ~17 hours) is the week's quiet but durable win.

---

## Sources with Working URLs

### Fresh research (September 11, 2026 arXiv announcement batch)
- Magenta (Lean math verification loop): https://arxiv.org/abs/2609.11319
- Ecdysis (runtime harness training): https://arxiv.org/abs/2609.11677
- COBRA-Skills (budgeted skill optimization): https://arxiv.org/abs/2609.11682
- The Agent Incident Registry: https://arxiv.org/abs/2609.11030
- BenchShield (reward-integrity instrumentation): https://arxiv.org/abs/2609.11028
- DriftNet (prompt-injection localization): https://arxiv.org/abs/2609.10892
- T1 (Terminal-Agent RL, long-horizon): https://arxiv.org/abs/2609.11042
- terms.txt (agentic web access consent/compensation): https://arxiv.org/abs/2609.11152
- Unlearning-checkpoint audit (263 batch-normalized checkpoints): https://arxiv.org/abs/2609.11490

### Industry news & first-party posts (September 10–12, 2026)
- OpenAI Agents API: https://openai.com/index/introducing-the-agents-api/ · https://developers.openai.com/api/docs/guides/agents-api/overview · https://runtimewire.com/article/openai-agents-api-managed-codex-harness
- DeepSeek V4.1-Flash: https://lmstudio.ai/models/deepseek-v4.1-flash · https://rits.shanghai.nyu.edu/ai/deepseek-v4-1-flash-890-byte-kv-cache · https://eu.36kr.com/en/p/3977300285174021
- Cognition SWE-2: https://cognition.com/blog/swe-2 · https://www.orcarouter.ai/blog/cognition-swe-2-release · https://news.ycombinator.com/item?id=49645443
- Sakana AI Fugu Max / Ultra v2: https://sakana.ai/fugu-max-release/ · https://openrouter.ai/sakana/fugu-ultra-v2 · https://pondero.ai/news/2026-09-12-sakana-fugu-max-ultra-v2
- Google Mantis: https://github.com/google/mantis · https://cloud.google.com/blog/products/identity-security/getting-started-with-the-mantis-harness-to-find-and-fix-bugs
- Anthropic distillation report: https://techcrunch.com/2026/09/10/anthropic-details-distillation-campaigns-from-alibaba-moonshot-ai-and-deepseek/
- OpenAI Lean 4 formal verification (Navier-Stokes): https://www.johndcook.com/blog/2026/09/09/formal-method-revolution/
- OpenAI math controversy (second mathematician): https://www.theverge.com/ai-artificial-intelligence/993263/where-does-openai-get-mathematics-training-data

### GitHub project records (verified via API, September 12, 2026)
- https://github.com/anthropics/claude-code (~144,885★) · https://github.com/openai/codex (~123,707★)
- https://github.com/deepseek-ai/deepseek-harness (~221,974★) · https://github.com/punkpeye/awesome-mcp-servers (~94,879★)
- https://github.com/all-hands-ai/openhands (~87,712★) · https://github.com/ChromeDevTools/chrome-devtools-mcp (~51,783★)
- https://github.com/K-Dense-AI/scientific-agent-skills (~44,668★) · https://github.com/openai/openai-agents-python (~29,396★)
- https://github.com/letta-ai/letta (~24,718★) · https://github.com/HKUDS/DeepCode (~16,524★)
- https://github.com/google/mantis (~1,494★, new this week)

---

## Short Compilation Note

Compiled September 12, 2026 (America/Los_Angeles). The arXiv material is the **September 11 announcement batch** (cs.AI, cs.LG, and cs.CL recent listings; ~433 unique entries), with abstracts fetched from arXiv and GitHub REST records verified live at compilation time. News and first-party posts (OpenAI, DeepSeek, Cognition, Sakana, Google Cloud, Anthropic/TechCrunch) were fetched and verified across the Sept 10–12 window. Preprint results are author-reported and not independently peer reviewed. Theme of the day: **the harness, not the model, is where 2026's agent race is being decided.** OpenAI turned the Codex harness into a managed product; Cognition shipped SWE-2 *only* inside Devin; Google open-sourced the Mantis security harness; and DeepSeek reset the agentic cost curve with a 552B open MoE. The Sept 11 arXiv batch answered the Sept 5 "stress-test the agent stack" prompt with tools — BenchShield (reward integrity), DriftNet (injection localization), Ecdysis (harness training), COBRA-Skills (budgeted skills), AIR (an incident registry), and T1 (terminal-agent RL). On the frontier, two structurally opposite bets — one sparse MoE (DeepSeek V4.1-Flash) and an orchestrated pool (Sakana Fugu) — landed within a tenth of a point on DeepSWE, both under ~$1.20/M output. Meanwhile the **distillation escalation** (Alibaba's 151M-exchange campaign) became the week's geopolitical wildcard, and **formal verification as an agent deliverable** (Lean FLT two weeks running, Navier-Stokes in ~17 hours) quietly became the week's most durable win.
