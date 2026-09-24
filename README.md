# 🔬 Agentic AI & Generative AI Research Report — Thursday, September 24, 2026

*Compiled Thursday, September 24, 2026 (America/Los_Angeles) from a fresh Sept 23–24 news pass (Anthropic Science blog, Al Jazeera, Z.ai / Hugging Face / Axios, Tech Startups funding roundups, Linux Foundation / OpenAI / InfoQ / TechCrunch, The Hindu, The Japan Times, Reuters, WSJ) and live GitHub REST API star counts re-verified at compilation time. Preprint, startup, and funding figures below are as reported by the cited outlets and not independently peer reviewed. This is a materially new report: today's anchor is **Anthropic disclosing that Claude autonomously discovered a novel, previously uncharacterized enzyme system with CRISPR-like DNA repeats ("array-associated reverse transcriptases," ART) — its first in-house biology discovery, made by ~950 Claude agents in ~21 hours / 210M tokens with only high-level direction from human scientists — landing the same day Z.ai shipped the full 753B-parameter GLM-5.3 open weights (a cyber-capable, ~40B-active MoE) and a dense Sept 23–24 funding wave (Cyera $400M, Tekever $580M, Enveda $311M, Snorkel $350M, Basecamp Research $140M, biosecurity startup Pilgrim $25M) all flowed through the newly formalized Agentic AI Foundation (MCP + AGENTS.md + goose under the Linux Foundation).*

---

## Top 5 Latest Advancements

### 1. Anthropic: Claude Autonomously Discovers a Novel CRISPR-Like Enzyme System (Today's Big One)

**What happened:** **Anthropic published (Sep 23, with coverage breaking Sep 24) the first results from a new in-house biology research program in which Claude autonomously discovered a previously uncharacterized enzyme system.** The team built its own lab and a single team spanning "training Claude in biology to running experiments in the lab," giving Claude a high-level prompt to mine a massive database of DNA sequences for interesting new reverse transcriptases (RTs). **After ~21 hours of searching using roughly 950 agents and ~210 million tokens**, one agent spotted a repeating array of DNA sequences next to an "odd-looking" RT gene — "a CRISPR-like repeat array" — and, working much like a human scientist, counted the repeats, measured their spacing, compared the layout to known RT systems, and searched the literature before filing a report for human review. The system, which Anthropic calls **array-associated reverse transcriptases (ART)**, is found mainly in bacteriophages and consists of three parts: an RT, a partner gene beside it, and a long array of evenly spaced DNA repeats that resembles a CRISPR array. The underlying RT (found in a jumbo phage) had been identified before, but **Claude appears to be the first to notice the system's defining features** — the associated non-coding DNA repeat array and an accessory protein of unknown function. Anthropic has released a **preprint**; MIT/Broad CRISPR pioneer **Feng Zhang** called it "an exciting example of how AI agents can contribute to biological discovery."

