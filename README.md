# 🧠 Prompt Optimizer

<p align="center">
  <img src="https://img.shields.io/badge/version-v10.0-blue.svg?style=for-the-badge&logo=git" alt="Version">
  <img src="https://img.shields.io/badge/architecture-Meta--Skill%20%26%20Skill%20Router-emerald.svg?style=for-the-badge" alt="Architecture">
  <img src="https://img.shields.io/badge/license-MIT-green.svg?style=for-the-badge" alt="License">
  <img src="https://img.shields.io/badge/target-Agents%20%7C%20Gemini%20%7C%20Claude%20%7C%20GPT%20%7C%20OSS-purple.svg?style=for-the-badge" alt="Targets">
</p>

<p align="center">
  <b>The Enterprise-Grade Meta-Skill & Skill Router for AI Coding Agents and Large Language Models.</b><br>
  Transform raw, underspecified prompts into structured, model-tuned, autonomous execution blueprints.
</p>

---

## 🚀 Executive Summary

**Prompt Optimizer** is an autonomous **Meta-Skill and Skill Router** designed for modern AI development environments (**Antigravity, Cursor, Claude Code, GitHub Copilot Workspace**) and frontier LLMs (**Gemini, Claude, GPT, Llama, DeepSeek, Qwen**).

Unlike legacy prompt generators that produce passive text snippets for copy-pasting, Prompt Optimizer produces **Active Agent Execution Instructions**. It commands AI agents to inspect project workspaces, edit codebase files directly, construct implementation plans, search local/web skill registries, and execute empirical build/test verification commands.

---

## 🔥 Key Pillars & Capabilities

```mermaid
graph TD
    A["🧑 Raw User Prompt"] --> PO["🧠 Prompt Optimizer (Meta-Skill)"]
    
    PO --> P1["🎯 Active Agent Framing"]
    PO --> P2["🧭 Dynamic Skill Routing"]
    PO --> P3["🛡️ 3-Gate Safety System"]
    PO --> P4["🛠️ Model Syntax Adapters"]
    PO --> P5["📐 Proportional 3-Tiering"]
    PO --> P6["🔒 Security & PII Redaction"]

    P1 --> OUT["⚡ Production-Grade AI Blueprint"]
    P2 --> OUT
    P3 --> OUT
    P4 --> OUT
    P5 --> OUT
    P6 --> OUT

    style PO fill:#6366f1,stroke:#4f46e5,color:#fff
    style OUT fill:#10b981,stroke:#059669,color:#fff
```

### 1. 🎯 Active Agent Execution Framing
* **Problem**: Standard prompts trigger AI agents to output walls of markdown code blocks in chat. Developers waste time copy-pasting, fixing imports, and manually debugging.
* **Solution**: Injects `Direct Workspace Actions` and `<making_code_changes>` directives that command agents to:
  - Open and inspect target files before writing edits.
  - Apply code modifications directly to workspace files.
  - Run empirical test suites (`npm test`, `php artisan test`, `pytest`, `flutter analyze`).

### 2. 🧭 Dynamic Skill Routing (Anti-Skill Hell Protocol)
* **Problem**: As developers install dozens of AI skills, they encounter **"Skill Hell"**—forgetting which skills exist, or having agents write naive custom code from scratch when a dedicated skill is available.
* **Solution**: Functions as a **Meta-Skill & Skill Router**:
  - **Local Skill Discovery**: Automatically instructs target agents to scan local skill roots (`~/.gemini/config/skills/`, `.agents/skills/`, plugin MCPs) and inspect `SKILL.md` before coding.
  - **Web & Internet Skill Search Fallback**: If no local skill matches, commands the agent to run a targeted web search (`search_web`, Google, GitHub) for specialized community skills, CLI specifications, or standard agent instruction sets.
  - **Zero Hardcoding**: Skill routing matches dynamically on task domain keywords (`<task_domain>`).

### 3. 🛡️ Three-Gate Safety & Quality System
Every prompt passes through **3 sequential gates** before optimization:
* **Gate 1 (Reject)**: Instantly blocks harmful, unsafe, or impossible requests.
* **Gate 2 (Clarify)**: Identifies missing *critical context* and asks **at most 2 targeted questions** using native IDE modals (`ask_question`). Auto-defaults remaining parameters to prevent user interrogation fatigue.
* **Gate 3 (Skip / Anti-Bloat)**: Protects simple prompts (`"format this json"`) from being bloated into 30-line structural prompts.

### 4. 🛠️ Model Syntax Adapters & Reasoning Intelligence
Tailors prompt geometry to the exact target LLM architecture:
* **Claude (Anthropic)**: XML tag section boundaries (`<role>`, `<task>`, `<constraints>`, `<agent_lifecycle>`) with completion tokens (`result: <summary>`).
* **Gemini (Google)**: Flat Markdown headers (`## Execution Steps`), procedural lists, and single-sentence silent thought step framing.
* **GPT & OpenAI Codex**: System/user message boundaries, `# Assistant Response Preferences` memory tracking, and explicit `[ROLE] → [CONTEXT] → [TASK]` delimiters.
* **Open-Source Models (Llama 3, Mistral, DeepSeek, Qwen)**: Compact Markdown (<2000 tokens), zero XML tags, strict schema limits, and format hallucination prevention.
* **Reasoning Models (o1/o3, Gemini Thinking, Extended Thinking)**: Constrains output format and workspace actions while leaving internal chain-of-thought unconstrained.

