# Threat Levels

Classify each task before execution. Apply the minimum required controls.

## Contents

- [The Shire](#the-shire)
- [Weathertop](#weathertop)
- [Helm's Deep](#helms-deep)
- [The Crack of Doom](#the-crack-of-doom)
- [Risk Classification Decision Tree](#risk-classification-decision-tree)
- [Failure-Mode Checklist](#failure-mode-checklist)
- [Ally Deployments](#ally-deployments)

## The Shire

> *"The world is indeed full of peril... but still there is much that is fair."*

Peace. Second breakfast. The road is easy.

Criteria:
- Low blast radius.
- Easy rollback.
- No sensitive data, security, or compliance impact.

Required controls:
- Basic validation evidence.
- Record rollback step.

## Weathertop

> *"Something draws near. I can feel it."*

First real danger. The Nazgul are out there. Proceed with caution — a scout confirms the path ahead.

Criteria:
- User-visible behavior changes.
- Moderate reliability or cost impact.
- Partial coupling to other tasks.

Required controls:
- Independent review by non-author agent.
- Validation evidence plus negative test or failure case.
- Explicit rollback note in task output.

## Helm's Deep

> *"So it begins."*

Open war. The walls are manned. No shortcuts, no side doors.

Criteria:
- Security, privacy, compliance, or data integrity implications.
- High customer or financial blast radius.
- Difficult rollback or uncertain side effects.

Required controls:
- Dedicated Palantir-bearer participation.
- Adversarial review with failure-mode checklist.
- Pre-merge or pre-release go/no-go checkpoint by Gandalf.
- Staged rollout or guarded launch when possible.

## The Crack of Doom

> *"Cast it into the fire! Destroy it!"*

The final irreversible step. There is no coming back from this. Every member of the Fellowship knows the stakes.

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
   - Could it destroy data with no backup? → **The Crack of Doom**
   - Does it touch regulated, safety-critical, or compliance-governed systems? → **The Crack of Doom**
   - Could failure cause a severe incident that cannot be undone? → **The Crack of Doom**
   - If none apply, proceed to question 2.

   _Examples: Dropping a production database table (The Crack of Doom), deleting a cloud storage bucket without snapshots (The Crack of Doom), modifying HIPAA-regulated data pipelines (The Crack of Doom)._

**2. Does it affect security, privacy, or data integrity?**
   - Does it modify authentication, authorization, or encryption? → **Helm's Deep**
   - Could it expose user data or PII? → **Helm's Deep**
   - Does it have high financial or customer blast radius? → **Helm's Deep**
   - If none apply, proceed to question 3.

   _Examples: Changing auth middleware or token validation (Helm's Deep), updating payment processing logic (Helm's Deep), modifying API rate-limiting or access controls (Helm's Deep)._

**3. Is the change visible to users or coupled to other work?**
   - Does it alter user-facing behavior, UI, or API responses? → **Weathertop**
   - Could it affect reliability, performance, or cost in a noticeable way? → **Weathertop**
   - Is it tightly coupled to other in-flight tasks? → **Weathertop**
   - If none apply, proceed to question 4.

   _Examples: Changing an API response format (Weathertop), updating a shared configuration file (Weathertop), refactoring a function used by multiple modules (Weathertop)._

**4. None of the above?** → **The Shire**
   - Low blast radius, easy rollback, no sensitive impact.

   _Examples: Renaming an internal variable (The Shire), fixing a typo in a code comment (The Shire), adding a unit test for existing logic (The Shire)._

## Failure-Mode Checklist

Run this checklist for Weathertop+ tasks.

- What could fail in production?
- How would we detect it quickly?
- What is the fastest safe rollback?
- What dependency could invalidate this plan?
- What assumption is least certain?

## Ally Deployments

Ally deployments inherit the parent Company's threat level:

- **The Shire / Weathertop:** Quest Leader deploys at discretion. No Gandalf approval required.
- **Helm's Deep:** Quest Leader must sound the Horn of Gondor and receive Gandalf's approval before deploying allies.
- **The Crack of Doom:** Ally deployment is not permitted. All Crack of Doom-tier work requires explicit Valar (human) confirmation.
