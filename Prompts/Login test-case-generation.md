# Prompt: Test Case Generation

**Purpose:** Used to convert existing test scenarios into detailed, step-by-step manual test cases that a tester can execute directly.

**Used with:** `test-scenarios/login-test-scenarios.xlsx`
**Produces:** `test-cases/login-test-cases.xlsx`

---

## Prompt Template

```
Convert these test scenarios into detailed manual test cases.

For each test case include:

- Test Case ID
- Requirement ID
- Test Case Title
- Preconditions
- Test Data
- Test Steps
- Expected Result
- Priority
- Test Type

Use the following priority values:
High
Medium
Low

Do not invent functionality that isn't present in the requirements.
```

---

## Notes

- This prompt assumes the test scenarios (Scenario ID, Requirement ID, description, expected result) are already available in context or attached.
- **"Do not invent functionality that isn't present in the requirements"** prevents the model from adding unstated behavior (e.g., specific character limits, lockout rules) directly into test steps or expected results.
- Any test case that necessarily depends on an undefined value (e.g., "enter a username at the maximum length boundary") should note in its **Test Data** or **Preconditions** that the exact value is a placeholder pending confirmation against the real system spec.
- Priority should reflect risk to core functionality (authentication, mandatory fields) as **High**, with boundary/assumption-dependent cases typically **Medium** or **Low**.