**Why it matters:** This is the clearest demonstration yet that **frontier agents can do genuine, novel scientific discovery** — not just summarize or automate, but surface a previously unknown biological system that "has only ever been found together in a handful of other systems, all of which are programmable and perform operations like cutting, copying, and pasting DNA." The ART discovery reframes the AI-for-science race from "can a model pass a biology exam" to **"can an agent + wet-lab pipeline produce a paper-grade, experimentally-validated discovery that no human had made"** — the same axis the labs have flagged (and Amodei's "machines of loving grace" framing) as the path to compounding returns. It also pairs with Anthropic's **Life Sciences Verification Program** (refined, more permissive biology safeguards for Claude Mythos/Opus/Sonnet) as a signal that the company is building a durable, safety-gated science vertical, not a one-off demo.

**Sources:** https://www.anthropic.com/news/claude-discovers-novel-enzyme-system · https://www.aljazeera.com/economy/2026/9/24/ai-model-claude-discovers-crispr-like-enzyme-system-anthropic-says · https://www.trendingtopics.eu/anthropic-claude-crispr-like-enzyme-system/

---

### 2. Z.ai Ships Full GLM-5.3 Open Weights — a Cyber-Capable 753B MoE (Not MIT This Time)

**What happened:** **Z.ai has published the full open weights for its flagship GLM-5.3 on Hugging Face (zai-org/GLM-5.3), making good on the release it delayed in August over safety concerns.** The model is a **~753B-parameter mixture-of-experts (~40B active per token) with a 1M-token context window and 128K max output**, in BF16 and FP8 safetensors (~755GB across 141 shards), built on the same base as GLM-5.2 with **every gain from post-training** (about a month of extra RL on long-horizon tasks). Headline capability: it is **the most capable open-weights model for coding** — Terminal-Bench 3.0 jumping from 4.6 (5.2) to 28.3, DeepSWE 46.2 → 66.9, ~50% better on Z.ai's in-house code benchmark, and open-source SOTA on Terminal-Bench 3.0 and Agents' Last Exam. The **cyber numbers that triggered the hold are now published openly**: CyberGym at 84.5 (beating Anthropic's Fable 5 and OpenAI's GPT-5.6 Sol), ExploitBench more than doubling from 24.4 to 54.4. It runs day-one on vLLM/SGLang with OpenAI-compatible endpoints and is served on OpenRouter. The catch is the license: unlike the MIT-licensed GLM-5.2 and GLM-5.3-Flash, the flagship ships under a **custom "GLM-5.3 License"** — effectively unrestricted for individuals and startups, but **any Model-as-a-Service business clearing $10B in revenue over any 12 months must pass Z.ai's security review** before commercial use.

**Why it matters:** This is **the most capable open-weights *cyber-offensive* model released to date, freely downloadable** — a meaningful shift for both defenders and attackers, and it lands under a new licensing posture that explicitly targets hyperscalers/neoclouds, signaling that China's open-weight labs are now writing the terms of engagement for the frontier. It extends this month's open-weights compression (Xiaomi MiMo-V2.6, GLM-5.2) and makes the "self-host a frontier-class agentic coding + security model" playbook fully real on a single multi-GPU box or a 256GB-RAM workstation via community quants.

**Sources:** https://z.ai/blog/glm-5.3 · https://curiouslm.com/blog/glm-5-3-open-weights-released · https://nowline.net/reports/z.ai-opens-glm-5.3-s-full-753b-weights-%E2%80%93-not-mit-this-time · https://www.axios.com/2026/08/14/china-open-source-ai-glm-53

---

### 3. A Dense AI Funding Wave: Tekever $580M, Cyera $400M, Snorkel $350M, Enveda $311M, Basecamp Research $140M, Pilgrim $25M

**What happened:** A **Sept 23–24 funding cluster** pushed capital into autonomous systems, data/RL infrastructure, AI-designed biotech, and biosecurity. **Tekever** (Portuguese-British autonomous-defense) raised a **$580M Series D** first close (UC Investments, Baillie Gifford) at a **$6.4B** valuation for AI-enabled autonomous aircraft with operational experience in Ukraine. **Cyera** pulled **$400M** from Goldman Sachs Growth Equity (on top of a $1B Series G at $12B) to secure data and AI-agent access across the enterprise. **Snorkel AI** raised **$350M at a $3.5B valuation** (Insight Partners, S32) to become the data/RL-environment supplier behind frontier models, with Reuters reporting annualized revenue above $350M (vs ~$20M a year earlier). **Enveda** (Boulder) closed a **$311M Series E** at ~$2B to industrialize AI-discovered natural-product drug discovery. **Basecamp Research** raised an oversubscribed **$140M Series C** (S32, Nvidia, Anthropic's Anthology Fund, NATO Innovation Fund, Rockefeller) for its "EDEN" biological foundation models and Trillion Gene Atlas. **Pilgrim** (Redwood City) raised a **$25M seed at a ~$150M valuation** for ARGUS, a ~50-lb airborne biological-threat detector — with Anthropic frontier-red-team leader **Logan Graham** and tech staffer **Sholto Douglas** investing personally.

**Why it matters:** Capital is concentrating on **what AI cannot easily replicate** — battlefield-deployed autonomy, proprietary biological data, and the data/RL substrate beneath frontier models — rather than on generic chatbot wrappers. The Pilgrim round is the standout tell: **frontier-lab security researchers are personally financing the biosecurity layer**, and the same week Anthropic's Claude made a biology discovery, money is flowing to the exact "AI + wet lab + safety" intersection. Combined with Crunchbase's record $510B H1 2026 (AI ≈ 80% of Q1 venture dollars), this is the clearest evidence yet that **the AI investment thesis has bifurcated into "the model" vs. "the defensible system around it."**

**Sources:** https://techstartups.com/2026/09/24/startup-funding-news-today-september-24-2026-50skills-byteask-pilgrim-kasvu-therapeutics-puxi-optoelectronics-more · https://techstartups.com/2026/09/23/venture-capital-startup-funding-roundup-september-23-2026-accel-jpmorgan-s32-t-rowe-price-y-combinator-more · https://techstartups.com/2026/09/22/venture-capital-startup-funding-roundup-september-22-2026-general-catalyst-goldman-sachs-greylock-m13-y-combinator-more

---

### 4. The Agentic AI Foundation (AAIF) Operationalizes Agent Interoperability — MCP, AGENTS.md, and goose Under the Linux Foundation

**What happened:** The **Agentic AI Foundation (AAIF)** — a directed fund under the Linux Foundation co-founded by **OpenAI, Anthropic, and Block**, with support from Google, Microsoft, AWS, Bloomberg, and Cloudflare — has moved from launch (Dec 2025) into **active working groups**. Its three founding projects — **Anthropic's Model Context Protocol (MCP), Block's goose agent framework, and OpenAI's AGENTS.md** — are now running under neutral governance, with AAIF standing up working groups on **Identity & Trust** (portable agent identity, delegation, cross-domain permissions), **Workflows & Process Integration** (handoff protocols, role definitions, state guarantees for multi-step business processes), and **Taxonomy & Landscape** (a shared glossary and ecosystem map). AGENTS.md — already adopted by **60,000+ open-source projects** including Codex, Cursor, Devin, Gemini CLI, GitHub Copilot, and VS Code (and now read as a fallback by Claude Code 2.1.277) — is being stewarded to prevent the agent tool surface from fragmenting.

**Why it matters:** This is the **infrastructure-layer consolidation of the agentic era** — the MCP/AGENTS.md/goose triad is becoming the "TCP/IP + DNS" of agents, and the working groups are the first serious attempt to standardize the things that actually block production: **agent identity, delegation, and handoff**. It matters for builders because the interoperability standards are being written *now*, in public, under a foundation no single vendor controls — a deliberate counter to "closed wall" proprietary agent stacks.

**Sources:** https://openai.com/index/agentic-ai-foundation/ · https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation · https://aaif.io/ · https://www.infoq.com/news/2025/12/agentic-ai-foundation/

---

### 5. Vertical-AI Funding Goes Physical and Proprietary: ByteAsk (C/C++ coding agents), AIONA (Japanese factory design knowledge), 50skills, Clastix (sovereign Kubernetes with Mistral)

**What happened:** A second wave of smaller Sept 24 rounds targets **vertical context as a moat**. **ByteAsk** (SF/Bengaluru, YC Fall 2026) raised **$1M pre-seed** to build coding agents for **C and C++** — the systems languages (aerospace, defense, robotics, HFT) where general web-trained agents struggle, including a post-trained C++ model. **AIONA** (Tokyo) secured **¥140M** to build REVY, an AI agent that captures the engineering design knowledge (FMEA/DRBFM, drawing checks, QFD) of retiring Japanese factory engineers. **50skills** (Reykjavík) raised **€5.3M** to orchestrate HR workflows between people and AI agents. **Clastix** (Naples) raised **€2.9M** with **Mistral** participating to build sovereign Kubernetes infrastructure. **Kasvu Therapeutics** (Helsinki) raised **€30M** for a non-hallucinogenic neuroplasticity drug, and **Langxi Technology** raised ~RMB200M to put silicon capacitors closer to AI chips.

**Why it matters:** The pattern is **AI as a component inside defensible, domain-locked businesses**, not a standalone product. The through-line — proprietary data, regulated workflows, physical/industrial context, and national-sovereignty constraints — is where the next generation of "AI companies" is being underwritten, and it's a direct complement to the big-lab model race: **the model layer commoditizes, the vertical moat compounds.**

**Sources:** https://techstartups.com/2026/09/24/startup-funding-news-today-september-24-2026-50skills-byteask-pilgrim-kasvu-therapeutics-puxi-optoelectronics-more

---

## Also Notable (Sept 23–24 window)

- **Alibaba's Zhenwu V900 chip and 5–10T-parameter Qwen roadmap** continue to drive the "full-stack, homegrown U.S. AI stack" narrative in China — the chip (T-Head, ~3× M890, clusters of up to 500K chips, mass production Q1 2027) plus a Qwen 4/4.5/5 roadmap toward "longer-horizon" tasks at 5–10T parameters, targeting 20+ GW of data-center capacity by 2032. (The Hindu / Japan Times)
- **Trump's UNGA "Superintelligence" rebrand and the U.S.–China AI incident hotline** remain live from Wednesday, with Treasury Bessent and China's He Lifeng holding further talks; the transatlantic governance rift (UN Guterres "responsible pacing" + EU regulation vs. U.S. executive-branch posture) is now structural. (Fortune / political.org)
- **The France-convened UN Security Council AI briefing** (Altman, Amodei, Hugging Face's Delangue, Bengio, with DeepSeek/Moonshot invited) continues to normalize AI as a standing great-power security matter. (Cointelegraph / The Print)
- **Z.ai's GLM-5.3-Flash** (320B-A18B, MIT) and the earlier **DeepSeek V4.1-Flash** ($0.003/M cached input) keep compressing the cost floor for self-hosted, frontier-class agentic workloads. (Z.ai / Stanford Tech Review)
- **Nvidia's "AGI has arrived" framing** (GPT-6 Astra trained on ~100K+ Grace Blackwell) vs. the ARC Prize co-founder's public dissent, and Anthropic researcher **Jacob Coxon's** viral "gambling with our lives" resignation, keep the AGI-debate thread active into this week. (Stanford Tech Review / TechCrunch)

---

## New Use Cases

1. **Autonomous wet-lab scientific discovery (new today).** Anthropic's ART discovery is the use case for **agent + lab pipelines that produce paper-grade, experimentally-validated novel biology** — the first time a frontier-lab agent is credited with discovering a previously uncharacterized enzyme system, with only high-level human direction.
2. **Open-weights cyber-offense as a commodity.** Z.ai's GLM-5.3 ships the most capable open-weights vulnerability-discovery/exploit model (CyberGym 84.5) freely downloadable — a new use case for **self-hosted, frontier-class security red-teaming and automated exploit generation** outside the closed-lab perimeter.
3. **Biosecurity early-warning as a funded category.** Pilgrim's ARGUS (airborne genomic biosurveillance, backed by Anthropic security researchers) is a new use case — **detecting dangerous pathogens circulating in the air before people get sick**, a direct hedge on the rising biological-capability risk from advanced AI.
4. **Agent identity, delegation, and handoff as production infrastructure.** The AAIF's Identity & Trust and Workflows & Process Integration working groups turn "how do agents authenticate, delegate, and hand off across systems" from a research question into a **standardized, interoperable capability** for multi-step business processes.
5. **Vertical context as a moat (systems code, factory engineering, HR, sovereign infra).** ByteAsk (C/C++), AIONA (Japanese factory design), 50skills (HR), and Clastix (sovereign Kubernetes with Mistral) are the use cases for **AI embedded in domain-locked, regulated, or national-sovereignty contexts** where the model is a component and the proprietary context is the product.

---

## Top Rated GitHub Projects Leveraging Agentic/Gen AI

Star counts and metadata **re-verified via the GitHub REST API at compilation time (Thursday, September 24, 2026)**. All figures are the live values as of this run.

| Project | Stars (Sept 24) | What it is |
|---|---|---|
| [deepseek-ai/deepseek-harness](https://github.com/deepseek-ai/deepseek-harness) | 235,001 | DeepSeek's "everything-is-a-plugin" agent harness |
| [anthropics/claude-code](https://github.com/anthropics/claude-code) | 147,921 | Claude Code — agentic coding tool in the terminal |
| [openai/codex](https://github.com/openai/codex) | 126,315 | Lightweight terminal coding agent; harness exposed via the Agents API |
| [punkpeye/awesome-mcp-servers](https://github.com/punkpeye/awesome-mcp-servers) | 95,479 | The canonical MCP server collection — the de facto map of the agent tool surface |
| [OpenHands/OpenHands](https://github.com/OpenHands/OpenHands) | 89,065 | AI-driven development / open agent for coding |
| [bytedance/deer-flow](https://github.com/bytedance/deer-flow) | 82,939 | Open-source long-horizon **SuperAgent** harness orchestrating sub-agents, memory, sandboxes, and skills |
| [microsoft/ai-agents-for-beginners](https://github.com/microsoft/ai-agents-for-beginners) | 75,584 | Microsoft's 18-lesson curriculum for building AI agents |
| [ChromeDevTools/chrome-devtools-mcp](https://github.com/ChromeDevTools/chrome-devtools-mcp) | 52,564 | Chrome DevTools for coding agents (Google) |
| [K-Dense-AI/scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills) | 46,491 | "Turn any AI agent into an AI Scientist" — the #1 agent-skills library for science |
| [openai/openai-agents-python](https://github.com/openai/openai-agents-python) | 29,676 | OpenAI's multi-agent framework; the SDK layer beneath the Agents API |
| [letta-ai/letta](https://github.com/letta-ai/letta) | 24,867 | Platform for stateful agents with advanced memory that learns and self-improves |
| [HKUDS/DeepCode](https://github.com/HKUDS/DeepCode) | 16,634 | Open agentic coding: harness, loop engineering, multi-agent orchestration |
| [google/mantis](https://github.com/google/mantis) | 1,705 | Google's modular security-review skills toolkit for coding agents (Apache 2.0) |

**Ecosystem watch:** the big harnesses remain the **stable substrate**, each still climbing day-over-day (deepseek-harness ~235.0K, claude-code ~147.9K, codex ~126.3K — the top three each gained ~50–150 stars since yesterday's run). Today's qualitative shift is on the **standards and science** side: the **Agentic AI Foundation (MCP + AGENTS.md + goose) operationalizing agent identity, delegation, and handoff** as public interoperability standards, **Z.ai shipping the most capable open-weights cyber model (GLM-5.3)** that makes self-hosted frontier security real, and **Anthropic's Claude making a genuine novel biology discovery** — together signaling the ecosystem is moving from "which harness is best" to **"which neutral infrastructure do agents run on, and what can they actually discover on their own?"** The K-Dense scientific-agent-skills and letta stateful-memory entries sit at the exact intersection of that shift.

---

## Sources

- Anthropic Claude ART / CRISPR-like enzyme discovery: https://www.anthropic.com/news/claude-discovers-novel-enzyme-system · https://www.aljazeera.com/economy/2026/9/24/ai-model-claude-discovers-crispr-like-enzyme-system-anthropic-says · https://www.trendingtopics.eu/anthropic-claude-crispr-like-enzyme-system/
- Z.ai GLM-5.3 open weights (753B MoE, cyber, custom license): https://z.ai/blog/glm-5.3 · https://curiouslm.com/blog/glm-5-3-open-weights-released · https://nowline.net/reports/z.ai-opens-glm-5.3-s-full-753b-weights-%E2%80%93-not-mit-this-time · https://www.axios.com/2026/08/14/china-open-source-ai-glm-53
- Funding wave (Sept 23–24): https://techstartups.com/2026/09/24/startup-funding-news-today-september-24-2026-50skills-byteask-pilgrim-kasvu-therapeutics-puxi-optoelectronics-more · https://techstartups.com/2026/09/23/venture-capital-startup-funding-roundup-september-23-2026-accel-jpmorgan-s32-t-rowe-price-y-combinator-more · https://techstartups.com/2026/09/22/venture-capital-startup-funding-roundup-september-22-2026-general-catalyst-goldman-sachs-greylock-m13-y-combinator-more
- Agentic AI Foundation (AAIF) / MCP / AGENTS.md / goose: https://openai.com/index/agentic-ai-foundation/ · https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation · https://aaif.io/ · https://www.infoq.com/news/2025/12/agentic-ai-foundation/
- Alibaba Zhenwu V900 chip + Qwen roadmap: https://www.thehindu.com/sci-tech/technology/alibaba-group-unveils-new-ai-chip-zhenwu-v900-plans-to-train-new-ai-model/article71494284.ece · https://www.japantimes.co.jp/business/2026/09/22/tech/alibaba-ai-chip-shares
- Trump UNGA "Superintelligence" rename / U.S.–China AI hotline: https://fortune.com/2026/09/22/beijing-and-washington-talk-about-an-ai-hotline-and-why-the-openai-hack-should-worry-every-ceo · https://political.org/2026/09/22/trump-flexes-american-power-at-un-renames-ai-superintelligence-and-warns-iran-of-annihilation
- GitHub star counts: verified live via the GitHub REST API at compilation time (all repos listed in the table above).

---

## Compilation Note

Compiled Thursday, September 24, 2026 (America/Los_Angeles). This report is materially distinct from the September 23 edition: yesterday's anchors were **the same-hour Claude Opus 5.5 / GPT-6 Sol–Luna frontier price war, Trump's UNGA "Superintelligence" rename and U.S.–China AI hotline, the France-convened UN Security Council AI briefing, Alibaba's Zhenwu V900 chip + 5–10T-param Qwen roadmap, and Naver Cloud's 700B open-source national security AI** — none of which are the lead stories today. Today's five leads are **Anthropic's Claude autonomously discovering a novel CRISPR-like enzyme system (ART), Z.ai shipping the full 753B open-weight GLM-5.3 cyber-capable MoE, the dense Sept 23–24 AI funding wave (Tekever $580M / Cyera $400M / Snorkel $350M / Enveda $311M / Basecamp Research $140M / Pilgrim $25M), the Agentic AI Foundation (MCP + AGENTS.md + goose) operationalizing agent-identity/handoff standards, and the vertical-AI wave (ByteAsk C/C++, AIONA factory engineering, 50skills, Clastix sovereign Kubernetes)**. Star counts were re-verified against the GitHub REST API this run; funding and preprint figures are as reported by the cited outlets and not independently verified.
