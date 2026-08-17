# 🔬 Agentic AI & Generative AI Research Report — August 17, 2026

*Compiled August 17, 2026 (America/Los_Angeles) from freshly submitted primary arXiv records (August 14, 2026 batch), linked project repositories, and live GitHub API records verified on the day of compilation. The research findings below are author-reported preprint results and have not been independently peer reviewed.*

---

## Top 5 Latest Advancements

### 1. Twin: Playing an Unknown Game with a Test-Time Digital Twin

**What happened:** *Twin: Playing an Unknown Game with a Test-Time Digital Twin* presents a Test-time World-model Inference system in which a **frontier coding agent writes an executable world model** for completing continual-learning tasks such as ARC-AGI-3 games. Each game hides its rules and goal; the system constructs them from simulation and interaction alone, without hand-engineered per-task designs. Its inductive prior over grid games is strong enough to recover the true transitions of the game and the goal on nearly all levels, with replay validation happening inside the twin world model — a harness enforces that an action is not executed until it has been validated against the learned model.

**Why it matters:** The agent's deliverable is no longer just code for the task but a *verified model of the environment itself*. Writing, simulating in, and replaying against a self-authored world model before acting is a concrete pattern for reducing real-world trial-and-error cost — and a strong signal that test-time compute spent on modeling (not just solving) is where robustness comes from.

**Source:** https://arxiv.org/abs/2608.14490v1

---

### 2. Marionette: Predicting World States, Rendering Geometry, Painting Appearance

**What happened:** *Marionette* attacks the core fragility of interactive game world models that autoregress visual observations directly in pixel or latent space: structured properties such as pose, geometry, and occlusion must be implicitly maintained by the same generative sequence, so errors accumulate over long horizons. Marionette instead **explicitly models the evolving world state**, delegates exact geometric computation to a fixed, zero-parameter renderer, and leaves the neural model only with synthesizing appearance — separating what must be exact from what can be learned.

**Why it matters:** This is a design principle for generative systems in general: route deterministic structure through deterministic machinery and reserve learned generation for appearance-level synthesis. For interactive video, robotics previews, and simulation content, it targets the long-horizon consistency failure that purely neural world models still struggle with.

**Source:** https://arxiv.org/abs/2608.14530v1

---

### 3. Handover of In-Context Learning State Across Session Boundaries

**What happened:** *Handover of In-Context Learning State Across Session Boundaries* studies what must be transferred when an LLM task continues in a new session — because context hit the input limit, the application restarted, or another agent was asked to finish the job. The authors formulate handover as **transfer of a task-relative in-context learning (ICL) state** and distinguish exact recovery of earlier material from preservation of the target distribution, analyzing both under an exogeneity assumption about how sessions are partitioned.

**Why it matters:** Multi-session and multi-agent pipelines are now standard, but "what do we pass on?" has been treated as an engineering afterthought. A formal account of ICL-state handover gives agent frameworks a principled basis for compaction, summarization, and agent-to-agent delegation — deciding what to carry forward by the distribution it preserves rather than by raw text overlap.

**Source:** https://arxiv.org/abs/2608.14528v1

---

### 4. Wyvern: An Agentic Framework for Generating Grounded Multimodal Reports

**What happened:** *Wyvern* is a multi-agent framework for the automated generation of **grounded, multimodal technical reports**. It integrates images, tables, and text with supporting references in a unified report, with particular emphasis on grounding — countering the tendency of generative models to synthesize fluent but unanchored content as knowledge growth outpaces human review capacity.

**Why it matters:** Report generation is one of the highest-volume agentic workloads (research briefs, engineering docs, market analyses), and its failure mode is silent: plausible text with no traceable evidence. A framework that treats grounding — every claim tied to a reference, every figure tied to data — as a first-class architectural property is directly applicable to production content pipelines.

**Source:** https://arxiv.org/abs/2608.14446v1

---

### 5. PACE-Bench: Benchmarking Physics Adaptation via Code Evolution in Dynamic Environments

**What happened:** *PACE-Bench (Physics Adaptation via Code Evolution)* introduces a simulator-grounded benchmark of **144 source-to-target adaptation pairs across six physics domains**. Each pair links a source environment to a mutated target environment with the same goal and interface: a code-driven design that succeeds in the source fails in the target, where agents must iteratively adapt. This directly tests recovery after execution conditions change — something existing self-evolving-agent evaluations, which optimize under fixed conditions, do not measure.

**Why it matters:** Self-improving agents are usually evaluated on whether they improve; PACE-Bench asks the harder question — *do they survive when the world changes underneath them?* That is the property that determines whether an agent can be trusted in long-running deployments where environments drift, APIs change, and physics parameters shift.

**Source:** https://arxiv.org/abs/2608.14441v1

---

## New Use Cases