### 5. 🔒 Production Security & PII Redaction
* **Anti-Injection Isolation**: Encapsulates untrusted inputs in `<user_input>` delimiters with explicit override protection rules.
* **Credential & Secret Stripping**: Automatically redacts API keys (`sk-...`), passwords, database connection strings, and sensitive PII into safe generalized placeholders (`YOUR_API_KEY`, `[database-host]`).

### 6. 🔗 Multi-Prompt Sequential Chaining
* Decomposes monolithic architectural requests ("build a full-stack e-commerce app") into an ordered sequence of 2-4 dependent sub-prompts (Backend → Frontend → Integration) with explicit handoff points.

---

## 📊 Comprehensive Tool Comparison

| Capability / Feature | Prompt Optimizer (v10) | ChatGPT Prompt Gen | PromptPerfect | AIPRM | FlowGPT |
|---|:---:|:---:|:---:|:---:|:---:|
| **Active File Editing Directive** | ✅ **Direct Workspace Edits** | ❌ Text Only | ❌ Text Only | ❌ Text Only | ❌ Text Only |
| **Dynamic Skill Routing (Anti-Skill Hell)** | ✅ **Local + Web Search** | ❌ | ❌ | ❌ | ❌ |
| **Meta-Skill Orchestration** | ✅ **Discovers & Invokes Skills** | ❌ | ❌ | ❌ | ❌ |
| **Safety Gates (Reject / Clarify / Skip)** | ✅ **3-Gate Pipeline** | ❌ | ❌ | ❌ | ❌ |
| **Model-Specific Syntax Adapters** | ✅ **Claude / Gemini / GPT / OSS** | ❌ GPT Only | ⚠️ Limited | ❌ GPT Only | ❌ |
| **Open-Source Model Scaling** | ✅ **Llama / DeepSeek / Qwen** | ❌ | ❌ | ❌ | ❌ |
| **Token-Efficient Proportionality** | ✅ **Light / Standard / Heavy** | ❌ Fixed Template | ❌ | ⚠️ Categories | ❌ |
| **Interactive IDE Clarification** | ✅ **ask_question Modals** | ❌ | ❌ | ❌ | ❌ |
| **Security & PII Sanitization** | ✅ **Anti-Injection + Redaction** | ❌ | ❌ | ❌ | ❌ |
| **Empirical Verification Step** | ✅ **Automated Build/Test Commands** | ❌ | ❌ | ❌ | ❌ |
| **Open Source & Free** | ✅ **MIT License** | ✅ Free | ❌ Paid API | ⚠️ Freemium | ✅ Free |

---

## 💰 Token Cost & Efficiency Benchmarks

Prompt Optimizer enforces **proportional context scaling**, injecting only necessary constraints to maximize LLM signal-to-noise ratio.

```mermaid
graph LR
    subgraph "❌ Unoptimized Multi-Turn Trial"
        M1["Vague Prompt"] --> M2["Passive Code Block"]
        M2 --> M3["Copy-Paste & Debug"]
        M3 --> M4["Re-prompting (3-5x)"]
        M4 --> M5["~2,500 Tokens Spent"]
    end

    subgraph "✅ Prompt Optimizer One-Shot"
        P1["Structured Agent Blueprint"] --> P2["Direct Workspace Execution"]
        P2 --> P3["~350 Tokens Spent"]
    end

    style M5 fill:#ef4444,stroke:#dc2626,color:#fff
    style P3 fill:#10b981,stroke:#059669,color:#fff
```

| Task Complexity | Manual Trial-and-Error | With Prompt Optimizer | Token Savings |
|---|:---:|:---:|:---:|
| **Light** (Bug fix / JSON format) | ~250 tokens × 3 turns | ~120 tokens × 1 shot | **84% Savings** |
| **Standard** (API controller / UI component) | ~600 tokens × 4 turns | ~380 tokens × 1 shot | **84% Savings** |
| **Heavy** (Full-stack feature / Architecture) | ~1,200 tokens × 5 turns | ~650 tokens × 1 shot | **89% Savings** |

---

## ⚡ Quick Installation

Copy and paste **one prompt** into your AI assistant (Antigravity, Gemini, Cursor) to install automatically:

```text
Create a new skill called "Prompt Optimizer" by performing the following steps:

1. Create the directory: ~/.gemini/config/skills/prompt_optimizer/
2. Create the directory: ~/.gemini/config/skills/prompt_optimizer/references/
3. Download and save the SKILL.md file from:
   https://raw.githubusercontent.com/mhammed2008/prompt-optimizer/main/SKILL.md
   → Save to: ~/.gemini/config/skills/prompt_optimizer/SKILL.md
4. Download and save the guide.md file from:
   https://raw.githubusercontent.com/mhammed2008/prompt-optimizer/main/references/guide.md
   → Save to: ~/.gemini/config/skills/prompt_optimizer/references/guide.md

After creating the files, confirm installation by listing the contents of ~/.gemini/config/skills/prompt_optimizer/
```

