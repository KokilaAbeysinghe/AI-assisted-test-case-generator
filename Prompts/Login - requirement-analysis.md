# Prompt: Requirement Ambiguity Analysis

**Purpose:** Used to critically analyze a single requirement (typically one that uses vague or non-mandatory language) and surface ambiguities, missing details, and testability gaps before test scenarios/cases are written against it.

**Used with:** A single requirement, e.g. `REQ-LOGIN-010`
**Produces:** `ai-analysis/ambiguity-analysis.md`

---

## Prompt Template

```
{PASTE REQUIREMENT ID AND TEXT HERE}

Identify ambiguities in this requirement.
```

---

## Notes

- This prompt works best on requirements that contain vague qualifiers ("should," "multiple," "appropriate," "reasonable," etc.) or omit concrete parameters (thresholds, durations, formats).
- A thorough response should cover, at minimum:
  1. **Ambiguous language** — words/phrases open to more than one interpretation.
  2. **Missing details** — parameters or behaviors the requirement doesn't define but that a test case would need.
  3. **Testability concerns** — which specific test types (positive, boundary, negative, security) cannot be authored until the ambiguity is resolved.
  4. **Clarifying questions** — a concrete list to send back to the requirement owner/stakeholder.
- The output should **never guess at a resolution and present it as fact** — a suggested rewritten/clarified version of the requirement may be offered, but only labeled explicitly as an illustrative example pending stakeholder confirmation, not as an assumed final requirement.
- This prompt is intended to run **before** scenario-generation.md for any requirement flagged as ambiguous, so downstream test scenarios/cases aren't built on invented behavior.
