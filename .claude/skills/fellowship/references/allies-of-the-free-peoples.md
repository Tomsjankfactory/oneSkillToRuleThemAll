# Allies of the Free Peoples

Allies of the Free Peoples are short-lived sub-agents a Quest Leader deploys for focused, independent objectives in service of the Company's task. They are doctrinally distinct from companions: companions subdivide the Company's deliverable, allies execute discrete sorties and return.

## Deploy-or-Escalate Decision

Choose the first condition that matches.

1. Quick recon of unfamiliar area → **Ranger of the North**
2. Targeted fix or small implementation to unblock Company → **Rider of Rohan**
3. Quick config/build/infra task → **Ent of Fangorn**
4. Sustained work, own deliverable, needs file ownership → **NOT an ally.** Request a new Company from Gandalf.
5. Work that subdivides the Company's main deliverable → **NOT an ally.** Muster the role instead.

## Ally Specialisations

| Type | Function | subagent_type | Use case |
|---|---|---|---|
| Ranger of the North | Reconnaissance & intel gathering | Explore (read-only) | Scout unfamiliar code, gather findings |
| Rider of Rohan | Direct action, targeted changes | general-purpose | Small fix, unblock a dependency |
| Ent of Fangorn | Engineering support | general-purpose | Quick config, build, infra task |

### Read-Only Specialisation

Rangers of the North use the `Explore` subagent type. They cannot modify files. They report findings to the Quest Leader, who decides how to act on them.

## Deployment Rules

- **Max 2 allies per Company at any time.** If the task needs more, it is companion work or a new Company.
- **Allies cannot deploy allies.** No recursion permitted.
- **Allies report only to their deploying Quest Leader.** They do not communicate with companions or other Companies.
- **Quest Leader must verify ally output** before incorporating it into the Company's deliverable.
- **Allies do not get Company names.** Identify them as: `Free Peoples Detachment, Company [Name] — [objective]`.

## Threat Level Interaction

Ally deployments inherit the parent Company's threat level:

- **The Shire / Weathertop:** Quest Leader deploys at discretion. No Gandalf approval required.
- **Helm's Deep:** Quest Leader must sound the Horn of Gondor and receive Gandalf's approval before deploying allies.
- **The Crack of Doom:** Ally deployment is not permitted. All Crack of Doom-tier work requires explicit Valar (human) confirmation.

## Recovery

Ally recovery is simple. No separate Last Alliance Protocol is needed.

- If an ally is stuck or unresponsive, Quest Leader **abandons the deployment**.
- Quest Leader either redeploys a fresh ally or handles the objective directly.
- If the same ally objective fails twice, Quest Leader **escalates to Gandalf**.

## Deployment Template

When deploying an ally, use the briefing template at `council-templates/ally-deployment-brief.md`.