### Manual Installation
```bash
git clone https://github.com/mhammed2008/prompt-optimizer.git
cp -r prompt-optimizer ~/.gemini/config/skills/prompt_optimizer
```

### Invocation Shortcuts
Trigger the skill in your IDE or chat window:

| Trigger Method | Command / Prompt Example |
|---|---|
| **Direct Slash Command** | `/Prompt Optimizer` |
| **Natural Language** | `"Optimize this prompt for Claude: ..."` |
| **Refine Request** | `"Improve my prompt to refactor the database layer"` |
| **Agent Tuning** | `"Make this prompt work with Cursor / Antigravity"` |

---

## 🧩 Architectural Execution Pipeline

```mermaid
flowchart TD
    RAW["🧑 Raw User Prompt"] --> ST1["Step 1: Analyze & Detect Execution Mode"]
    
    ST1 --> G1{"Gate 1: Safe?"}
    G1 -->|"❌ Harmful"| REJ["Reject & Offer Safe Alternative"]
    G1 -->|"✅ Safe"| G2
    
    G2{"Gate 2: Missing Critical Context?"}
    G2 -->|"❌ Unknowns"| ASK["Ask ≤2 Questions via ask_question Modal"]
    ASK --> ANS["Wait for User Input"]
    ANS --> G3
    G2 -->|"✅ Complete"| G3
    
    G3{"Gate 3: Already Optimal?"}
    G3 -->|"✅ Yes"| SKIP["Skip / Light Rewrite (Anti-Bloat)"]
    G3 -->|"Needs Work"| ST2["Step 2: Select Techniques (A-L)"]
    
    ST2 --> ST3["Step 3: Determine Tier & Model Scaling"]
    ST3 --> ST4["Step 4: Format with Model Syntax Adapter"]
    ST4 --> ST5["Step 5: Adversarial Stress-Test"]
    ST5 --> ST6["Step 6: Output Finalized Blueprint"]

    style RAW fill:#6366f1,stroke:#4f46e5,color:#fff
    style ST6 fill:#10b981,stroke:#059669,color:#fff
    style REJ fill:#ef4444,stroke:#dc2626,color:#fff
```

---

## 📖 Real-World Production Examples

### Example 1: Active Agent Mode (Laravel API Caching & Rate Limiting)
**Original Prompt**: *"fix rate limit handling in ScanController.php"*

**Optimized Blueprint Output**:
```markdown
## Role
Act as a Senior Laravel Backend & Security Engineer.

## Context
Project workspace contains `app/Http/Controllers/ScanController.php` handling external API requests.

## Task
Directly modify `app/Http/Controllers/ScanController.php` to implement robust caching and HTTP 429 backoff handling.

<skill_discovery>
- Check locally installed skills (~/.gemini/config/skills/, .agents/skills/) for laravel/backend.
- If a matching local skill exists, read its SKILL.md file before proceeding.
</skill_discovery>

## Direct Workspace Actions
1. Inspect `app/Http/Controllers/ScanController.php`.
2. Add response caching (`Cache::remember`) to prevent redundant external API calls.
3. Add `Http::retry()` backoff logic for HTTP 429 rate limit responses.
4. Modify `app/Http/Controllers/ScanController.php` directly in the workspace codebase.

## Constraints
- Do NOT output code blocks in chat — apply edits directly to the workspace file.
- Preserve all existing method signatures and route contracts.
- Include inline comments explaining caching TTL and backoff intervals.

## Verification
Validate PHP syntax cleanly and confirm no unhandled exceptions are introduced.
```

---

### Example 2: Negative Example (Preventing Over-Engineering)

❌ **Over-Engineered Anti-Pattern**:
```text
Input: "format this json file"
Bad Output: A 30-line prompt with Role ("Act as a senior data architect"),
Context ("JSON is a data format..."), Task, Constraints, Verification,
and few-shot examples — for a one-line task. (Wastes tokens & confuses model).
```

✅ **Correct Light Output**:
```text
Reformat the following JSON with 2-space indentation, sorted keys, and valid UTF-8.
Preserve all existing data — do not add, remove, or modify any values.
```

---

## 📁 Repository Structure

```
.
├── SKILL.md             # Core runtime skill (~250 lines) — loaded by AI agents
├── references/
│   └── guide.md         # Full rationale, examples, anti-patterns & version history (~575 lines)
├── benchmarks/
│   └── test_prompts.md  # 10-test benchmark evaluation suite
└── README.md            # Professional technical documentation
```

---

## 📄 License & Community

Released under the **[MIT License](LICENSE)**. Free to use, modify, and distribute for commercial and open-source projects.

<p align="center">
  <b>Stop copy-pasting code blocks. Start commanding AI agents.</b><br>
  <code>/Prompt Optimizer</code> — The Meta-Skill & Skill Router.
</p>
