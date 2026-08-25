# 🔬 Agentic AI & Generative AI Research Report — August 25, 2026

*Compiled August 25, 2026 (America/Los_Angeles) from freshly submitted arXiv records (August 23–24, 2026 batches), linked project repositories, and live GitHub API records verified on the day of compilation. The research findings below are author-reported preprint results and have not been independently peer reviewed.*

---

## Top 5 Latest Advancements

### 1. Prime Agent: A Self-Improving RLM Harness

**What happened:** *Prime Agent* (arXiv:2608.23552) is an open-source harness for long-horizon evaluation and coding-agent workflows. A persistent IPython REPL implements the Recursive Language Model (RLM) abstraction for programmatic context processing and test-time compute; a *Continual Harness* preserves histories, memories, skills, prompts, and subagent specifications across trajectories; recursive subagents coordinate through direct agent-to-agent communication; and an *Agents View* daemon lets humans inspect and manage sessions. The harness standardizes execution, recovery, verification, and resource accounting while leaving strategy construction to the model — an expressive "membrane" that keeps harness failures from becoming model failures. On ARC-AGI-3 it raises RHAE Best@1 from 30% to 95.5% and matches or exceeds native and popular harnesses across long-context coding, GPU-kernel generation, emulator construction, and autonomous nanoGPT speedruns. On Factorio, refinement enables continuous technology progression and dedicated subagents enable parallelized work. Code: https://github.com/PrimeIntellect-ai/prime-agent (already ~18.3k stars at compilation time).

**Why it matters:** This is strong evidence that a large share of "agentic capability" lives in the membrane between model and environment: one shared REPL plus persistent skill/memory state plus recursive subagents closes a ~65-point gap on long-horizon tasks without touching weights. It also operationalizes self-improvement at the harness level — the system grows by accumulating and refining artifacts across runs rather than by updating weights — and the open release gives every lab a reference for harness engineering as a first-class research object.

**Source:** https://arxiv.org/abs/2608.23552

---

### 2. AutoSaddler: Automatic Harness Optimization with Durable Updates from Agent Execution Traces

**What happened:** *AutoSaddler* (arXiv:2608.23041) formulates harness improvement as an offline learning problem: given failure signals from mini-batches of agent execution traces, it iteratively updates the harness using (1) failure-trace diagnosis, (2) structured patch generation that treats the harness as code, and (3) validation-based update selection. On GAIA2, SWE-Bench Pro, and Terminal-Bench 2.0 it improves agent performance over the corresponding base harnesses by **+9.0, +9.6, and +10.0 percentage points** respectively. Ablations identify three ingredients of effective harness optimization: deep debugging rather than shallow reflection, targeted modifications rather than unconstrained editing, and generalization-aware selection rather than trajectory-specific repair. Project: https://aka.ms/AutoSaddler-website

**Why it matters:** Harness design — the search over prompts, tool configurations, and control logic — was the manual bottleneck of agent engineering. AutoSaddler closes the loop automatically: mine failure traces, emit code patches against the harness, and keep only updates that generalize. Together with Prime Agent (this week) and Task-CoEvolve (last week), it establishes harness optimization as its own subfield with reproducible recipes — the agent stack is now being tuned by the agent stack itself.

**Source:** https://arxiv.org/abs/2608.23041

---

### 3. InjecMEM: Memory Injection Attack on LLM Agent Memory Systems

**What happened:** *InjecMEM* (arXiv:2608.23471, accepted at COLM 2026) is a memory-injection attack paradigm that requires only a **single interaction — no read/edit access to the memory store —** to steer later responses of related queries toward a pre-specified output. Guided by the retrieval-then-generate mechanism of memory systems, it crafts (a) a retriever-agnostic *anchor* containing high-recall topical cues so downstream retrieval consistently associates the record with the target topic, and (b) an *adversarial command* learned via gradient-based coordinate search, averaged over synthetic prompt templates and insertion positions, so it stays effective under uncertain fused contexts, variable placements, and long prompts. Evaluated across multiple memory systems and backbone models, InjecMEM achieves reliable topic-conditioned retrieval and targeted generation, remains effective under memory drift, transfers across backbones, and leaves non-target queries unaffected.

**Why it matters:** Persistent memory is becoming a default subsystem of deployed agents (personalization, continuity), and this paper shows memory is an attack surface, not just a capability. A single benign-looking interaction plants a trigger that later fires on topically related queries — a stealthier failure mode than prompt injection because it persists after the attacker leaves. It is a concrete hardening requirement for any agent that keeps memories: treat stored records as untrusted input at retrieval time, and adopt the released framework as a red-team baseline.

