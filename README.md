# 🔬 Agentic AI & Generative AI Research Report — Tuesday, November 24, 2026

*Compiled Tuesday, November 24, 2026 (America/Los_Angeles) from a fresh research pass on November 23–24, 2026. Today's edition introduces five completely new anchor stories not present in the November 23 edition: **XPENG unveiling WorldGPT** — a single "Turing World Model" that learns across six machine embodiments (cars, boats, drones, single- and dual-arm robots, and humanoids) and posts 12 first-place results on public autonomous-driving, robotics, and video-generation benchmarks; **Google DeepMind's Gemini 4 agent teams discovering Lean-verified quantum algorithms** — agent swarms, checked by the Lean theorem prover and a clean-sandbox external verifier, cut the estimated cost of a fusion simulation 11.8× and produced formally verified programs for five quantum problems; **OpenAI and Cisco launching Shirudo** — an open-source, eBPF-based Linux runtime in which AI agents write signed kernel "shields" that block an exploit in the wild (demonstrated against Java4Shell and a recent PHP flaw) without restarting the service; **Anthropic completing the largest IPO in history (~$81.3B) under fire** — a Nobel/Turing/Fields laureate coalition's "MisAnthropic Statement" and its S-1's RSI risk-factor language putting recursive self-improvement at the center of the listing; and **Yandex shipping YandexGPT 4** — a new Pro/Lite model generation with chain-of-thought reasoning and ~4× longer context. Security watch leads with the **CISA KEV Nov 23 batch** (MONAI Label CVE-2026-133968 and N-able MailAssure CVE-2026-134624, both critical, federal due Nov 26) and the **WebSec benchmark** finding that all eight major search APIs served malicious content to AI coding agents. Figures below are as reported by the cited outlets and are not independently verified.*

---

## Top 5 Latest Advancements

### 1. XPENG Unveils WorldGPT — One World Model That Learns Across Cars, Robots, and Drones (Nov 24)

**What happened:** XPENG (Guangzhou) unveiled **WorldGPT**, part of its **Turing World Model** family, on Nov 24 — a single AI model designed to let *different types of machines* understand, predict, and act in the physical world. Unlike conventional systems built separately per task, WorldGPT learns from visual data across **six embodiments: cars, boats, drones, single-arm robots, dual-arm robots, and humanoid robots** — the first world model to demonstrate both prediction *and* action-planning across all six. Given previous camera footage plus a simple instruction, it can generate video of how a scene might evolve, plan the actions needed to complete a task, and explain its reasoning in natural language. Architecturally it runs a **large cloud-based "teacher model"** that learns shared physical-world knowledge across machine fleets, then distills that knowledge into smaller, specialized **on-device models** — so developers build one shared foundation and adapt to specific hardware rather than retraining per machine. As of Nov 12, 2026, WorldGPT held **12 first-place rankings across public benchmarks** in four areas: in autonomous driving it led **NAVSIM v2** (standard and challenging scenarios, 4 benchmark evaluations); in robotics it hit a **95.2% average success rate across 50 single-arm manipulation tasks** (highest among published models) and led on adapting to unfamiliar tasks and changing environments; in visual understanding it ranked first on **CV-Bench** and two **BLINK** subtasks (spatial understanding and object relationships); and in video generation it posted the highest overall **VBench 2.0** score and tied for first on **WorldOlympiad** (long-horizon simulation). (XPENG — Nov 24)

**Why it matters:** Physical AI has historically been a collection of per-modality systems (a driving stack, a manipulation stack, a video model). WorldGPT is an early, concrete argument that **one shared world model can transfer across embodiments** — the same way a foundation model generalizes across text tasks — collapsing the per-machine training cost and pointing at a common substrate for autonomous vehicles + robotics + drones. The teacher→on-device distillation pattern is also the practical answer to the on-vehicle compute constraint.

**Sources:**
- https://www.xpeng.com/news/01a20bcf44b3a1e838d68a02a2110153

---

### 2. Google DeepMind: Gemini 4 Agent Teams Discover Lean-Verified Quantum Algorithms (Nov 23)

