# Prompt Optimizer — Benchmark Test Suite

> **How to use**: For each test, paste the **Raw Prompt** into your target model, then paste the **Optimized Prompt**. Compare the outputs side-by-side using the evaluation criteria. No API keys needed — works with any free-tier model access.

---

## Test 1: Light-Creative (Gate 3 → Light Rewrite)

- **Raw**: "create a snake game using html css js with modern style"
- **Expected tier**: Light
- **Expected gate**: Gate 3 → Light rewrite (creative task, tech stack clear)
- **Target model**: Gemini Flash
- **Evaluation criteria**:
  - [ ] Game logic complete (snake moves, grows, collision detection, score)
  - [ ] Modern styling (dark theme, gradients, animations)
  - [ ] Responsive layout (works on mobile viewport)
  - [ ] Game-over / restart screen
- **Pass condition**: Optimized prompt produces responsive design + better UI polish without sacrificing game logic

---

## Test 2: Light-Chat (Gate 3 → Skip)

- **Raw**: "format this json file"
- **Expected tier**: Light
- **Expected gate**: Gate 3 → Skip or minimal rewrite
- **Target model**: Any
- **Evaluation criteria**:
  - [ ] Skill recognizes this as already near-optimal
  - [ ] Output is ≤ 3 lines (no heavy structure)
  - [ ] Added only essential constraints (indentation, preserve data)
- **Pass condition**: Skill does NOT produce a full Role/Context/Task structure

---

## Test 3: Standard-Code (Active Agent Mode)

- **Raw**: "fix rate limit handling in ScanController.php"
- **Expected tier**: Standard
- **Expected gate**: Gate 2 (may ask about framework)
- **Target model**: Claude Sonnet or Gemini Flash
- **Evaluation criteria**:
  - [ ] Specifies target file explicitly
  - [ ] Includes Direct Workspace Actions section
  - [ ] Adds caching + retry logic constraints
  - [ ] Includes "do not output code blocks in chat" anti-instruction
  - [ ] Verification step present
- **Pass condition**: Model edits the file directly instead of printing code in chat

---

## Test 4: Standard-Data (Chat Response Mode)

- **Raw**: "convert my csv to json"
- **Expected tier**: Standard
- **Expected gate**: Gate 3 → Standard (2 ambiguities: schema, edge cases)
- **Target model**: GPT-4o or Gemini Flash
- **Evaluation criteria**:
  - [ ] Schema specified (key naming, type casting, null handling)
  - [ ] Edge cases listed (quoted commas, escaped quotes)
  - [ ] Output format locked (no markdown fences)
  - [ ] No unnecessary Role framing (data-transform domain)
- **Pass condition**: Output is valid JSON with correct type casting and edge case handling

---

## Test 5: Standard-Creative (UI Dashboard)

- **Raw**: "build me an admin dashboard"
- **Expected tier**: Standard
- **Expected gate**: Gate 2 (may ask about framework + data)
- **Target model**: Gemini Flash
- **Evaluation criteria**:
  - [ ] Responsive design constraints present (viewport, breakpoints, touch targets)
  - [ ] Accessibility constraints present (ARIA, contrast, keyboard nav)
  - [ ] Specific UI components listed (sidebar, charts, tables, header)
  - [ ] Doesn't over-structure for a creative UI task
- **Pass condition**: Dashboard is responsive on mobile and has accessible interactive elements

---

## Test 6: Heavy-Debug (Full Flow with Questions)

- **Raw**: "my api is broken it returns 500 sometimes fix it"
- **Expected tier**: Heavy
- **Expected gate**: Gate 2 → 2 clarifying questions
- **Target model**: Claude Sonnet
- **Evaluation criteria**:
  - [ ] Skill asks ≤ 2 clarifying questions before generating
  - [ ] Questions target critical context (framework, endpoint, conditions)
  - [ ] Final prompt includes error handling, logging, and backward compatibility
  - [ ] Anti-instructions prevent lazy fixes
- **Pass condition**: Model diagnoses root cause (e.g., connection pool, unhandled promise) not just adds try/catch

---

## Test 7: Heavy-Fullstack (Multi-Service)

- **Raw**: "build me a full-stack task app"
- **Expected tier**: Heavy
- **Expected gate**: Gate 2 (may ask about tech stack)
- **Target model**: Claude Opus or GPT-5
- **Evaluation criteria**:
  - [ ] Decomposed into prompt chain (≥ 2 prompts)
  - [ ] Each prompt scoped to single concern
  - [ ] Handoff points defined between prompts
  - [ ] Integration / verification step included
- **Pass condition**: Each prompt produces working code; combined result runs as a full app

---

## Test 8: Standard-Security (Auth Flow)

- **Raw**: "add login to my express app"
- **Expected tier**: Standard
- **Expected gate**: Gate 2 (auth method, session storage)
- **Target model**: Gemini Flash
- **Evaluation criteria**:
  - [ ] Specifies auth method (JWT, session, OAuth)
  - [ ] Includes password hashing constraint (bcrypt)
  - [ ] CORS and security headers mentioned
  - [ ] Direct workspace actions present
  - [ ] "Do not store plaintext passwords" anti-instruction
- **Pass condition**: Generated auth code uses bcrypt, httpOnly cookies, and proper error handling

---

## Test 9: Heavy-Refactor (Cross-Module)

- **Raw**: "refactor the codebase to use dependency injection"
- **Expected tier**: Heavy
- **Expected gate**: Gate 2 (language, framework, DI pattern)
- **Target model**: Claude Opus
- **Evaluation criteria**:
  - [ ] Asks about language and framework before generating
  - [ ] Lists specific files/modules to refactor
  - [ ] Preserves existing interfaces and contracts
  - [ ] Includes verification (tests still pass)
  - [ ] Anti-instruction: don't change public API surface
- **Pass condition**: Refactored code compiles, tests pass, and DI pattern is consistent across modules

---

## Test 10: Prompt Chaining (3-Prompt Sequence)

- **Raw**: "build a real-time chat app with rooms"
- **Expected tier**: Heavy → Chain
- **Expected gate**: Decomposition into 3 prompts
- **Target model**: Any
- **Evaluation criteria**:
  - [ ] Prompt 1: Backend (WebSocket server, room management)
  - [ ] Prompt 2: Frontend (chat UI, room list, message display)
  - [ ] Prompt 3: Integration (connect frontend to backend, test real-time messaging)
  - [ ] Each prompt independently runnable
  - [ ] Handoff points explicit
- **Pass condition**: All 3 prompts, run sequentially, produce a working real-time chat app

---

## Scoring Guide

| Result | Meaning |
|---|---|
| **10/10 tests pass** | Skill is production-ready |
| **8-9/10 pass** | Minor edge cases to address |
| **6-7/10 pass** | Significant gaps in coverage |
| **< 6/10 pass** | Needs architectural revision |

---

## Model-Scaling Verification

Run Tests 1, 4, and 5 on each model class to verify model-aware scaling:

| Model Class | Expected Behavior |
|---|---|
| **Frontier** (Opus, GPT-5) | Full structural output for Standard+ tasks |
| **Mid-range** (Sonnet, Flash) | Simplified output, imperative style for Standard |
| **Lightweight** (Haiku, mini) | Light tier only, 2-3 sentence prompts, warning if task needs Standard+ |
