# Prompt: Test Scenario Generation

**Purpose:** Used to generate comprehensive test scenarios directly from a set of software requirements, before any detailed test cases are written.

**Used with:** `requirements/login-requirement.md`
**Produces:** `test-scenarios/login-test-scenarios.xlsx`

---

## Prompt Template

```
You are a Senior Software QA Engineer.

I will provide you with software requirements.

Your task is to analyze the requirements and generate
comprehensive test scenarios.

Requirements:

{PASTE REQUIREMENTS HERE}

Generate:

1. Positive test scenarios
2. Negative test scenarios
3. Boundary/edge cases
4. Validation scenarios
5. Security-related test scenarios

For each scenario provide:
- Scenario ID
- Requirement ID
- Scenario description
- Expected result

Do not invent requirements that are not provided.
```

---

## Notes

- The instruction **"Do not invent requirements that are not provided"** is critical — it keeps the model from assuming unstated functionality (e.g., account lockout, password complexity rules, session timeout) that wasn't in the source requirements.
- The five scenario categories (Positive, Negative, Boundary/Edge, Validation, Security) give broad coverage from a single pass.
- Any scenario that depends on an undefined parameter (e.g., field length limits) should be flagged as an assumption rather than silently invented — see `requirement-analysis.md` for a dedicated ambiguity-finding prompt.
