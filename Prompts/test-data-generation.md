# Prompt: Test Data Generation

**Purpose:** Used to generate concrete input values (usernames, passwords, and edge-case strings) needed to execute the manual test cases.

**Used with:** `requirements/login-requirement.md`
**Produces:** `test-data/login-test-data.xlsx`

---

## Prompt Template

```
Based only on the login requirements above,
generate test data for manual testing.

Include:

1. Valid username/password
2. Invalid username
3. Invalid password
4. Empty username
5. Empty password
6. Very long username
7. Very long password
8. Special characters
9. Leading/trailing spaces

Do not assume a specific username/password length unless
the requirement specifies one. Mark assumptions separately.
```

---

## Notes

- **"Do not assume a specific username/password length unless the requirement specifies one"** is the key constraint — most login requirements never define min/max lengths, so any concrete length used for "very long" test data is an arbitrary stress-test value, not a real system boundary.
- **"Mark assumptions separately"** means every assumed value or behavior (length limits, whitespace trimming behavior, permitted special characters, case-sensitivity) must be clearly labeled as an assumption, not presented as fact.
- Test data covering security-related strings (e.g., SQL-injection or script-injection style input) does not require a length/format assumption — the concept is directly justified by input-handling and security concerns, independent of any undefined length rule.
- Output should make it easy to separate "ready-to-use data" from "data that depends on confirming an assumption first" (e.g., via a dedicated column or summary section).
