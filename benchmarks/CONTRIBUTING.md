# Contributing Benchmark Tests

Thank you for helping improve the Prompt Optimizer benchmark suite! This guide explains how to submit new test cases.

## Test Case Format

Each test case in `test_prompts.md` follows this template:

```markdown
## Test N: [Title] ([Expected Gate Behavior])

- **Raw**: "[The exact prompt a user would type]"
- **Expected tier**: Light | Standard | Heavy
- **Expected gate**: Gate 2 / Gate 3 → [expected behavior]
- **Target model**: [Model name or "Any"]
- **Evaluation criteria**:
  - [ ] [Specific, measurable assertion]
  - [ ] [Another assertion]
  - [ ] [...]
- **Pass condition**: [One-sentence summary of what "passing" looks like]
```

## Guidelines

1. **Be specific** — Each evaluation criterion should be objectively verifiable (yes/no), not subjective ("looks good").
2. **Cover a gap** — Before adding a test, check if existing tests already cover that tier + domain + gate combination.
3. **Include the expected gate** — This is critical for validating Gate 3 anti-bloat behavior.
4. **Keep raw prompts realistic** — Use prompts that real users actually type, not artificially constructed edge cases.
5. **One domain per test** — Don't mix concerns (e.g., "fix my API and also add dark mode").

## What We Need Most

| Gap | Description |
|---|---|
| **Multi-language** | Tests with non-English raw prompts |
| **Mobile/Flutter** | Mobile app development domain |
| **DevOps/Infra** | CI/CD, Docker, Kubernetes prompts |
| **ML/Data Science** | Model training, data pipeline prompts |
| **Gate 1 (Reject)** | Prompts that should be rejected as harmful/impossible |

## Running Benchmarks

After adding your test, run the automated suite to verify parsing:

```bash
# Node.js
node benchmarks/run_benchmarks.js --verbose

# Python
python benchmarks/run_benchmarks.py --verbose
```

## Submitting

1. Fork the repository
2. Add your test case(s) to `benchmarks/test_prompts.md`
3. Run the benchmark suite to verify no parsing errors
4. Open a Pull Request with a description of what gap your test covers
