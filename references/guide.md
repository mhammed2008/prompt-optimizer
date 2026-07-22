# Prompt Optimizer — Reference Guide

This document contains the full rationale, extended examples, version history, and design decisions behind the Prompt Optimizer skill. The runtime instructions live in `SKILL.md` — this file is for humans maintaining or learning from the skill.

---

## Design Rationale

### Why Active Agent Framing Over Passive Code Blocks
Traditional prompt engineering guides focus on generating text responses in a chat window. In modern AI development environments (Antigravity, Cursor, Claude Code, GitHub Copilot Workspace), users expect the AI to **act as an autonomous engineer** — inspecting files, editing code directly, creating implementation plans, and running verification commands.

If an optimized prompt asks for "code examples in markdown", AI coding agents will simply print code in chat rather than modifying the codebase. Prompt Optimizer explicitly formats coding prompts with **Direct Workspace Actions** and **File Modification Commands** to drive active execution.

### Why Gates Instead of a Linear Flow
Most prompt optimizers immediately rewrite whatever they receive. The gate system prevents three failure modes:
- **Gate 1** stops the optimizer from polishing harmful requests into professional-sounding instructions.
- **Gate 2** stops the optimizer from fabricating context (tech stacks, frameworks) to fill gaps.
- **Gate 3** stops the optimizer from bloating an already-good prompt just to justify its existence.

---

## Core Principles (Extended)

| Principle | Description |
|---|---|
| **Active Execution** | Command AI agents to edit files, create plans, and run tests directly in the workspace. |
| **Precision** | Every sentence carries intent — remove ambiguity by specifying *what*, *how*, and constraints around it. |
| **Structure** | Use clear section order (Role → Context → Task → Direct Workspace Actions → Constraints → Verification). |
| **Model & Agent Awareness** | Tailor style to the target AI agent or model's strengths. |
| **Token Efficiency** | Cut filler, pleasantries, and redundancy. Maximize signal-to-noise. |
| **Proportionality** | Match the optimized prompt's length to the task's complexity. |

---

## Agentic vs. Passive Prompting Guide

| Feature | Passive Chat Prompt | Active Agent Prompt (Prompt Optimizer) |
|---|---|---|
| **Goal** | Get code snippets to copy/paste | Have the AI edit files and execute tasks |
| **Output Command** | "Provide the code for X" | "Inspect `[file.ext]`, apply changes directly, and verify" |
| **Anti-Instruction** | "Do not include markdown text" | "Do not just output code blocks in chat; modify the workspace files directly" |
| **Workflow** | User copies code manually | Agent modifies code, creates plan, and runs verification commands |

---

## Model & Agent-Specific Strategies (Extended)

### AI Coding Agents (Antigravity, Cursor, Claude Code)
- **Strengths**: File system access, terminal execution, multi-file editing, planning tools.
- **Best Practices**:
  - Always specify target file paths explicitly: `app/Http/Controllers/ScanController.php`.
  - Include an explicit `## Direct Workspace Actions` section listing step-by-step file edits.
  - Instruct the agent to run verification commands (e.g. `npm test`, `php artisan test`, `flutter analyze`).

### Reasoning Models (OpenAI o1/o3, Gemini Thinking, Claude Extended Thinking)
- **Strengths**: Deep architectural reasoning, handling complex logic and constraint interactions.
- **Best Practices**:
  - Focus constraints strictly on the **output format** and **workspace actions**.
  - Avoid forcing detailed step-by-step chain-of-thought instructions; allow the model's internal thinking process to run unconstrained.

---

## Full Worked Examples

### Example 1: Active Agent Coding — Laravel API Caching & Rate Limiting

**Original:**
> "fix rate limit handling in ScanController.php"

**Tier:** Standard | **Execution Mode:** Active Agent Mode

**Turn 1 — Analysis + Question:**
- Target file identified in workspace: `app/Http/Controllers/ScanController.php`
- Goal: Implement caching and exponential backoff to handle external API rate limits legally and resiliently.

**Optimized Prompt:**

```text
## Role
Act as a Senior Backend Security & Laravel Engineer.

## Context
The project workspace contains `app/Http/Controllers/ScanController.php` which proxies requests to an external API (VirusTotal). Currently, frequent requests cause HTTP 429 rate-limiting issues.

## Task
Implement response caching and resilient rate-limit handling directly within `app/Http/Controllers/ScanController.php`.

## Direct Workspace Actions
1. Open and inspect `app/Http/Controllers/ScanController.php`.
2. Wrap external API calls with Laravel's `Cache::remember()` (caching responses by hash/URL for 24 hours).
3. Add `Http::retry(3, 15000)` backoff logic to gracefully pause when HTTP 429 status codes occur.
4. Modify `app/Http/Controllers/ScanController.php` directly in the codebase.

## Constraints
- Do NOT just print code blocks in chat — apply modifications directly to `ScanController.php`.
- Preserve existing method contracts and response schemas.
- Rely on native Laravel facades (`Cache`, `Http`, `RateLimiter`).

## Verification Plan
1. Check that `ScanController.php` compiles cleanly without syntax errors.
2. Confirm caching TTL and retry parameters are properly configured.
```

---

## Version History

- **v6 (current)** — Added **Active Agent Execution Framing** to command direct workspace file editing, implementation plans, and verification commands instead of passive code blocks in chat. Added Reasoning Models ("Thinking Mode") guidance.
- **v5** — Split into lean runtime SKILL.md (~210 lines) + reference guide. Adopted Gate-based processing and interactive pre-draft interview.
- **v4** — Architectural rewrite: Gates 1-3, Definitions, Domain Adaptation, Prompt Security, JSON Schema.
