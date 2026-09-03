# 🔬 Agentic AI & Generative AI Research Report — September 3, 2026

*Compiled September 3, 2026 (America/Los_Angeles) from the arXiv announcement batch of September 2, 2026 (cs.AI / cs.CL / cs.LG recent listings, IDs 2609.024xx–028xx), live GitHub REST API records verified at compilation time, and industry news from TechCrunch's AI feed (Sept 1–3, 2026). The research findings below are author-reported preprint results and have not been independently peer reviewed.*

---

## Top 5 Latest Advancements

### 1. Nemotron-3-CC: the First AI System to Outscore the Top Human at an IOI Problem Set

**What happened:** NVIDIA published the end-to-end specialization pipeline behind **Nemotron-3-CC** (arXiv:2609.02849): large-scale curation of **22,000 competitive-programming problems**, synthetic reasoning traces, SFT, and RL. **Nemotron-3-Nano-CC (30B-A3B)** was trained with SFT+RL and **Nemotron-3-Ultra-CC (550B-A55B)** with SFT alone, plus **GenCorrect**, a feedback-driven test-time compute strategy that iteratively generates, evaluates, and refines diverse solutions. On IOI 2025, Nano-CC improved from 130 to 291 points after post-training and to **468 with GenCorrect** (gold threshold: 438.3); Ultra-CC reached 502. The decisive result is prospective: evaluated **live during IOI 2026** under the same time, internet-access, and submission constraints as human contestants, the competition-specific Ultra-CC system scored **535.4 of 600** — above the gold threshold of 361.12 *and* above the top human score of 498.27.

**Why it matters:** Competitive programming has been the cleanest stress test of LLM reasoning, and for the first time an AI crossed from "medal-level" to **beating the best human** on a live IOI problem set — with test-time compute as the decisive lever (468 vs 291 for the same 30B model). A 30B-A3B MoE with the right post-training plus iterative self-refinement now clears gold, which reframes competitive programming as a tractable RLVR benchmark rather than a frontier-model-only arena.

**Source:** https://arxiv.org/abs/2609.02849

---

### 2. Repo-To-Skill (DisCo) + the AREX Skill Library: Distilling 1,000 Repositories into 5,000+ Verified Agent Skills

**What happened:** *Repo-To-Skill* (arXiv:2609.02749) formalizes **operational knowledge** — the know-how that separates *knowing a method* from *making it work* — as a layer that current agent architectures leave outside the agent. The paper's **DisCo** research agent both creates and uses distilled skills, in two complementary modes: *task-agnostic* distillation of the field's widely used repositories, and *task-oriented* distillation for a concrete task. Applied across the open ML ecosystem, this yields the **AREX-Skill Library: 5,000+ verified skills distilled from 1,000 widely used ML repositories**, organized into 20 areas and 178 capability families. With the GPT-5.5 backbone, research harness, and execution budget held fixed, the skill-equipped agent scores **134.3% higher on MLE-bench**, 34.4% higher on PaperBench, 9.2% higher on FrontierCS, and 14.0% higher on PassNet than the same agent without skills.

**Why it matters:** A +134% MLE-bench gain from *zero parameter changes* — just compact, verified skills — is one of the largest harness-side effects reported this year, and it lands the same week as DeepSeek's dsh plugin ecosystem and Microsoft's skill-recorder (see GitHub table). "Skills as a portable, distillable asset class" has moved from thesis to measured engineering practice, and the AREX library is now a concrete public substrate for it.

**Source:** https://arxiv.org/abs/2609.02749

---

### 3. Declarative Attention: Language Models Can Control Their Own Attention

**What happened:** *Language Models Can Control Their Own Attention* (arXiv:2609.02737) introduces **Declarative Attention (DA)**, an intrinsic approach to sparse decoding: instead of an extrinsic proxy selecting tokens for the model (which still costs O(N) per step), the model itself **declares in its chain-of-thought where it needs to attend**, partitioning generation into `<global>` (full context), `<focus>` (a specific region), and `<local>` (recent output only). The inference engine parses these declarations *like tool calls* and skips most of the KV-cache read. Zero-shot across **15 long-context tasks** on off-the-shelf models: **Gemma-4-31B** attends **52.0% fewer tokens** during decoding with only a 1.27pp accuracy drop; **Qwen-3.6-27B** cuts attended tokens 31.1% with a 2.75pp drop — and the accuracy cost shrinks with model scale.

