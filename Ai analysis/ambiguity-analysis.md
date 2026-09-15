# Ambiguity Analysis

## REQ-LOGIN-010

> **Requirement Text:** "The system should lock the user account after multiple failed login attempts."

---

### 1. Ambiguous Language

| # | Term / Phrase | Issue |
|---|---|---|
| 1.1 | **"should"** | Non-mandatory wording. In requirement-writing convention (e.g., RFC 2119 / IEEE 830 style), "shall" indicates a mandatory requirement, while "should" indicates a recommendation. It is unclear whether account lockout is a hard requirement or an optional/best-effort behavior. |
| 1.2 | **"multiple"** | No numeric threshold is given. "Multiple" could mean 3, 5, 10, or any other number of attempts. Without a defined value, the trigger condition for lockout cannot be tested. |
| 1.3 | **"failed login attempts"** | No time window is defined. Are failed attempts counted: within a single session? Within a rolling time window (e.g., 5 attempts in 10 minutes)? Cumulatively without any time limit (i.e., forever, unless reset)? |
| 1.4 | **"lock the user account"** | "Lock" is not defined. Does it mean a temporary lockout that auto-expires after a set duration, or a permanent lock requiring manual/admin intervention to unlock? |

---

### 2. Missing Details / Undefined Parameters

| # | Missing Detail | Why It Matters |
|---|---|---|
| 2.1 | **Failed-attempt threshold** | Cannot design a boundary test (e.g., "locks on the Nth attempt, not the N-1th") without a defined number. |
| 2.2 | **Time window for counting attempts** | Determines whether the counter is session-based, rolling, or lifetime — directly affects test setup and expected results. |
| 2.3 | **Lockout duration** | Unknown whether lockout is temporary (auto-unlocks after X minutes) or indefinite (requires manual reset). Affects both functional and negative test design. |
| 2.4 | **Unlock mechanism** | Not specified whether unlocking happens automatically after a timeout, via email/SMS verification, via CAPTCHA, via password reset, or only via administrator action. |
| 2.5 | **Counter reset condition** | Unclear if the failed-attempt count resets after a successful login, after the lockout duration expires, after a fixed time period, or never resets automatically. |
| 2.6 | **Scope of the lock** | Unclear if lockout is tied to the username/account (affecting the user from any device), to a specific IP address, to a specific device/browser session, or some combination. This significantly changes attack-prevention effectiveness and legitimate-user impact. |
| 2.7 | **User-facing messaging** | No mention of what message (if any) is shown to the user once the account is locked, and whether it differs from the generic "invalid credentials" error required by REQ-LOGIN-004. |
| 2.8 | **Notification to the account owner** | Not specified whether the legitimate user is notified (e.g., via email) that their account was locked, which is a common security/UX expectation. |
| 2.9 | **Behavior on subsequent attempts while locked** | Unclear if the system re-validates credentials and separately reports "account locked," or simply keeps returning a generic invalid-credentials message (which affects whether this could leak account-status information — an enumeration risk). |
| 2.10 | **Administrator/support process** | No mention of whether administrators have a manual unlock capability, or an audit trail of lockout events. |
| 2.11 | **Attempts against non-existent usernames** | Unclear whether failed attempts against a username that doesn't exist are counted the same way as attempts against a valid, existing username (relevant to preventing enumeration attacks). |

---

### 3. Testability Concerns

Because of the ambiguities above, the requirement as written **cannot be directly translated into deterministic test cases**. Specifically:

- A **positive test** ("account locks after the correct number of failed attempts") cannot be authored without a defined threshold.
- A **boundary test** ("locks on attempt N, not N‑1") cannot be authored without a defined threshold.
- A **negative test** verifying the account remains unlocked below the threshold cannot be authored for the same reason.
- Tests covering **lockout expiry** or **manual unlock** cannot be authored without knowing the unlock mechanism.
- Tests verifying whether the system **avoids revealing account-lock status** to an unauthenticated attacker (a security consideration) cannot be authored without knowing the intended messaging behavior.

---

### 4. Recommended Clarifying Questions for Stakeholders

1. Is this requirement **mandatory** ("shall") or a **recommendation** ("should")? Should the wording be corrected?
2. What is the exact **number of failed attempts** that triggers a lock (e.g., 3, 5, 10)?
3. Is the failed-attempt count based on a **time window** (e.g., 5 attempts within 15 minutes), or is it a simple **cumulative counter** with no time limit?
4. Is the lockout **temporary** (auto-unlocks after a defined duration) or **permanent** (requires manual reset)? If temporary, what is the duration?
5. What is the **unlock mechanism** — automatic timeout, self-service (e.g., email link, security questions), CAPTCHA, or administrator-only unlock?
6. Does a **successful login reset** the failed-attempt counter? Does the counter also reset after some elapsed time regardless of success?
7. Is the lock applied at the **account level** (blocks login from any device/location) or scoped to an **IP address / device / session**?
8. What **message** is shown to the user once locked out — and does it differ from the standard invalid-credentials message, or is it identical to avoid revealing account status to an attacker?
9. Is the **account owner notified** (e.g., via email) when their account is locked?
10. Do failed attempts against a **non-existent username** count toward any lockout logic, or does lockout only apply to attempts against a real, existing account?
11. Is there a requirement for **logging/auditing** lockout events for security monitoring purposes?

---

### 5. Suggested Rewritten Requirement (Example — Pending Stakeholder Confirmation)

*This is only a suggested illustration of how the requirement could be clarified once the above questions are answered — it does not represent an assumed or approved requirement.*

> "The system **shall** lock a user account for **[X] minutes** after **[N] consecutive failed login attempts** within a **[Y]-minute window**. While locked, the system shall display a generic error message that does not distinguish a locked account from invalid credentials. The failed-attempt counter shall reset upon a successful login or after the lockout period expires."

---

*This analysis is based solely on the requirement text provided (REQ-LOGIN-010). No lockout behavior, threshold, or duration has been assumed or tested against; all such details remain open until clarified by stakeholders.*