**What happened:** Google DeepMind (with Google Quantum AI) presented research on Nov 23 showing that **teams of Gemini 4 agents, checked by the Lean theorem prover**, produced lower-cost quantum programs for five problems — the largest scientific gain being an **11.8× reduction in the estimated cost of a fusion simulation**. The problems covered **parallel Grover search, fixed-point arcsin arithmetic, and three simulations** (alpha-particle stopping power in fusion fuel, non-Born–Oppenheimer molecular dynamics, and Cytochrome P450 energy estimation). For fault-tolerant circuits the team measured **spacetime cost = peak logical qubits × T-gate count** (memory demand combined with the operations that are expensive on error-corrected quantum computers). Two safeguards made the results meaningful: an **external verifier replayed every submission in a clean sandbox against a frozen specification** — checking dependent definitions, permitted axioms, and claimed costs — so agents couldn't weaken theorems or game local checks; and **independent teams shared their best verified solutions, reusable lemmas, and reviewed dead-end notes through a shared wiki**, with agents meeting "every four hours in virtual conferences" to critique proposals (conference claims counted only after verification). The paper estimates **61% of the measured cost reduction came from within teams, 15% from cross-team wiki material, and 24% from the conferences** (with the caveat that credit is hard to separate cleanly). The work was first posted to arXiv on Nov 6 ("Discovering formally verified quantum programs with AI," v3 Nov 16, manuscript dated Nov 17) with a public repository separating the core **QuantumComputation** library from **QuantumComputationSpecs** (specifications + benchmark challenges, discovered programs on a `discoveries` branch). DeepMind is explicit about the limits: end-to-end simulations still demand far more resources than projected first fault-tolerant quantum computers, and the results are bounded by specifications that **exclude error correction and qubit routing**. (Google DeepMind, Unite.AI — Nov 23)

**Why it matters:** This is a template for **agentic scientific discovery with formal guarantees**: the Lean check plus a frozen-spec sandbox means agents can propose *and prove* reductions beyond what classical simulation can test, while humans own the physical model and cost conventions. The cross-team wiki + recurring-conference structure is a reusable multi-agent research protocol — and the honest disclosure that gains vanish once error correction and routing enter the spec is exactly the calibration the field needs.

**Sources:**
- https://deepmind.google/discover/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/
- https://www.unite.ai/google-deepmind-agent-teams-discover-lean-verified-quantum-algorithms/

---

### 3. OpenAI and Cisco Launch Shirudo — Agentic Linux Security That Shields Systems Without a Reboot (Nov 23)