**Why it matters:** Long-context inference cost is usually attacked from outside the model (retrieval, proxy scorers, pruning). DA shows the model already knows which context matters and can be given a *protocol* to say so — turning attention sparsity into something the model itself programs, with no training. The tool-call-style interface is a natural fit for agent runtimes that already parse structured declarations, and it opens a new axis of sparse attention to be optimized via training.

**Source:** https://arxiv.org/abs/2609.02737

---

### 4. SafeEvolve: Harness–Policy Co-Evolution from Agent Experience for Safety Alignment

**What happened:** *SafeEvolve* (arXiv:2609.02786) is an experience-driven self-evolving framework for agent safety that closes a gap between the two existing levers — external harness updates and policy optimization — neither of which alone bridges runtime control with intrinsic safety. SafeEvolve mines **safety evidence from completed on-policy trajectories** and runs a continual co-evolution loop: on the *harness side*, trajectory-level evidence becomes **bounded, component-level updates** across the safety prompt and hierarchical skills, yielding auditable and *reversible* harness artifacts; on the *policy side*, a two-stage SFT-RL paradigm (harness-use SFT to bootstrap reliance on evolved artifacts, then harness-augmented RL with verifier-decomposed rewards) shapes autonomous safety behavior during multi-step exploration. On agentic safety benchmarks it achieves a stronger safety-utility tradeoff than baselines: for **Qwen3.5-4B, a 3× reduction in attack success rate on AgentDojo while improving benign utility from 59.79% to 61.86%**.

**Why it matters:** Security is the weak point of self-evolving harnesses — an agent that rewrites its own scaffolding can drift into unsafe territory. SafeEvolve answers with *safety experience as the training signal*: the harness gains are auditable and reversible (a property the StarHarness/Recuris line of work has lacked), and the two-stage policy side teaches the model to *use* the evolved safety scaffolding rather than merely tolerate it. Combined with this week's CodePoisonRAG (below), agent safety is rapidly becoming its own engineering discipline with measured baselines.

**Source:** https://arxiv.org/abs/2609.02786

---

### 5. Coverage, Not Targeting: A Structural Regime in Multi-Turn Agent Credit Assignment