**Source:** https://arxiv.org/abs/2608.23471

---

### 4. SkillAlchemy: Open-World Agent Skill Creation

**What happened:** *SkillAlchemy* (arXiv:2608.23417) tackles **open-world skill creation**: given an underspecified skill brief and a source-access specification, a creator must discover behavior-relevant requirements omitted by the brief and determine how broadly each source-derived procedure is justified. The proposed framework is admission-centered: it identifies implicit requirements through contrastive evidence, admits candidate procedures based on evidence-supported scope, and compiles admitted content into a grammar-guided skill package. Across 87 SkillsBench v1.1 tasks, SkillAlchemy improves pass rate by **19.9 percentage points over no-skill execution** and **8.6 percentage points over the strongest automated baseline**, reaching performance comparable to human-curated skills.

**Why it matters:** Skills are the fastest-growing unit of agent extensibility (see also this week's "Signal or Noise?" web-dev skills benchmark). SkillAlchemy attacks the human-authorship bottleneck and shows reliable skills can be mined from open-world materials when scoping is made explicit. The admission-centered design — evidence in, justified scope out, compiled package — is a reusable template for any pipeline that turns documents into agent capabilities.

**Source:** https://arxiv.org/abs/2608.23417

---

### 5. The Interaction Tax: When Communication Erases Diversity in Multi-Agent Teams

**What happened:** *The Interaction Tax* (arXiv:2608.23541, accepted at ICML 2026) resolves part of the multi-agent debate by distinguishing types of communication: different model families find structurally different solutions, but when agents read each other's **complete outputs, their proposals converge within one round**, erasing the diversity that motivated using multiple models. Across 11 verifier-scored optimization tasks under matched budgets, full-solution interaction is a weak default and independent proposal generation avoids the collapse. Full-solution interaction mainly makes agents stay close to the first solution they see instead of trying different approaches, and critique helps only when the violated rule is easy for the LLM to find and fix.

**Why it matters:** This gives the contradictory multi-agent literature a mechanistic account: performance depends less on the number of agents than on the *information they exchange*. The practical prescription is cheap — default to independent generation, share only what other outputs need, and reserve communication for targeted critique of checkable rules. For teams building multi-agent stacks, it turns "debate more" folklore into a budgeted design decision.

**Source:** https://arxiv.org/abs/2608.23541

---

## New Use Cases

- **Million-scale optical-link fault management in production AIDCs (arXiv:2608.23145):** The first LLM-powered multi-agent system for autonomous fault management across millions of optical links in production AI data centers. Refined via SFT and continuous memory evolution, it achieves **97.7% F1 and over 60% fault-incident reduction**, outperforming SOTA LLM baselines on a ten-week field-data evaluation — a rare report of a fully deployed agent system at carrier/infrastructure scale, measured in the field rather than on a benchmark.
- **Process-constrained self-evolution for evidence-grounded clinical interaction (MediSkill-Evo, arXiv:2608.23397):** A clinical agent that evolves governed process knowledge **without backbone fine-tuning**: four typed banks (clinical skills, process rules, symbolic schemas, measurement procedures) with provenance, support, replay, and controller-defined safety checks governing publication to a frozen test-time snapshot; a Process-Constrained Preference Harness binds evidence to its source, rejects controller-invalid candidates, and ranks actions with a safety-prioritized Clinical Process Critic. On 300 held-out encounters it improves diagnosis accuracy 61.33% → 69.00%, treatment-intent coverage 33.62% → 66.44%, and cuts automatically scored critical failures from 31.00% to 16.33% versus AgentClinic.
- **EarthVerse: scientific agents across dynamic Earth systems and natural hazards (arXiv:2608.23525):** A benchmark of 405 reproducible package-scoped tasks grounded in 199 documented events across 19 hazard families. Agents must inspect heterogeneous evidence, choose compatible data, execute transparent calculations, reconcile source differences, and preserve provenance. Executable ground truth decomposes each task into fine-grained answer units with task-specific rubrics that allow multiple valid paths. Across 25 evaluated systems, the best mean answer-unit accuracy is 84.65% but the highest Strict@95 is only 34.81% — agents complete individual steps without holding a consistent chain across evidence, scales, units, and physical interpretation.
- **CyberFactory: scaling agentic cybersecurity training from real CVEs (arXiv:2608.23181):** A unified open-source framework that transforms public vulnerability artifacts (CVEs from the wild) into executable, verifiable task instances for PoC generation, vulnerability patching, and cybersecurity QA. A reusable vulnerability-analysis skill guides a teacher through source inspection, domain-prior problem solving, and evidence-based validation; the resulting *agentic* trajectories — the model interacts with tools and target environments and revises per execution feedback — train **Aegis**, which internalizes the skill without needing it at inference. Aegis reaches 52.4% Pass@1 on CyberGym under a one-hour budget (+22.8 points over its Qwen 3.5 base), an open recipe for security-domain agent post-training.
- **ReWorld: real-time interactive world models with long-horizon memory (arXiv:2608.23565, project: https://zhifeichen097.github.io/ReWorld/):** An interactive world model that follows user actions, remembers places it has shown, and streams in real time. Mixed per-head attention windows confine most heads to the recent past while a small set of global heads attends over the entire history; a pose-indexed landmark bank under a fixed KV budget retrieves landmarks nearest the current pose; and a metric-scale-aligned data engine (eight sources: Unreal fly-throughs, game roaming, real footage) puts all content on one physical action scale. LoRA-confined distribution-matching distillation compresses sampling to four steps, streaming 704×1280 video. Against six recent interactive world models it attains the best control fidelity (11.95° rotation error) and best generation quality, and on minute-long out-and-back rollouts (64 s) its fixed 12-chunk cache still regenerates the starting view — the regime where sliding windows have evicted the evidence.

---

## Top Rated GitHub Projects Leveraging Agentic/Gen AI

GitHub repository records were checked through the API on August 25, 2026. Stars and latest-push timestamps are point-in-time observations and can change. This table is a curated ranking of highly starred, active repositories directly useful for agent construction or operation; it is not a claim about software quality or an exhaustive ranking of every AI repository.

| Rank | Project | Stars observed | Latest push observed (UTC) | Agentic/GenAI role |
|---:|---|---:|---|---|
| 1 | [openclaw/openclaw](https://github.com/openclaw/openclaw) | 387,575 | 2026-08-25 | Personal AI assistant — any OS, any platform; still the most-starred agentic project. |
| 2 | [obra/superpowers](https://github.com/obra/superpowers) | 277,433 | 2026-08-19 | Agentic skills framework & software development methodology. |
| 3 | [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) | 236,299 | 2026-08-25 | Extensible personal agent with tools, skills, memory, and autonomous workflows. |
| 4 | [n8n-io/n8n](https://github.com/n8n-io/n8n) | 202,384 | 2026-08-25 | Fair-code workflow automation platform with native AI capabilities; visual building plus custom code. |
| 5 | [Significant-Gravitas/AutoGPT](https://github.com/Significant-Gravitas/AutoGPT) | 186,857 | 2026-08-25 | Accessible autonomous agent platform — build, run, and share AI agents. |

Notable new entrant this week: [PrimeIntellect-ai/prime-agent](https://github.com/PrimeIntellect-ai/prime-agent) (self-improving RLM agent, see Top 5 #1) reached ~18,345 stars within days of release.

---

## Sources with Working URLs

Every URL below returned HTTP 200 during compilation on August 25, 2026.

### Fresh research (August 23–24, 2026 arXiv batches)

- Prime Agent: A Self-Improving RLM Harness — https://arxiv.org/abs/2608.23552
- AutoSaddler: Automatic Harness Optimization with Durable Updates from Agent Execution Traces — https://arxiv.org/abs/2608.23041
- InjecMEM: Memory Injection Attack on LLM Agent Memory Systems — https://arxiv.org/abs/2608.23471
- SkillAlchemy: Open-World Agent Skill Creation — https://arxiv.org/abs/2608.23417
- The Interaction Tax: When Communication Erases Diversity in Multi-Agent Teams — https://arxiv.org/abs/2608.23541
- First Demonstration of Multi-Agent LLM System for Million-Scale Optical Link Management in Global Production AIDCs — https://arxiv.org/abs/2608.23145
- MediSkill-Evo: Process-Constrained Self-Evolution for Evidence-Grounded Clinical Interaction — https://arxiv.org/abs/2608.23397
- EarthVerse: Benchmarking Scientific Agents Across Dynamic Earth Systems and Natural Hazards — https://arxiv.org/abs/2608.23525
- CyberFactory: Scaling Cyber Security Capabilities with Instances from the Wild — https://arxiv.org/abs/2608.23181
- ReWorld: An Interactive World Model with Long-Horizon Memory — https://arxiv.org/abs/2608.23565

### Additional notable submissions

- How to Train a Critic Stably and Efficiently (BPCO) — https://arxiv.org/abs/2608.23566
- SRPO: Self-Reflective Policy Optimization for Long-Horizon Reasoning — https://arxiv.org/abs/2608.23493
- SWE Refactor Bench: Can Coding Agents Complete a Long-Horizon, Whole-Repository Stack Migration? — https://arxiv.org/abs/2608.23564
- Agent-G2: Gaussian Guidance for Agentic Reinforcement Learning — https://arxiv.org/abs/2608.23318
- CatchBench: When Can an Agent Failure Be Caught? — https://arxiv.org/abs/2608.22808
- Signal or Noise? A Benchmark Study of Agent Skills in Web Development — https://arxiv.org/abs/2608.23067
- Apodex 1.1: Scaling Agentic Intelligence for Complex Work — https://arxiv.org/abs/2608.23283

### GitHub project records

- OpenClaw — https://github.com/openclaw/openclaw
- Superpowers — https://github.com/obra/superpowers
- Hermes Agent — https://github.com/NousResearch/hermes-agent
- n8n — https://github.com/n8n-io/n8n
- AutoGPT — https://github.com/Significant-Gravitas/AutoGPT
- Prime Agent (new this week) — https://github.com/PrimeIntellect-ai/prime-agent

### Paper-linked code and project pages (verified live)

- Prime Agent — https://github.com/PrimeIntellect-ai/prime-agent
- BPCO / golden_critic — https://github.com/QPHutu/golden_critic
- SRPO — https://github.com/Galleons2029/SRPO
- Agent-G2 — https://github.com/ZJU-REAL/Agent-G2
- CatchBench (code and data) — https://github.com/yzhao062/catchbench
- World-model-as-simulator survey project page — https://github.com/AtongWang/world-model-simulators
- Jiuge-Tuiqiao (code and demo) — https://github.com/jiangli-va/Jiuge-Tuiqiao
- ReWorld project page — https://zhifeichen097.github.io/ReWorld/
- AutoSaddler website — https://aka.ms/AutoSaddler-website

### Date-sorted arXiv AI discovery feed

- Fresh submissions: https://export.arxiv.org/api/query?search_query=cat%3Acs.AI&sortBy=submittedDate&sortOrder=descending&max_results=20

---

## Short Compilation Note

This report is materially new relative to August 21, 2026: it replaces the August 20 arXiv batch (AI4AI-Bench, MidTool, Break It Down Pass It On, Task-CoEvolve, Phantom Gains) with freshly submitted work from August 23–24 — an open-source **self-improving RLM harness** (Prime Agent) that lifts ARC-AGI-3 RHAE Best@1 from 30% to 95.5% without touching weights, an **automatic harness optimizer** that mines failure traces into durable code patches (AutoSaddler, +9.0 to +10.0 pp on GAIA2 / SWE-Bench Pro / Terminal-Bench 2.0), a **single-interaction injection attack** that turns agent memory into a persistent attack surface (InjecMEM), **source-grounded open-world skill creation** that reaches human-curated parity (SkillAlchemy), and a mechanistic account of when **multi-agent communication erases the diversity** it was supposed to buy (Interaction Tax, ICML 2026). Today's practical theme is the **harness-and-skill layer becoming self-improving and auditable**: the model stays fixed while the membrane — REPL, memory, skills, subagents, control logic — accumulates and refines itself across runs, and memory is simultaneously exposed as the new attack vector. On the applied side, the first field-deployed multi-agent system for **million-scale optical-link fault management** in production AIDCs (97.7% F1, >60% fault-incident reduction), a **process-constrained self-evolving clinical agent** that cuts critical failures nearly in half, **EarthVerse** exposing that scientific agents rarely hold a consistent evidence chain across 405 hazard tasks, a **CVE-to-trajectory pipeline** (CyberFactory/Aegis) that open-sources agentic cybersecurity post-training, and **ReWorld** streaming real-time interactive video with pose-indexed long-horizon memory. The top-rated GitHub ranking holds at the same five projects (star counts updated); the week's notable new entrant is PrimeIntellect-ai/prime-agent, already at ~18.3k stars within days of release.