**What happened:** On Nov 23, **OpenAI and Cisco** (built by Cisco's Isovalent team) launched **Shirudo** (Japanese for "shield"), an **open-source Linux runtime** (BSD 2-Clause; BPF programs dual-licensed BSD/GPL) that lets AI agents **write dynamic eBPF controls to shield a running system from an exploit while teams test and roll out the real patch — with no restart or downtime**. Built atop Isovalent's **Tetragon** eBPF platform, its working unit is an **"upatch"**: a small signed eBPF program (for the kernel) or a signed **Java agent** (for JVMs) that blocks a vulnerable code path at a kernel hook or guards application code. A **guardian agent** runs the defense loop: it scans open-source code and ingests vendor disclosures, traces each vulnerability to the affected assets and attack paths, **reproduces and validates the exploit**, writes a small targeted shield, and confirms it blocks the exploit while the service still runs. Shields graduate to active blocking **only when the evidence says it's safe**, and retire when the real patch lands. Shields ship as **signed `.bee` packages over an OCI-compliant registry**, are validated with **TPM 2.0** measurements, and — after boot — the kernel only accepts BPF from a loader signed with the operator's key, with every change measured into the TPM for verifiable evidence. In controlled tests, a **Codex-generated shield stopped a Java4Shell exploit on a live Elasticsearch service without restarting it** (adding an input check to Java's Base64 decoder), and Cisco says Shirudo also wrote code that detected and blocked attempts to exploit a recent **PHP** flaw. It is **pre-release**, requiring a patched bpf-next kernel, a TPM 2.0, and a measured boot (x86-64 CI complete; arm64 host tests; riscv64 pending). (OpenAI, Cisco, The Hacker News, Quartz — Nov 23–24)

**Why it matters:** Shirudo attacks the **patch-window** — the days between a public CVE and a deployed patch — by giving defenders a machine-speed, agent-operated mitigation layer that doesn't take workloads offline. It's a direct, agentic answer to the exact class of problem in this report's security watch (the Java4Shell and MONAI Label exploitation waves), and its signed-loader + TPM-attestation design shows how far "self-defending infrastructure" has moved from a slogan toward a working, open architecture.

**Sources:**
- https://openai.com/index/introducing-shirudo/
- https://blogs.cisco.com/news/expanding-the-defenders-window-with-self-defending-infrastructure
- https://thehackernews.com/2026/11/openai-and-cisco-unveil-ai-assisted.html
- https://github.com/shirudo-dev/shirudo

---

### 4. Anthropic Completes the Largest IPO in History — and a Laureate Coalition Calls It "Not a Safe AI Company" (Nov 18–23)

**What happened:** Anthropic completed **the largest initial public offering in history, raising ~$81.3 billion** (per The Verge), with shares opening on the Nasdaq and CEO **Dario Amodei** giving a Nasdaq bell speech in which he promised to pace training and deployment "as long as needed for safety" and said the company would not bend to business or political pressure. The listing landed in the middle of an organized safety backlash: on **Nov 18**, the **Center for AI Safety (CAIS)** joined a rare cross-spectrum coalition — including **Nobel laureates (Oliver Hart), Turing Award winner Judea Pearl, Fields medallists (Peter Scholze, James Maynard, David Mumford), Steven Pinker, Lawrence Lessig and Laurence Tribe, Hugging Face co-founder Thomas Wolf, xAI co-founder Igor Babuschkin, FLI chair Max Tegmark, and e/acc founder Guillaume "Beff Jezos" Verdon** — in signing the **"MisAnthropic Statement"** (misanthropicstatement.com), which argues Anthropic "warns that recursively self-improving AI could concentrate power and escape human control, yet races to build it first," uses safety branding to court investors, and has quietly weakened its pledges. The statement's three charges: (1) **racing toward RSI** while warning about it; (2) **using safety branding** to recruit safety-conscious talent and pitch investors as it automates AI R&D; and (3) **weakening safety commitments** — fully dropping its unilateral commitments to pause in its February Responsible Scaling Policy revision, and lobbying to weaken SB 1047, the RAISE Act, and the AEGIS Act while privately backing federal pre-emption of state AI laws. The S-1 itself is the exhibit: it discloses that **Claude writes over 90% of Anthropic's own code**, that a METR analysis found AI development sped up **~2×**, and that the company **"may imminently meet its Responsible Scaling Policy's definition"** of dramatically accelerated AI progress — while also stating it does **not** expect to safely let Claude fully build its successors without "meaningful human supervision." Early investor **Dustin Moskovitz** told the NYT he invested to promote safety, not racing; more than 100 protesters gathered outside Anthropic's SF HQ, and four were arrested for allegedly blocking the entrance. (The Verge, TNW, Future of Life Institute, safe.ai — Nov 18–23)

**Why it matters:** This is the first time a frontier-lab **IPO** has become the vehicle for a public RSI debate — the "AI that builds itself" question is now a *disclosed, investor-facing risk factor* rather than a think-tank hypothesis. The coalition's unusual composition (safety researchers *and* accelerationists, Nobel and Turing laureates, open-source and alignment figures) signals a consensus that the RSI race — not any single safety failure — is the contested issue, and it frames how public-market pressure will shape frontier-lab release cadence for the next several quarters.

**Sources:**
- https://thenextweb.com/news/misanthropic-statement-anthropic-not-safe-ai-company-cais-ipo
- https://safe.ai/news/anthropic-is-not-a-safe-ai-company
- https://futureoflife.org/statement/leaders-condemn-anthropic-for-race-to-rsi/
- https://www.sec.gov/Archives/edgar/data/2130357/000162828026068676/anthropicpbc-sx1ax1.htm

---

### 5. Yandex Ships YandexGPT 4 — a New Model Generation With Reasoning and ~4× Context (Nov 24)

**What happened:** Yandex released **YandexGPT 4** on Nov 24, a new generation of generative models available via the **Yandex Cloud API** (some functions still in test mode), split into a **Pro** model (complex, time-consuming tasks like sales analysis) and a **Lite** model (speed-sensitive scenarios). The headline changes: the models **learn to reason** — they support chain-of-thought, breaking hard questions into step-by-step sub-problems before answering (with hidden reasoning to be added to the API later) — and they **process ~4× more text than the third generation**, keeping conversation context much longer and analyzing **~60 pages of text** (roughly 60 pages of context). Yandex reports **Pro outperforms the previous generation in ~70% of cases on response quality**, approaching GPT-4o on some open-ended tasks, while **Lite matches the previous generation's most powerful model**. Hallucination/error rates on RAG-style external-source questions **roughly halved (from ~4% to 2.1%)**, and the models answer **~2× faster** than before. The line adds **third-party command generation** — e.g., asking it to find a plane ticket produces a command for the airline service to start a seat search — to be added to Yandex Cloud "in the near future." The first consumer service to ship it is **Alice** (the "Pro" option). (Yandex via AKM — Nov 24)

**Why it matters:** YandexGPT 4 is the clearest sign yet that **reasoning and long-context are becoming table stakes** outside the US/China frontier tier — a major non-English (Russian-first) lab shipping CoT + 4× context + agentic command generation to a commercial cloud within a year of the US labs' reasoning wave. The error-rate halving on RAG is the kind of enterprise-relevant metric that matters for production deployments.

**Sources:**
- https://www.akm.ru/eng/press/yandex-launches-a-new-generation-of-yandexgpt-4-language-models-they-have-learned-to-reason-and-proc/

---

## New Use Cases

### Agentic "Self-Defending" Infrastructure — Shielding Systems Through the Patch Window (Nov 23)
Shirudo (Top 5 #3) creates a new operational category: **agent-operated, runtime, zero-downtime vulnerability mitigation**. The use case is the *patch window* — the days between a public CVE and a deployed patch — where an agent reproduces the exploit, writes a signed eBPF/Java shield, verifies it blocks the attack while the service stays up, and retires it once the real patch lands. It's a direct, deployable answer to the Java4Shell and MONAI Label exploitation waves and a template for "self-healing" fleets that can't take multi-day training jobs or 24/7 services offline.
*Source: https://openai.com/index/introducing-shirudo/*

### Shared-Embodiment Physical AI — One World Model, Many Machines (Nov 24)
XPENG's WorldGPT (Top 5 #1) reframes robotics/AV development from "train a model per machine" to **a shared cloud teacher distilled into specialized on-device models across cars, boats, drones, and robots**. The reusable use case: a single physical-world foundation that transfers perception, prediction, and action-planning across embodiments, cutting per-machine training cost and letting one codebase drive heterogeneous fleets.
*Source: https://www.xpeng.com/news/01a20bcf44b3a1e838d68a02a2110153*

### Formal-Verification-Gated Agentic Science — Lean as the Agent's Proof Oracle (Nov 23)
DeepMind's quantum work (Top 5 #2) establishes a repeatable use case: **run agent swarms against a frozen specification, with a Lean check and a clean-sandbox external verifier as the acceptance gate**, plus a cross-team wiki and recurring "conferences" for knowledge sharing. The pattern — *agents propose, the prover disposes* — is directly transferable to any domain where a result can be formally checked (optimization, combinatorics, systems verification).
*Source: https://deepmind.google/discover/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/*

### RSI as a Disclosed, Investor-Facing Risk Factor (Nov 18–23)
Anthropic's IPO (Top 5 #4) makes **recursive self-improvement a public, regulated disclosure** for the first time: an S-1 that quantifies self-written code (90%), self-accelerated R&D (~2×), and an "imminent" RSI threshold, alongside a named mitigation (human supervision). The use case is governance — a template for how future frontier-lab filings (and any RSI-capable product) will frame capability risk to regulators and shareholders.
*Source: https://www.sec.gov/Archives/edgar/data/2130357/000162828026068676/anthropicpbc-sx1ax1.htm*

---

## Top Rated GitHub Projects Leveraging Agentic/Gen AI

| Repository | Stars* | What it does (agentic/Gen-AI angle) |
|---|---|---|
| [shirudo-dev/shirudo](https://github.com/shirudo-dev/shirudo) | 1,555 | **OpenAI + Cisco "Shirudo"** — an eBPF-based Linux security platform where **AI agents write signed kernel/Java "upatches"** that block exploits on a running system without a reboot; TPM-attested, OCI-delivered shields (pre-release; C, created Oct 13). |
| [erkamyaman/safe-anything](https://github.com/erkamyaman/safe-anything) | 607 | **"Find the holes before someone else does"** — a fast, 100%-Rust vulnerability scanner for **XSS, SQL injection, leaked secrets, dependency CVEs, and the AI-agent setup that writes the code** (Claude Code / Codex / Cursor / MCP); every finding ships with the line, the reason, and the fix (Rust, created Nov 22). |
| [deterministic-machines/deslop-please](https://github.com/deterministic-machines/deslop-please) | 616 | **"Bring (back) sanity to your code"** — an opinionated linter that removes **sloppy/AI-generated code**, following *A Philosophy of Software Design*; CI-badged, on crates.io (Rust, created Nov 22). |
| [jaredfreellm/FREELLM_INSTALL](https://github.com/jaredfreellm/FREELLM_INSTALL) | 252 | **One OpenAI-compatible endpoint for many free LLM tiers** — a self-hosted gateway that combines providers' free tiers behind a single `/v1` API, picks a healthy model per request, fails over on rate limits, and tracks usage per key (MIT, created Nov 22). |
| [duwqijlk/browser-capture](https://github.com/duwqijlk/browser-capture) | 190 | **Zero-dependency browser CDP + stealth-hook capture & reverse-engineering AI Skill/CLI** for BitBrowser, AdsPower, and Chrome/VisibleV8 — full-packet capture and reverse engineering packaged as an agent skill (JS, created Nov 23). |

\* Star counts verified live via the GitHub API on November 24, 2026; all repos created Oct 13–Nov 23, 2026 and are actively pushed. (The Nov 23 edition covered EL4CTEO/fast-anything, iamajmeena/neonclipping, leanprover-community/riemann-hypothesis, boringmarketer/boring-marketing-skills, and CocoSgt/riemann-hypothesis-lean. A large cluster of Nov 22–24 "game cheat / mod menu / seed-phrase recovery" repositories with near-identical star counts and scam-style descriptions was **excluded as suspected star-farming/scam**.)

---

## Security & Remediation Watch

**New this cycle (Nov 23–24):**

1. **CISA KEV Nov 23 batch — two critical, actively exploited flaws (federal due date Nov 26).** CISA added two vulnerabilities to its Known Exploited Vulnerabilities catalog on Nov 23, both with a **Nov 26, 2026 federal remediation deadline**:
   - **CVE-2026-133968 — Project MONAI MONAI Label path traversal → RCE (CVSS 3.1 9.8, CRITICAL).** Unauthenticated remote attackers can traverse directories via the `image` parameter to `PUT /datastore/image` and write arbitrary files outside the datastore, achieving **remote code execution**. Affects versions **0 through 0.8.5**; exploited in the wild since **September 2026** (the China-linked "Cairn" AI-agent campaign detailed in the Nov 23 edition), with public exploit code now in nuclei-templates. **Remediate:** upgrade to **MONAI Label ≥ 0.8.6** (`pip install -U monailabel==0.8.6` / `docker pull projectmonai/monailabel:0.8.6`); enable authentication, restrict the ANNOTATOR role, and keep instances off untrusted networks. **Verify for compromise** on any exposed instance that ran during the Sept 8–10 window.
   - **CVE-2026-134624 — N-able MailAssure (SpamExperts) SSRF (CVSS 4.0 9.3, CRITICAL).** The LDAP-synchronization connection check during relay configuration does not restrict its destination, so an **authenticated API user** can force the server to connect to **arbitrary internal hosts/ports**, map the internal network, and send crafted data to internal services. Affects versions **before 20261121.1943**. **Remediate:** upgrade to **build 20261121.1943 or later**; treat any exposed MailAssure/SpamExperts relay endpoint as a potential internal-network reconnaissance vector.
   *(CISA, CVEGuru, eastbaycyber — Nov 23–24)*
   *Sources: https://cisa.gov/news-events/alerts/2026/11/23/cisa-adds-two-known-exploited-vulnerabilities-catalog · https://www.cisa.gov/known-exploited-vulnerabilities-catalog*

2. **WebSec benchmark: every major search API served malicious content to AI coding agents (Nov 23).** AIR Research Lab's **WebSec** benchmark — the first public measurement of how often commercial web-search APIs hand AI agents dangerous content — ran **4,719 realistic coding-agent queries** through **eight search APIs (Firecrawl, Tavily, Perplexity, Parallel, Exa, Nimble, Brave, You.com)** and scanned **282,000+ results**. **No query mentioned anything malicious, yet every API returned known-malicious content at least once** — 534 searches (~1.4%) surfaced known-malicious content, and agents were handed malicious/risky results **1,026 times** (per-API rates 0.8%–2.2%; highest on install/package queries). Its **WebSec Index** (higher = safer) ranked **Firecrawl 21.59** and **Tavily 18.59** highest, **You.com 5.02** lowest — a >4× spread, but *no provider came back clean*. It documents six attack pathways (prompt injection, typosquatting, hallucination attacks, SEO/AEO manipulation, web-search hijacking, manipulative content) and a real chain — **SolanaCry**, a 286-star GitHub repo ranking first for a Solana starter-kit query whose install step dropped a NetSupport Manager remote-access trojan onto any agent that ran it. **Remediation:** treat everything an agent reads (search results, READMEs) as **untrusted input**; block auto-approval of `curl | sh` / `iwr | iex` download-and-execute; verify package existence/age and domain registration before install; and log what agents *read*, not just what they run. *(AIR, The Hacker News, Cloud Security Alliance — Nov 23–24)*
   *Sources: https://www.air.security/blog-posts/websec · https://thehackernews.com/expert-insights/2026/11/ai-coding-agents-are-getting-malicious.html*

**Due today (Nov 24) / carry-forward — patch now:**
- **CVE-2026-125350 — Google Chromium XML use-after-free (CVSS 8.8)** — the **eighth actively exploited Chrome zero-day of 2026**; RCE inside the sandbox via a crafted webpage, affecting Chrome, Edge, and other Chromium browsers. Federal due date is **Nov 24 (today)**. **Remediate:** update to **Chrome 157.0.8103.50/.51** (Win/macOS) / `.50` (Linux) and apply equivalent fixes in Edge/Brave/Opera/Vivaldi.
- **CVE-2026-124194 — Microsoft Office Outlook "missing user interaction" spoofing** — an unauthorized attacker can perform spoofing over the network. Federal due date is **Nov 24 (today)**. Apply the current Outlook security update.
- **Java4Shell (CVE-2026-114938)** — the critical unauthenticated OpenJDK Base64-decoder RCE remains the top-priority patch of the cycle (see Nov 23 edition); note Shirudo's (Top 5 #3) demonstrated Java4Shell shield as an interim, zero-downtime mitigation.
- **Agent-framework PyPI supply-chain compromise** — audit any `agentframework` installs from the compromise window (see Nov 23 edition).

**AI-tooling security theme:** The MONAI Label campaign (AI agents *as* exploiters), the WebSec benchmark (search APIs as an untrusted retrieval layer), and Shirudo (agents as defenders) together mark **agentic AI security as a two-sided problem** — the same autonomy that lets agents find and shield exploits also lets them be weaponized and poisoned. Teams should treat agent web/search input as untrusted, gate auto-approve installs, and keep a runtime mitigation layer (eBPF shields, canary tokens, provider pinning) for the patch window.
*Sources: https://openai.com/index/introducing-shirudo/ · https://aws.amazon.com/blogs/aws/amazon-threat-intelligence-monai-label-campaign/*

---

## Also Notable

- **GPT-6.2 Sol lands in the ChatGPT Chat tab (Nov 23–24)** — OpenAI rolled out a chat-tuned version of GPT-6.2 Sol to **Plus, Pro, Business, and Enterprise** (Free/Go excluded for now), better at detailed instructions, web search, and reading fine detail in photos (OpenAI's own tests: image understanding 47.4% → 71.7%; instruction-following on hard prompts 62.5% → 78.1%), and it can proactively offer **price-drop alerts**. GPT-5.6 Sol/Terra are set to retire from Work/Codex on **Dec 23**. (The Verge, 9to5Mac, Digital Trends)
- **Google Gemini 4 Neon** — priced $3/$15 per million tokens, #3 on the Artificial Analysis Intelligence Index (61) and **#1 on the AA Coding Agent Index (58.6)**, with a 1M-token context and four thinking levels. (AIBriefs)
- **Qoder's "HungerG"** — a new coding model with an undisclosed developer, selectable in Qoder/Qoder IDE and free to try through Nov 30. (The Neuron)
- **RoboTrack** (Nov 23) — point tracking for real-world robotic manipulation, released on Hugging Face. (HF)
- **Meta's Alexandr Wang** framed the AI-assisted Riemann proof as "a clear sign that superintelligence is right around the corner," arguing raw intelligence is no longer the bottleneck (see Nov 23 edition).

---

## Sources

### Today's anchors
- https://www.xpeng.com/news/01a20bcf44b3a1e838d68a02a2110153
- https://deepmind.google/discover/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/
- https://www.unite.ai/google-deepmind-agent-teams-discover-lean-verified-quantum-algorithms/
- https://openai.com/index/introducing-shirudo/
- https://blogs.cisco.com/news/expanding-the-defenders-window-with-self-defending-infrastructure
- https://thehackernews.com/2026/11/openai-and-cisco-unveil-ai-assisted.html
- https://github.com/shirudo-dev/shirudo
- https://thenextweb.com/news/misanthropic-statement-anthropic-not-safe-ai-company-cais-ipo
- https://safe.ai/news/anthropic-is-not-a-safe-ai-company
- https://futureoflife.org/statement/leaders-condemn-anthropic-for-race-to-rsi/
- https://www.sec.gov/Archives/edgar/data/2130357/000162828026068676/anthropicpbc-sx1ax1.htm
- https://www.akm.ru/eng/press/yandex-launches-a-new-generation-of-yandexgpt-4-language-models-they-have-learned-to-reason-and-proc/

### Security
- https://cisa.gov/news-events/alerts/2026/11/23/cisa-adds-two-known-exploited-vulnerabilities-catalog
- https://www.cisa.gov/known-exploited-vulnerabilities-catalog
- https://www.air.security/blog-posts/websec
- https://thehackernews.com/expert-insights/2026/11/ai-coding-agents-are-getting-malicious.html
- https://labs.cloudsecurityalliance.org/research/csa-research-note-search-api-poisoning-coding-agents-2026112/
- https://aws.amazon.com/blogs/aws/amazon-threat-intelligence-monai-label-campaign/

### GitHub repos
- https://github.com/shirudo-dev/shirudo
- https://github.com/erkamyaman/safe-anything
- https://github.com/deterministic-machines/deslop-please
- https://github.com/jaredfreellm/FREELLM_INSTALL
- https://github.com/duwqijlk/browser-capture

### Also Notable
- https://www.theverge.com/ai-artificial-intelligence/1040716/openai-launched-a-chat-specific-version-of-gpt-6-2-sol
- https://9to5mac.com/2026/11/23/chatgpt-expands-gpt-6-2-sol-as-openai-sets-retirement-date-for-two-models/
- https://www.digitaltrends.com/computing/chatgpt-is-getting-a-chat-tuned-gpt-6-2-sol-and-it-can-offer-to-watch-for-a-price-drop/

---

## Compilation Note

Compiled Tuesday, November 24, 2026 (09:10–09:55 PT, America/Los_Angeles) by the ai-research cron job. Research pass covered Nov 23–24, 2026 via live web search and direct fetches across XPENG, Google DeepMind, Unite.AI, OpenAI, Cisco/Isovalent, The Hacker News, Quartz, The Verge, TNW, the Future of Life Institute, safe.ai, the SEC (S-1), Yandex (AKM), CISA KEV, AIR Research Lab, the Cloud Security Alliance, and the GitHub API (repo star counts verified live). All five anchors are new relative to the November 23 edition, which led with Z.ai's GLM-5.4 Loop Transformer, the NVIDIA/Jensen Huang reinstatement, the Riemann proof's first verification gate, Anthropic's "Claude writes 90% of its own code," and METR's Q4 capability warning. Today's edition is dominated by **agentic AI going physical and self-defending** (XPENG WorldGPT, DeepMind's Lean-verified quantum agents, and OpenAI/Cisco's Shirudo), with **Anthropic's record IPO and the RSI backlash** as the week's defining governance story and **CISA's Nov 23 KEV batch + the WebSec benchmark** anchoring the security watch. Figures are as reported by the cited outlets and are not independently verified.