**What happened:** *Coverage, Not Targeting* (arXiv:2609.02417) identifies the structural quantity that predicts when per-turn credit targeting is the right move in multi-turn agentic RL: the **verifier information density** V_d = k/C (the fraction of an agent's C-step causal chain whose per-turn correctness the verifier actually exposes). Terminal-state verifiers sit deep in a **low-V_d regime** where targeting is the wrong axis: in controlled shared-rollout comparisons on τ²-bench, a **uniform dense reward** spread across turns beats the sparse binary outcome reward (which is *net-harmful* on 4/5 seeds), while concentrating the same advantage on progress turns — or on random turns — is equally harmful. The mechanism: terminal verification collapses the observable signal to a single final-write turn (k=1 in 98% of rollouts) while success needs a 5–8-step prerequisite chain. A synthetic phase boundary puts the crossover at **V_d\* ≈ 0.8**, versus measured V_d ≈ 0.15 on τ²-bench and ≈ 0.4 on BFCL V3 (where uniform wins too, with a matched-concentration shuffled control negative on 8/8 seeds). The effect reproduces across model families on ToolACE-2-8B (Δ = −0.048 over 32 pre-registered seeds; an independent 20-seed replication is itself significant).

**Why it matters:** Multi-turn RLVR is converging on fancy credit-assignment machinery (per-turn critics, influence graphs, token-level rewards) while this result shows the *reward schedule itself* — not the targeting sophistication — is the dominant lever when verifiers are sparse. The prescriptive rule is clean and testable: if your verifier only sees the final state, spread reward uniformly; only reach for per-turn targeting once you push V_d toward ~0.8.

**Source:** https://arxiv.org/abs/2609.02417

---

## Also Notable (same batch)

- **CORAL** (arXiv:2609.02730): an LLM-native harness that puts an agent in a *continual closed loop on a live production recommender system* — each cycle it observes operating signals, reasons over a memory of past decisions and outcomes, and invokes tools (including a numerical optimizer constrained to a fixed operating budget) to reconfigure retrieval/ranking/serving, improving *in context without parameter updates*. A/B-validated on two large-scale social platforms: engagement improved at no added serving cost on one, serving cost reduced without engagement loss on the other.
- **Discriminative World Models for Web Agents** (arXiv:2609.02885): world models for test-time action selection are usually trained by supervised next-state prediction — an objective misaligned with the downstream ranker. The fix is **predicted-state matching**: the predicted representation must distinguish the true resulting state from those reached by alternative actions, trained on a branching dataset derived from WebArena Go-Browse. Beats supervised-next-state world models and improves PRM-style ranking on WebPRMBench and end-to-end success on WebArena-Lite.
- **Cliff** (arXiv:2609.02817): a reward-shaping strategy that uses an off-the-shelf LLM teacher to locate the **first mistake** in each rollout, converting it into token-level advantages (positive for the correct prefix, negative after) — no specialized process reward model needed. Across 12 scenarios it outperforms on-policy distillation by 15% and standard GRPO by 7%.
- **CivBench** (arXiv:2609.02459): an open-source long-horizon benchmark for MCP-mediated agents in *Civilization VI* — 300+ turn episodes, thousands of tool calls, 76 MCP tools, plus a narration layer that converts visual game state into structured text. Early runs reveal consistent failure modes: agents under-monitor strategically relevant state (querying every 30–75 turns when playbooks say every 20) and frequently fail to execute their own near-term planning commitments (RAG@10).
- **CodePoisonRAG** (arXiv:2609.02774): a black-box, upstream knowledge-poisoning attack on retrieval-augmented code generation — CWE-specific vulnerability injection plus semantic mislabeling, with at most one poisoned artifact per anticipated task. All 85 crafted artifacts (10 CWE classes, Java and C) land in the Top-3 retrieval results, at a mere 0.7% corpus-poisoning ratio.
- **EarlyEval** (arXiv:2609.02783): cheaper agent evaluation via early outcome prediction — deciding how an agent run will end before it finishes.
- **Trace as State** (arXiv:2609.02702): treats reasoning traces as *conditional states* for long-context transformers, an alternative to treating them as inert context.
- **Dutch Books for Language Models** (arXiv:2609.02797): operationalizing Dutch-book calibration attacks on LMs — probabilistic incoherence can be exploited against model-predicted prices.

---

## New Use Cases

1. **The open-model supply chain changes hands: Nvidia acquires Hugging Face for $12.93B** (TechCrunch, Sept 3). After weeks of rumors, Nvidia confirmed the acquisition of the platform hosting **3M models, 1M applications used by 18M+ developers, and 500K datasets**. Jensen Huang says Hugging Face will continue supporting open-source and open-weight models and expand developer access — the hardware vendor now owns the default registry, model card, and Spaces distribution layer for the open ecosystem, with direct implications for who curates (and who is curated) in the agent-model stack.
2. **Offensive security reaches a critical threshold: OpenAI's Astra.** OpenAI disclosed that Astra will be the first LLM to meet its own "critical cybersecurity threshold" in preparation for release, with its most advanced capabilities access-limited (Sept 1). A follow-up report (The Information via TechCrunch, Sept 2) says Astra uses a reasoning technique called **"recurrent depth" (a.k.a. "opaque recurrence")** that lets it operate outside sequential thinking — making its chain of thought materially harder to monitor, which has "rattled" AI safety experts even though current use of the technique is reportedly limited.
3. **Weather as a live AI inference surface: Google's WeatherNext 3.** DeepMind and Google Research released a next-generation weather model that "sees the changing atmosphere more clearly and predicts its behavior more often," and Google says it will begin feeding **search, Google Maps, Gemini, and its cloud platforms** — deep-learning meteorology moving from research demo into the consumer information layer (Sept 3).
4. **Scam authentication as a shopping-agent feature.** Amazon's **Alexa for Shopping** can now "definitively" confirm whether a message claiming to be from Amazon is genuine, by checking sender information, content, timing, and metadata against the billions of messages Amazon has sent — a response to ~360,000 customers per year asking (Sept 2). A consumer assistant that verifies the *authenticity of the channel* itself, with the system improving as users report suspicious messages.
5. **Privacy compliance as a consumer assistant differentiator.** Ollie, a family-focused personal AI assistant, is among the first mainstream (non-enterprise) AI assistants to achieve **SOC 2 compliance** — formal, independently audited data controls — and is explicitly positioning audited privacy as the wedge in the assistant race (Sept 3).
6. **Legal ground settles for the pretraining industry.** The US government sided with OpenAI on the question of training LLMs on copyrighted material (Sept 2) — a de-risking event for the entire open-data and fine-tuning economy, and a signal to the ~500K-dataset Hugging Face ecosystem now entering Nvidia ownership.

---

## Top Rated GitHub Projects Leveraging Agentic/Gen AI

Star counts and metadata verified via the GitHub REST API at compilation time (September 3, 2026).

| Project | Stars | What it is |
|---|---|---|
| [deepseek-ai/deepseek-harness](https://github.com/deepseek-ai/deepseek-harness) | ~210.8k | DeepSeek's "everything-is-a-plugin" agent harness (Cordis-powered); crossed 210k stars this week |
| [agentscope-ai/agentscope](https://github.com/agentscope-ai/agentscope) | ~30.6k | Build and run agents you can see, understand, and trust |
| [anywhere-labs/dsh-desktop](https://github.com/anywhere-labs/dsh-desktop) | ~23.3k | Desktop client for the DeepSeek Harness plugin ecosystem ("the desktop itself is a plugin") |
| [letta-ai/letta](https://github.com/letta-ai/letta) | ~24.6k | Platform for stateful agents with advanced memory that learns and self-improves |
| [titanwings/distilly](https://github.com/titanwings/distilly) | ~24.3k | Distill how people think into reusable Skills for any agent or bot |
| [guillaumemeyer/watermarks-remover](https://github.com/guillaumemeyer/watermarks-remover) | ~20.3k | Privacy-first app that strips multi-vendor AI watermarks (C2PA/metadata) from content you own |
| [firecrawl/anydoc](https://github.com/firecrawl/anydoc) | ~20.2k | Rust converter: Word/PPT/Excel/OpenDocument/RTF/EPUB/CSV/PDF → clean Markdown for agent/RAG pipelines |
| [HKUDS/DeepCode](https://github.com/HKUDS/DeepCode) | ~16.5k | Open agentic coding: agent harness, loop engineering, and multi-agent orchestration |
| [yc-software/qm](https://github.com/yc-software/qm) | ~14.5k | Multiplayer agent harness for work |
| [awesome-dsh-plugin/awesome-dsh-plugin](https://github.com/awesome-dsh-plugin/awesome-dsh-plugin) | ~14.4k | Curated plugin list for DeepSeek Harness |
| [lsdefine/GenericAgent](https://github.com/lsdefine/GenericAgent) | ~14.1k | Self-evolving agent: grows a skill tree from a 3.3K-line seed |
| [pathwaycom/arc-task-gen](https://github.com/pathwaycom/arc-task-gen) | ~10.4k | Generates original ARC-AGI-1-style tasks distribution-matched to the public eval set |
| [trycompai/crm](https://github.com/trycompai/crm) | ~9.6k | Open-source agentic-first CRM designed for AI agents |
| [MoonshotAI/Kimi-K3](https://github.com/MoonshotAI/Kimi-K3) | ~8.7k | Moonshot's open frontier-intelligence model release |
| [FareedKhan-dev/kimi-k3-in-c](https://github.com/FareedKhan-dev/kimi-k3-in-c) | ~7.1k | 2.78-trillion-parameter Kimi K3 running inference on a single CPU in 8.24 GB of RAM (portable C99, no BLAS) |
| [sapientinc/PRAXIST](https://github.com/sapientinc/PRAXIST) | ~6.9k | Autonomous research system for measurable, computer-executable research (new this week) |
| [genspark-ai/genoffice](https://github.com/genspark-ai/genoffice) | ~4.8k | Free open-source alternative to Microsoft Office with built-in AI agents (Word/Excel/PowerPoint) |
| [microsoft/skill-recorder](https://github.com/microsoft/skill-recorder) | ~3.8k | Records your on-screen work session and uses the GitHub Copilot CLI to reconstruct it as instructions (new: Microsoft) |

**Ecosystem watch:** the DeepSeek Harness cluster keeps compounding — the core repo passed **210k stars** (≈+11k since Aug 27), dsh-desktop passed 23k, and the plugin list, routing suites, and web aggregation ecosystem continued expanding. The *skill* layer of the agent stack is the week's through-line: the AREX skill library (Repo-To-Skill, above) quantifies the payoff, while Microsoft shipped **skill-recorder** (screen-session → agent instructions) on the same day. Moonshot's **Kimi-K3** open release is spawning an immediate community port (a C99 single-CPU build of the 2.78T-parameter model), and GenSpark's **genoffice** points at agentic office suites as the next consumer battleground — one week after Nvidia made the open-model registry part of its own stack.

---

## Sources with Working URLs

### Fresh research (September 2, 2026 arXiv announcement batch)
- Nemotron-3-CC (IOI 2025/2026 post-training): https://arxiv.org/abs/2609.02849
- Repo-To-Skill / DisCo / AREX-Skill Library: https://arxiv.org/abs/2609.02749
- Language Models Can Control Their Own Attention (Declarative Attention): https://arxiv.org/abs/2609.02737
- SafeEvolve: https://arxiv.org/abs/2609.02786
- Coverage, Not Targeting: https://arxiv.org/abs/2609.02417

### Additional notable submissions (same batch)
- CORAL: https://arxiv.org/abs/2609.02730
- Discriminative World Models for Web Agents: https://arxiv.org/abs/2609.02885 (project page: https://dhruvpendharkar.github.io/dwm/)
- Cliff: https://arxiv.org/abs/2609.02817
- CivBench: https://arxiv.org/abs/2609.02459
- CodePoisonRAG: https://arxiv.org/abs/2609.02774
- EarlyEval: https://arxiv.org/abs/2609.02783 · Trace as State: https://arxiv.org/abs/2609.02702 · Dutch Books for LMs: https://arxiv.org/abs/2609.02797

### Industry news (TechCrunch, September 1–3, 2026)
- Nvidia confirms Hugging Face acquisition ($12.9B): https://techcrunch.com/2026/09/03/nvidia-confirms-it-will-buy-hugging-face-for-12-9-billion/
- OpenAI Astra "critical cybersecurity threshold" disclosure: https://techcrunch.com/2026/09/01/open-ais-astra-model-is-on-the-way-and-very-good-at-breaking-into-computer-systems/
- Astra "recurrent depth" / "opaque recurrence" safety concerns: https://techcrunch.com/2026/09/02/openais-new-reasoning-technique-alarms-ai-safety-experts/
- Google WeatherNext 3: https://techcrunch.com/2026/09/03/googles-latest-ai-weather-model-gives-you-no-excuse-to-forget-your-umbrella/
- Amazon shopping-AI scam verification: https://techcrunch.com/2026/09/02/psa-amazons-shopping-ai-can-now-tell-you-if-that-message-is-a-scam/
- Ollie SOC 2 privacy positioning: https://techcrunch.com/2026/09/03/ollie-is-betting-privacy-can-win-the-ai-assistant-race/
- US government sides with OpenAI on LLM training copyright: https://techcrunch.com/2026/09/02/u-s-government-sides-with-openai-on-issue-of-training-llms-on-copyrighted-material/

### GitHub project records (verified via API, September 3, 2026)
- https://github.com/deepseek-ai/deepseek-harness (~210,848★, TypeScript; created 2026-08-13)
- https://github.com/agentscope-ai/agentscope (~30,569★) · https://github.com/anywhere-labs/dsh-desktop (~23,335★)
- https://github.com/letta-ai/letta (~24,601★) · https://github.com/titanwings/distilly (~24,317★)
- https://github.com/guillaumemeyer/watermarks-remover (~20,265★) · https://github.com/firecrawl/anydoc (~20,189★)
- https://github.com/HKUDS/DeepCode (~16,481★) · https://github.com/yc-software/qm (~14,528★)
- https://github.com/awesome-dsh-plugin/awesome-dsh-plugin (~14,353★) · https://github.com/lsdefine/GenericAgent (~14,114★)
- https://github.com/pathwaycom/arc-task-gen (~10,422★) · https://github.com/trycompai/crm (~9,561★)
- https://github.com/MoonshotAI/Kimi-K3 (~8,700★, created 2026-07-27) · https://github.com/FareedKhan-dev/kimi-k3-in-c (~7,061★)
- https://github.com/sapientinc/PRAXIST (~6,909★, created 2026-08-27) · https://github.com/genspark-ai/genoffice (~4,800★)
- https://github.com/microsoft/skill-recorder (~3,806★, created 2026-07-29)

---

## Short Compilation Note

Compiled September 3, 2026 (America/Los_Angeles). The arXiv material comes from the **September 2 announcement batch** (cs.AI, cs.CL, and cs.LG recent listings; IDs 2609.024xx–028xx), with abstracts fetched directly via the arXiv API. GitHub star counts and repository metadata were verified live against the GitHub REST API at compilation time, and news items are from TechCrunch's AI feed for September 1–3. All preprint results are author-reported and not independently peer reviewed. Theme of the day: **the stack consolidates while the skill layer professionalizes** — Nvidia swallowed Hugging Face for $12.9B just as the US government de-risked pretraining on copyrighted data; OpenAI put an "opaque-recurrence" model across its critical cybersecurity threshold while safety experts watched the monitorability cost; and on the research side, the best post-training + test-time compute system beat the top human at IOI 2026, while skill distillation (AREX), auditable harness safety co-evolution (SafeEvolve), model-controlled attention (DA), and reward-coverage theory (Coverage, Not Targeting) each moved agent engineering from vibes to measured baselines.
