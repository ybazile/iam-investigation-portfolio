# 📁 Project 1 — Okta MFA Failure Investigation

**Status:** Complete

## Overview

A staff member was unable to access the Okta Dashboard due to repeated MFA prompts they could not satisfy. The user's password was accepted, but the login flow stopped at the MFA step. This investigation documents the authentication failure, System Log analysis, root cause, and remediation.

## Environment & Tools Used

- Okta Admin Console
- Okta System Log
- Okta Sign-On Policies
- macOS (user endpoint)
- Private/Incognito browser session for reproduction

## Problem Scenario

The user reported that they were unable to complete MFA during login. Password authentication succeeded, but Okta repeatedly prompted for MFA enrollment and would not allow access to the dashboard.

## Timeline of Events

- **23:08:27 — Sign-on policy evaluated (CHALLENGE)**
  Okta reviewed the login attempt and determined that MFA was required before granting access.
- **23:08:27 — MFA requirement triggered (CHALLENGE)**
  Okta checked for an enrolled MFA method. None were configured, so the user could not satisfy the MFA challenge.
- **23:09:10 — Password authentication succeeded (SUCCESS)**
  The user entered the correct password, but without an enrolled MFA factor, the login flow could not continue.

## Screenshots & Evidence

> Re-add these from your original captures — see repo root README for details.

- User profile – no MFA enrolled
- MFA enrollment prompt (Okta Verify required)
- System Log – authentication via MFA (password SUCCESS)
- System Log – account management policy CHALLENGE
- System Log – sign-on policy CHALLENGE

## Investigation Steps

- Checked the user's profile in Okta Directory and confirmed the account was active.
- Reviewed the user's enrolled authenticators and verified **none were configured**.
- Reviewed the Sign-On Policy and confirmed MFA was required for this user.
- Reproduced the login attempt using a private browser session on macOS.
- Observed the user being redirected directly to the **Okta Verify enrollment screen** after password entry.
- Analyzed System Log events showing:
  - **Password authentication SUCCESS**
  - **Sign-on policy CHALLENGE**
  - **Account management policy CHALLENGE**
- Confirmed the login flow failed because the user had no enrolled MFA method to satisfy the challenge.

## Root Cause Identified

The authentication failure occurred because the user had no enrolled MFA authenticators, while the active sign-on and account management policies required Okta Verify. The password step succeeded, but the login flow could not continue because the user had no valid factor to satisfy the MFA challenge.

## Fix Applied

- Reset the user's authenticators in Okta.
- Guided the user through enrolling Okta Verify on their device.
- Confirmed successful MFA enrollment.
- Verified successful authentication in the System Log after enrollment.

## Prevention / Hardening

- Add an onboarding checkpoint to ensure all new users complete MFA enrollment before their first login.
- Updated internal documentation to include MFA enrollment verification steps.
- Run periodic audits to identify accounts missing required MFA factors and remediate them proactively.

## Key Takeaways

- MFA failures often stem from missing or incomplete enrollment.
- Okta System Log provides clear visibility into authentication flow and policy decisions.
- Ensuring MFA enrollment during onboarding prevents downstream access issues.
