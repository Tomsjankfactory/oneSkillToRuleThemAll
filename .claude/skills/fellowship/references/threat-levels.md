# Threat Levels

Classify each task before execution. Apply the minimum required controls.

## Contents

- [The Shire](#the-shire)
- [The Wilds](#the-wilds)
- [Isengard](#isengard)
- [Mount Doom](#mount-doom)
- [Risk Classification Decision Tree](#risk-classification-decision-tree)
- [Failure-Mode Checklist](#failure-mode-checklist)
- [Ally Deployments](#ally-deployments)

## The Shire

Criteria:
- Low blast radius.
- Easy rollback.
- No sensitive data, security, or compliance impact.

Required controls:
- Basic validation evidence.
- Record rollback step.

## The Wilds

Criteria:
- User-visible behavior changes.
- Moderate reliability or cost impact.
- Partial coupling to other tasks.

Required controls:
- Independent review by non-author agent.
- Validation evidence plus negative test or failure case.
- Explicit rollback note in task output.

## Isengard

Criteria:
- Security, privacy, compliance, or data integrity implications.
- High customer or financial blast radius.
- Difficult rollback or uncertain side effects.

Required controls:
- Dedicated Palantir-bearer participation.
- Adversarial review with failure-mode checklist.
- Pre-merge or pre-release go/no-go checkpoint by Gandalf.
- Staged rollout or guarded launch when possible.

## Mount Doom

Criteria:
- Irreversible actions.
- Regulated or safety-sensitive effects.
- Mission failure likely causes severe incident.

Required controls:
- Keep scope minimal and isolate risky changes.
- Require explicit human confirmation before irreversible action.
- Two-step verification and documented contingency plan.
- If controls are unavailable, do not execute.

## Risk Classification Decision Tree

Walk through these questions in order. Stop at the first "yes" — that determines the threat level.

**1. Is the action irreversible or regulated?**
   - Could it destroy data with no backup? → **Mount Doom**
   - Does it touch regulated, safety-critical, or compliance-governed systems? → **Mount Doom**
   - Could failure cause a severe incident that cannot be undone? → **Mount Doom**
   - If none apply, proceed to question 2.

   _Examples: Dropping a production database table (Mount Doom), deleting a cloud storage bucket without snapshots (Mount Doom), modifying HIPAA-regulated data pipelines (Mount Doom)._

**2. Does it affect security, privacy, or data integrity?**
   - Does it modify authentication, authorization, or encryption? → **Isengard**
   - Could it expose user data or PII? → **Isengard**
   - Does it have high financial or customer blast radius? → **Isengard**
   - If none apply, proceed to question 3.

   _Examples: Changing auth middleware or token validation (Isengard), updating payment processing logic (Isengard), modifying API rate-limiting or access controls (Isengard)._

**3. Is the change visible to users or coupled to other work?**
   - Does it alter user-facing behavior, UI, or API responses? → **The Wilds**
   - Could it affect reliability, performance, or cost in a noticeable way? → **The Wilds**
   - Is it tightly coupled to other in-flight tasks? → **The Wilds**
   - If none apply, proceed to question 4.

   _Examples: Changing an API response format (The Wilds), updating a shared configuration file (The Wilds), refactoring a function used by multiple modules (The Wilds)._

**4. None of the above?** → **The Shire**
   - Low blast radius, easy rollback, no sensitive impact.

   _Examples: Renaming an internal variable (The Shire), fixing a typo in a code comment (The Shire), adding a unit test for existing logic (The Shire)._

## Failure-Mode Checklist

Run this checklist for The Wilds+ tasks.

- What could fail in production?
- How would we detect it quickly?
- What is the fastest safe rollback?
- What dependency could invalidate this plan?
- What assumption is least certain?

## Ally Deployments

Ally deployments inherit the parent Company's threat level:

- **The Shire / The Wilds:** Quest Leader deploys at discretion. No Gandalf approval required.
- **Isengard:** Quest Leader must signal Gandalf and receive approval before deploying allies.
- **Mount Doom:** Ally deployment is not permitted. All Mount Doom-tier work requires explicit Valar (human) confirmation.
