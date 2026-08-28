# 🔐 IAM Investigation Portfolio
> **Identity-Focused Investigations, Authentication Troubleshooting, and Access Governance Documentation**

![Okta](https://img.shields.io/badge/Okta-Identity-blue?logo=okta)
![Azure](https://img.shields.io/badge/Azure-Entra%20ID-0089D6?logo=microsoftazure)
![IAM](https://img.shields.io/badge/IAM-Investigations-green)
![Access Review](https://img.shields.io/badge/Access-Review-orange)
![Incident Response](https://img.shields.io/badge/Incident-Response-red)

## Executive Summary

This repo is a centralized hub for identity-focused investigations, authentication troubleshooting, and security-minded documentation. Each project reflects a real-world IAM workflow — MFA failures, suspicious sign-ins, and access reviews — documented the way an identity/security team would document an incident: environment, timeline, log evidence, root cause, remediation, and hardening recommendations.

Three investigations are included, spanning two identity platforms (Okta and Microsoft Entra ID) and three distinct problem types: authentication failure, credential compromise/probing, and privilege drift.

### Skills Demonstrated
- Okta Admin Console & System Log analysis
- Microsoft Entra ID (Azure AD) group and audit log review
- MFA policy evaluation and enrollment troubleshooting
- Sign-in log analysis / identity threat detection
- Access review and least-privilege remediation
- Root-cause analysis and incident documentation
- Endpoint reproduction and testing (macOS/Windows, private browser sessions)

---

## Investigation Tracker

| # | Project | Platform | Focus | Status |
|---|---|---|---|---|
| 1 | [Okta MFA Failure Investigation](projects/01-okta-mfa-failure-investigation.md) | Okta | MFA enrollment failure, policy evaluation, System Log | ✅ Complete |
| 2 | [Suspicious Sign-In & Identity Compromise Investigation](projects/02-suspicious-signin-identity-compromise.md) | Okta | Sign-in anomalies, credential probing, remediation | ✅ Complete |
| 3 | [Azure Access Review & Privilege Drift Investigation](projects/03-ad-group-misconfiguration-access-drift.md) | Microsoft Entra ID | Group-based access review, privilege drift, least privilege | ✅ Complete |

---

# Investigation Summaries

## Investigation 1 — Okta MFA Failure Investigation

**Focus:** A staff member's login stopped at the MFA step after password success. Investigated via Okta System Log and Sign-On Policy review.

**Root Cause:** No MFA authenticators were enrolled for the user, while active policy required Okta Verify — the login flow had no valid factor to satisfy the challenge.

**Fix:** Reset authenticators, guided user through Okta Verify enrollment, confirmed successful authentication afterward.

**Full write-up →** [`projects/01-okta-mfa-failure-investigation.md`](projects/01-okta-mfa-failure-investigation.md)

---

## Investigation 2 — Suspicious Sign-In & Identity Compromise Investigation

**Focus:** Sign-in activity on one account included an attempt from Singapore and rapid-fire failed password attempts from Florida — a pattern consistent with credential probing.

**Root Cause:** Likely unauthorized sign-in attempt using the account's username, plus brute-force/password-spray-style activity. MFA prevented the foreign attempt from progressing; no compromise occurred.

**Fix:** Password reset, forced MFA enrollment, revoked all active sessions, monitored for further activity.

**Full write-up →** [`projects/02-suspicious-signin-identity-compromise.md`](projects/02-suspicious-signin-identity-compromise.md)

---

## Investigation 3 — Azure Access Review & Privilege Drift Investigation

**Focus:** Routine access review flagged a user with more group memberships than their role required.

**Root Cause:** Privilege drift from manual group assignment, no automated expiration on temporary access, and no governance controls on admin group membership.

**Fix:** Removed leftover (`Project Phoenix – Temporary Access`) and excessive (`App Admin – Marketing Portal`) group memberships, leaving only the legitimate `Operations Team` assignment.

**Full write-up →** [`projects/03-ad-group-misconfiguration-access-drift.md`](projects/03-ad-group-misconfiguration-access-drift.md)

---

# Key Findings

- Diagnosed and resolved an MFA enrollment gap by cross-referencing Okta System Log policy-evaluation events (`CHALLENGE`) against the user's enrolled-authenticator state.
- Distinguished credential-probing activity from normal user behavior by correlating sign-in geography, timing patterns, and MFA-stage drop-off across a single account's log history.
- Identified and remediated privilege drift by classifying each group membership against its documented purpose and the user's actual role, restoring least privilege.
- Documented full timelines, evidence, and remediation steps for each investigation in a format consistent with real identity/security team incident documentation.

---

# Tools & Environment

- **Okta Admin Console** — MFA, policies, System Log
- **Microsoft Entra ID (Azure AD)** — group management, audit logs, access reviews
- **macOS / Windows** — endpoint reproduction and testing
- **Private/Incognito Sessions** — clean authentication testing
- **Browser DevTools** — redirect flow inspection
- **Log Analysis** — authentication events, group membership changes

---

# Detection & Governance Opportunities

- Add an MFA-enrollment checkpoint to onboarding to prevent repeat failures like Investigation 1.
- Enforce MFA universally and monitor sign-in logs for geography/timing anomalies like those in Investigation 2.
- Implement Conditional Access and Identity Protection where licensing allows.
- Run periodic Access Reviews and apply expiration policies to temporary group access to prevent drift like Investigation 3.
- Use Privileged Identity Management (PIM) for admin-tier roles instead of standing group membership.
- Require manager approval for elevated access grants.

---

# Repo Structure

```
iam-investigation-portfolio/
├── README.md
├── projects/
│   ├── 01-okta-mfa-failure-investigation.md
│   ├── 02-suspicious-signin-identity-compromise.md
│   └── 03-ad-group-misconfiguration-access-drift.md
└── assets/
    └── (screenshots)
```

---

# Resume Highlights

This project demonstrates my ability to:

- Investigate and resolve real IAM authentication failures using platform-native log tooling (Okta System Log)
- Detect and respond to suspicious sign-in activity, including credential-probing patterns
- Conduct access reviews and remediate privilege drift to restore least privilege
- Document security investigations clearly, with full timelines, evidence, root cause, and remediation
- Work across multiple identity platforms (Okta, Microsoft Entra ID)

---

## Author

**Yvener Bazile**

Cloud Security • SOC Analyst • Azure • Okta • IAM