- **Agentic spreadsheet reasoning with hierarchical relation graphs (SheetCompass, arXiv:2608.14452):** Real workbooks contain implicit cross-table associations, fine-grained column dependencies, and spatial layouts that flattening into sequential strings destroys. SheetCompass builds hierarchical relation graphs preserving intra-sheet boundaries and inter-sheet semantics so LLMs can exploit the global spatial context human experts use — a practical upgrade for finance/ops agents operating on live workbooks.
- **Separating evidence interpretation from decision aggregation (arXiv:2608.14509):** Multi-source reasoning systems usually concatenate everything into one prompt, conflating two operations with different requirements. A four-field evidence tuple — hypothesis, reliability bucket, rationale, provenance — fixes the interface between an interpreting stage (which rewards capacity and context) and a combining stage (which rewards fixed arithmetic and comparability), and exposes failure modes invisible in end-to-end scores.
- **Statistically certified safety-neuron refusal triggering (Tripwire, arXiv:2608.14392):** Neuron-level jailbreak defenses typically either erase distributed harmful semantics at a large intervention footprint or rely on external classifiers with compounding errors. Tripwire triggers aligned refusal through statistically *certified* safety neurons — finer-grained defense with quantified guarantees and less utility loss, a template for production guardrail design.
- **AI-generated crisis video detection under social dissemination (RA-Bench, arXiv:2608.14391):** A benchmark of 17,886 videos using real footage as anchors evaluates how detectability varies with generation conditions, how people perceive generated depictions of wars and disasters, and whether detectors remain reliable *after* social dissemination degrades quality — the setting where misinformation actually spreads.
- **Precision-based adaptive stopping for LLM evaluations (optstop, arXiv:2608.14425):** Fixed sampling budgets waste compute on items whose estimates are already precise. optstop treats evaluation as sequential measurement with hierarchical Bayesian inference — keep sampling where uncertainty is high, stop where it is not — supporting binary, ordinal, and continuous outcomes live or retrospectively, without a calibrated item bank.
- **Power Sampling paradox: verifier-free sharpening can backfire (arXiv:2608.14420):** Power Sampling sharpens a model's distribution over complete trajectories as a verifier-free inference-time improvement — yet it can drive *more* probability mass toward correct trajectories while degrading downstream accuracy by up to 18.5 percentage points in self-consistency settings. Inference-time scaling knobs need per-pipeline validation, not blanket adoption.

---

## Top Rated GitHub Projects Leveraging Agentic/Gen AI

GitHub repository records were checked through the API on August 17, 2026. Stars and latest-push timestamps are point-in-time observations and can change. This table is a curated ranking of highly starred, active repositories directly useful for agent construction or operation; it is not a claim about software quality or an exhaustive ranking of every AI repository.

| Rank | Project | Stars observed | Latest push observed (UTC) | Agentic/GenAI role |
|---:|---|---:|---|---|
| 1 | [openclaw/openclaw](https://github.com/openclaw/openclaw) | 386,526 | 2026-08-17 | Personal AI assistant — any OS, any platform; still the most-starred agentic project. |
| 2 | [obra/superpowers](https://github.com/obra/superpowers) | 273,107 | 2026-08-13 | Agentic skills framework & software development methodology. |
| 3 | [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) | 231,885 | 2026-08-17 | Extensible personal agent with tools, skills, memory, and autonomous workflows. |
| 4 | [n8n-io/n8n](https://github.com/n8n-io/n8n) | 200,961 | 2026-08-17 | Fair-code workflow automation platform with native AI capabilities; visual building plus custom code. |
| 5 | [Significant-Gravitas/AutoGPT](https://github.com/Significant-Gravitas/AutoGPT) | 186,641 | 2026-08-17 | Accessible autonomous agent platform — build, run, and share AI agents. |

---

## Sources with Working URLs

Every URL below returned HTTP 200 during compilation on August 17, 2026.

### Fresh research (August 14, 2026 arXiv batch)

- Twin: test-time digital twin world models — https://arxiv.org/abs/2608.14490v1
- Marionette: state prediction + zero-parameter geometry rendering — https://arxiv.org/abs/2608.14530v1
- Handover of in-context learning state across session boundaries — https://arxiv.org/abs/2608.14528v1
- Wyvern: agentic grounded multimodal report generation — https://arxiv.org/abs/2608.14446v1
- PACE-Bench: physics adaptation via code evolution — https://arxiv.org/abs/2608.14441v1
- SheetCompass: hierarchical relation graphs for agentic spreadsheet reasoning — https://arxiv.org/abs/2608.14452v1
- Split the Labor: evidence interpretation vs. decision aggregation — https://arxiv.org/abs/2608.14509v1
- Tripwire: statistically certified safety neurons — https://arxiv.org/abs/2608.14392v1
- RA-Bench: AI-generated crisis video detection under dissemination — https://arxiv.org/abs/2608.14391v1
- optstop: Bayesian optimal stopping for LLM evaluations — https://arxiv.org/abs/2608.14425v1
- Power Sampling paradox in verifier-free inference-time scaling — https://arxiv.org/abs/2608.14420v1

### GitHub project records

- OpenClaw — https://github.com/openclaw/openclaw
- Superpowers — https://github.com/obra/superpowers
- Hermes Agent — https://github.com/NousResearch/hermes-agent
- n8n — https://github.com/n8n-io/n8n
- AutoGPT — https://github.com/Significant-Gravitas/AutoGPT
- Firecrawl — https://github.com/firecrawl/firecrawl

### Date-sorted arXiv AI discovery feed

- Fresh submissions: https://export.arxiv.org/api/query?search_query=cat%3Acs.AI&sortBy=submittedDate&sortOrder=descending&max_results=20

---

## Short Compilation Note

This report is materially new relative to August 16, 2026: it replaces the August 13 arXiv batch (Mimir v1, OmniScientist, Vero, Synthetic Persona Pretraining, AutoDesign) with freshly submitted work on **test-time world-model construction** (Twin), **state–geometry–appearance separation in interactive generation** (Marionette), **ICL-state handover across session boundaries**, **grounded multimodal report agents** (Wyvern), and **adaptation under environment mutation** (PACE-Bench). Today's practical theme is **verify before you act**: build an executable model of the world and replay against it before executing, route deterministic structure through deterministic machinery, carry forward what a handover preserves rather than what it repeats, tie every generated claim to a reference, and test whether agents recover when the rules change — while the Power Sampling paradox reminds us that inference-time sharpening must be validated per pipeline.
