# Changelog

All notable changes to the Prompt Optimizer skill are documented in this file.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

---

## [v11] — 2026-07-23

### Added
- **KV-Cache Prefix Ordering** — Strict Stable-to-Dynamic section ordering (System/Role → Skills/Docs → Workspace Rules → Dynamic Task → User Input) for ~50-80% token cost reduction on API providers with prompt caching.
- **Partial Context Pruning** — `<skill_discovery>` now instructs agents to perform line-range slicing via `view_file(StartLine, EndLine)` to read only the target domain section of skill files, preventing context bloat.
- **Token Compression** rules — Mandates concise internal monologue ("single-sentence silent thought step before file edits").
- **Model Cost Recommendation Tokens** in Output Format — Light/Standard/Heavy → suggested compute tier.
- **Parallel Execution Blueprints** — Non-dependent file actions grouped for concurrent execution.
- **Self-Check section** — Validates presence of `references/guide.md` and `benchmarks/test_prompts.md` on first invocation with graceful fallback.
- **Assumed Defaults section** — Gate 2 now requires a clearly labeled `## Assumed Defaults` block when the ≤2 question limit forces defaulted unknowns.
- **Model guidance expiration notice** — Quarterly re-verification reminder for model-specific scaling advice.
- **Automated benchmark runners** — `benchmarks/run_benchmarks.js` (Node.js) and `benchmarks/run_benchmarks.py` (Python).
- **Graceful guide.md fallback** — Loading Rule now explicitly handles missing/empty reference file without stalling.

### Changed
- README comparison table updated from v10 to v11 with honest scope footnote.
- Token savings benchmarks reframed as estimates with methodology disclosure.

---

## [v10] — 2026-07

### Added
- **Dynamic Skill Routing & Anti-Skill Hell Protocol** — Automatically instructs target AI agents to scan locally installed skills (`~/.gemini/config/skills/`, `.agents/skills/`, installed plugins/MCP) or perform a targeted web/internet search for domain-specific community skills before writing code.
- **Meta-Skill positioning** — Prompt Optimizer now functions as an orchestration layer that discovers, routes to, and invokes other specialized skills dynamically.
- Zero hardcoded skill names — matching happens dynamically on task domain keywords.

---

## [v9] — 2026-06

### Added
- **Open-source model support** — Dedicated syntax adapter and scaling rules for Llama, Mistral, DeepSeek, and Qwen.
- **Negative optimization examples** — "What Bad Optimization Looks Like" section with anti-patterns.
- **PII/sensitive data handling** guidance.

### Changed
- SKILL.md reduced from 444 to ~280 lines by moving examples to `references/guide.md`.
- Merged Step 3 + Step 3.5 into unified "Tier, Scale & Adapt" step.
- Compacted anti-patterns table.
- Strengthened Gate 2 assumption-documentation for >2 unknowns.

---

## [v8] — 2026-05

### Added
- **Gate 3 structural enforcement** with hard decision tree and inline example.
- **Model-aware output scaling** (Frontier / Mid-range / Lightweight tiers).
- **Accessibility expansion** — ARIA labels, WCAG AA contrast (≥ 4.5:1), keyboard navigation alongside responsive design for all UI tasks.
- 3 new worked examples (Light-creative/UI, data-transformation, prompt-chaining).
- **Security hardening** — 4 real-world injection attack examples and production checklist.
- **Benchmark test suite** (manual, free, 10 tests).
- Context cost reduction via loading directive.
- Difficulty calibration in output format.
- Feedback loop for iterative improvement.

---

## [v7] — 2026-04

### Added
- **Model Syntax Adapters** — Claude XML tags vs Gemini H2 headers vs GPT System Delimiters vs Agentic IDE tags.
- **Memory & Preference Layering** — `# Assistant Response Preferences` integration.
- **Agent Lifecycle Status Signals** — `result: <deliverable>`, `needs input: <blocker>`, `failed: <reason>`.

### Changed
- Integrated production system prompt principles from analyzed leaked prompts (Claude Code, Cursor, Gemini 3, OpenAI Codex/Memory).

---

## [v6.1] — 2026-03

### Added
- Restored Prompt Security section.
- Extended guide content (Non-Goals, Prompt Chaining, Domain Adaptation, Anti-Patterns Extended, 3 worked examples).
- Execution mode detection heuristics.
- Light Tier and Chat Response Mode examples.

---

## [v6] — 2026-02

### Added
- **Active Agent Execution Framing** — Commands direct workspace file editing, implementation plans, and verification commands instead of passive code blocks in chat.
- Reasoning Models ("Thinking Mode") guidance.

---

## [v5] — 2026-01

### Changed
- Split into lean runtime `SKILL.md` (~210 lines) + `references/guide.md`.
- Adopted Gate-based processing and interactive pre-draft interview.

---

## [v4]

### Changed
- Architectural rewrite: Gates 1-3, Definitions, Domain Adaptation, Prompt Security, JSON Schema.

---

## [v3]

### Added
- Prompt Security, Domain Adaptation, Testing Suggestions, Self-Improvement pass, Prompt Chaining, JSON Schema, Light tier example.

---

## [v2]

### Added
- Activation Guard.
- Concrete tier thresholds.

### Changed
- Replaced numeric self-score with Remaining Risks.
- Added Step 6.

---

## [v1]

- Initial release.
