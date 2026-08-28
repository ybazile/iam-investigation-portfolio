# 📁 Project 2 — Security Investigation: Suspicious Sign-In and Possible Identity Compromise

**Status:** Complete
**User:** Jordan Matthews
**Date:** March 7, 2026

## Executive Summary

- Unusual sign-in activity was detected on the Jordan Matthews account.
- Activity included a sign-in attempt from Singapore and several failed password attempts from Florida.
- The pattern suggested possible credential misuse or probing behavior.
- Sign-in logs were reviewed, authentication patterns analyzed, and remediation steps applied.
- No successful compromise occurred, but the activity was treated as a legitimate security concern.

## Timeline of Events

- **8:00 AM (Florida):** First-time sign-in, password change required.
- **8:03 AM (Florida):** MFA registration triggered but not completed.
- **8:30 AM (Singapore):** Sign-in attempt from an unfamiliar region; MFA required; attempt did not complete.
- **5:36–5:37 PM (Florida):** Multiple failed password attempts in rapid succession, all showing invalid credentials.

## Screenshots & Evidence

> Re-add these from your original captures — see repo root README for details.

## Log Analysis

- The Singapore attempt came from a region and IP not associated with the user.
- The attempt stopped at the MFA stage, which is consistent with someone testing stolen or guessed credentials.
- The failed password attempts from Florida happened within seconds of each other, which looks more like automated guessing than a typical user mistake.
- The earlier legitimate sign-in helped establish what normal behavior looks like for this account.
- Taken together, the events suggested probing activity rather than normal user behavior.

## Root Cause

- The Singapore sign-in was likely an unauthorized attempt using Jordan's username.
- The failed attempts from Florida resembled brute-force or password-spray behavior.
- None of the attempts resulted in a successful sign-in, and MFA prevented the foreign attempt from progressing.
- The account was not compromised, but the activity indicated a credible identity-based attack attempt.

## Remediation

- Reset the user's password.
- Required MFA enrollment.
- Revoked all active sessions.
- Reviewed authentication methods for anything unusual.
- Checked audit logs for additional activity.
- Monitored the account for further sign-ins.
- Notified the user and provided guidance on password hygiene.

## Validation

- No additional suspicious activity appeared in the logs after remediation.
- MFA registration completed successfully.
- Password reset confirmed.
- All active sessions were cleared.
- Account behavior returned to normal.

## Recommendations

- Enforce MFA for all users.
- Monitor sign-in logs regularly.
- Educate users about phishing and credential safety.
- Implement Conditional Access and Identity Protection if licensing becomes available.
- Encourage strong, unique passwords and avoid password reuse.
