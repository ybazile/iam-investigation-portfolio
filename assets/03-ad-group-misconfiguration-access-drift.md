# 📁 Project 3 — AD Group Misconfiguration & Access Drift Investigation

**Status:** Complete

## Overview

This investigation reviews the group memberships assigned to user Roronoa Zoro and identifies excessive or outdated access that resulted in privilege drift. The goal was to validate current access, determine what is legitimate, and remove anything unnecessary.

## Environment & Tools

- **Platform:** Microsoft Entra ID
- **Tools Used:** User blade, Group blade, Audit Logs
- **Scope:** Group-based access review for one user

## Problem Scenario

During a routine access review, Zoro appeared to have more access than required for his role. His group memberships suggested:

- Leftover project access
- Elevated admin access
- Legitimate operational access

This triggered a privilege drift investigation.

## Evidence — Before Remediation

### User's Initial Group Memberships

A screenshot was captured showing Zoro assigned to three groups:

- **Operations Team**
- **Project Phoenix – Temporary Access**
- **App Admin – Marketing Portal**

This confirmed the presence of both leftover and elevated access.

### Group Purpose Evidence

Each group's Overview page was captured to document its intended purpose:

- **Operations Team:** Core operations staff
- **Project Phoenix – Temporary Access:** Temporary project access
- **App Admin – Marketing Portal:** Elevated admin access for a specific application

### Audit Evidence

Audit logs showed multiple **"Add member to group"** events for Zoro, confirming manual assignment activity.

> Re-add screenshots from your original captures — see repo root README for details.

## Analysis

### Classification of Each Group

- **Operations Team → Legitimate** — Matches Zoro's role and should remain.
- **Project Phoenix – Temporary Access → Leftover** — Access was granted for a quick task related to the project. The task ended, but the user was never removed from the group.
- **App Admin – Marketing Portal → Excessive** — Elevated admin access not required for his job.

### Root Cause

Privilege drift occurred due to:

- Lack of periodic access reviews
- Manual group assignments
- No automated expiration for temporary access
- No governance controls around admin group membership

## Remediation

### Actions Taken

Zoro was removed from:

- **Project Phoenix – Temporary Access**
- **App Admin – Marketing Portal**

He remains only in:

- **Operations Team**

### Evidence — After Remediation

A screenshot was captured showing Zoro with only one group membership, confirming successful cleanup.

## Prevention & Hardening

To prevent similar drift in the future:

- Implement Access Reviews for all security groups
- Use Privileged Identity Management (PIM) for admin roles
- Apply expiration policies for temporary project access
- Require manager approval for elevated access
- Maintain a quarterly access certification process

## Final Verdict

This investigation confirmed that Zoro had:

- One legitimate access
- One leftover access
- One excessive admin access

All unnecessary access was removed, restoring the principle of least privilege. The user's access is now clean, appropriate, and aligned with job responsibilities.
