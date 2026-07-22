# Prompt Optimizer Skill

Rewrites raw prompts into professional, structured, model-tuned instruction sets — applying persona framing, active agent execution framing, few-shot examples, constraint layering, and output-schema specification.

Tuned specifically for **AI Coding Agents** (Antigravity, Cursor, Claude Code), **Gemini**, **Claude**, and **GPT** models.

---

## 🌟 Key Features

- **Active Agent Framing**: Ensures coding prompts command AI agents to **directly edit workspace files, create implementation plans, and execute verification commands** — avoiding passive chat-only code blocks.
- **Gate-Based Processing**: Evaluates intent, safety, context, and necessity before rewriting.
- **Three-Tier Architecture**:
  - **Light**: Quick single-action prompts (Task + Constraints).
  - **Standard**: Single domain, 1-3 missing details (Role + Context + Task + Workspace Actions + Constraints).
  - **Heavy**: Cross-domain, mission-critical, or complex tasks with adversarial stress-testing.
- **Interactive Clarification**: Solicits missing critical context before drafting the final prompt.
- **Target Tuning**:
  - **AI Coding Agents**: Direct workspace actions, file edits, plan creation, test verification.
  - **Gemini**: Markdown headers, flat numbered lists, system framing.
  - **Claude**: XML delimiters (`<context>`, `<task>`), detailed anti-instructions.
  - **GPT**: System/user separation, few-shot examples, JSON schema constraints.
  - **Reasoning Models**: Unconstrained internal reasoning with rigid output framing.

---

## 📁 Repository Structure

```
.
├── SKILL.md             # Core runtime skill definition & system prompt
├── references/
│   └── guide.md         # Full design rationale, agentic guidelines, & version history
└── README.md            # Overview and usage instructions
```

---

## 🚀 How to Use

### Installing in Gemini Antigravity IDE
Place this repository or folder under your custom skills path:
- Global: `~/.gemini/config/skills/prompt_optimizer/`
- Workspace: `.agents/skills/prompt_optimizer/`

### Invocation
Ask your AI assistant:
- `"/Prompt Optimizer"`
- `"Optimize this prompt for Antigravity: ..."`
- `"Refine my prompt into an active file-editing instruction"`

---

## 📄 License
MIT License. Free to use, modify, and distribute.
# prompt-optimizer
