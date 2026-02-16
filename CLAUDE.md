# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

TheFellowship -- a Lord of the Rings-themed multi-agent coordination skill for Claude Code, adapted from the [Nelson skill](https://github.com/harrymunro/nelson). Nelson uses Royal Navy metaphors (Admiral, Captains, Crew, Ships) to orchestrate parallel agent teams. TheFellowship replaces every naval concept with a Middle-earth equivalent while preserving all operational logic, decision trees, governance rules, and templates exactly.

Invoked with `$gandalf`.

## Source Reference

Every file in this skill maps 1:1 to a Nelson file. When implementing, fetch the Nelson source from `https://raw.githubusercontent.com/harrymunro/nelson/main/` and re-theme it. Do not invent new operational logic -- only change terminology.

## Character-to-Role Mapping

### Three-Tier Hierarchy

| Tier | Nelson | Fellowship | Character |
|---|---|---|---|
| Strategic Coordinator | Admiral | The White Council | **Gandalf** -- delegates, tracks, never implements |
| Tactical Commander | Captain | Quest Leader | **Aragorn** (primary), any member elevated to lead a Company |
| Human Authority | Admiralty | The Valar | The human operator -- final say on scope/budget/abort |

### Seven Fellowship Roles (replace 7 Navy Crew)

| # | Nelson Role | Fellowship Character | Abbr | Function | subagent_type |
|---|---|---|---|---|---|
| 1 | Executive Officer (XO) | Aragorn (Ranger-King) | RK | Integration & orchestration | general-purpose |
| 2 | Principal Warfare Officer (PWO) | Gimli (Dwarf-Smith) | DS | Core implementation | general-purpose |
| 3 | Navigating Officer (NO) | Legolas (Elf-Scout) | ES | Codebase research | Explore (read-only) |
| 4 | Marine Engineering Officer (MEO) | Boromir (Shield of Gondor) | SG | Testing & validation | general-purpose |
| 5 | Weapon Engineering Officer (WEO) | Sam (Hobbit-Gardener) | HG | Config, infrastructure | general-purpose |
| 6 | Logistics Officer (LOGO) | Merry (Hobbit-Strategist) | HS | Documentation & deps | general-purpose |
| 7 | Coxswain (COX) | Pippin (Hobbit-Watcher) | HW | Standards review & quality | Explore (read-only) |

### Special Roles

- **Red-Cell Navigator** -> **Palantir-bearer** -- adversarial reviewer, challenges assumptions
- **Frodo** -> Not an agent. Represents the critical deliverable / mission objective itself ("the Ring that must reach Mount Doom")

### Temporary Sub-Agents (replace Royal Marines -> Allies of the Free Peoples)

| Nelson Marine | Fellowship Ally | subagent_type | Function |
|---|---|---|---|
| Recce Marine | Ranger of the North | Explore (read-only) | Scout unfamiliar code |
| Assault Marine | Rider of Rohan | general-purpose | Targeted fix, unblock |
| Sapper | Ent of Fangorn | general-purpose | Config, build, infra |

### Threat Levels (replace Action Stations)

| Nelson | Fellowship | Risk |
|---|---|---|
| Station 0: Patrol | The Shire | Low -- internal renames, comments |
| Station 1: Caution | The Wilds | Moderate -- user-facing, coupled |
| Station 2: Action | Isengard | High -- security, compliance |
| Station 3: Trafalgar | Mount Doom | Critical -- irreversible, needs human confirmation |

## Concept Mapping (Naming Glossary)

| Nelson | Fellowship |
|---|---|
| Squadron | The Fellowship |
| Ship | Company (named after Middle-earth locations) |
| Sailing Orders | The Quest |
| Battle Plan | Strategy of the Council |
| Quarterdeck Rhythm | Council of Elrond Checkpoints |
| Captain's Log | Red Book of Westmarch |
| Standing Orders | Laws of the Wise |
| Damage Control | Last Alliance Protocols |
| Royal Marines | Allies of the Free Peoples |
| Commendations | Songs of Praise |
| Signal Flags | Eagle Signals |

### Company Names (replace Ship Names, organized by task weight)

- **Outposts** (general tasks): Bree, Laketown, Edoras, Helm's Deep, Osgiliath, Ithilien, Fornost, Tharbad
- **Strongholds** (high-tempo/high-risk): Minas Tirith, Erebor, Khazad-dum, Isengard, Dol Amroth, Hornburg
- **Waypoints** (small tasks): Weathertop, Amon Hen, Tol Brandir, Cair Andros, Henneth Annun
- **Legendary Holds** (critical-path): Rivendell, Lothlorien, The Grey Havens, Valinor
- **Hidden Paths** (research/stealth): Shelob's Lair, Paths of the Dead, Moria Depths, The Old Forest

## File Structure (33 files, 1:1 with Nelson)

```
.claude/
  agents/
    gandalf.md                                    <- agents/nelson.md
  skills/
    fellowship/
      SKILL.md                                    <- skills/nelson/SKILL.md
      references/
        threat-levels.md                          <- action-stations.md
        fellowship-roles.md                       <- crew-roles.md
        fellowship-composition.md                 <- squadron-composition.md
        songs-of-praise.md                        <- commendations.md
        allies-of-the-free-peoples.md             <- royal-marines.md
        council-templates/
          the-quest.md                            <- sailing-orders.md
          strategy-of-the-council.md              <- battle-plan.md
          company-manifest.md                     <- ship-manifest.md
          fellowship-briefing.md                  <- crew-briefing.md
          council-of-elrond-report.md             <- quarterdeck-report.md
          red-book-of-westmarch.md                <- captains-log.md
          palantir-review.md                      <- red-cell-review.md
          ally-deployment-brief.md                <- marine-deployment-brief.md
        laws-of-the-wise/
          gandalf-at-the-forge.md                 <- admiral-at-the-helm.md
          mustering-all-races.md                  <- all-hands-on-deck.md
          army-beyond-the-walls.md                <- battalion-ashore.md
          fellowship-in-the-mines.md              <- becalmed-fleet.md
          aragorn-at-the-anvil.md                 <- captain-at-the-capstan.md
          companions-without-purpose.md           <- crew-without-canvas.md
          straying-from-the-path.md               <- drifting-anchorage.md
          wrong-burden.md                         <- pressed-crew.md
          corrupting-the-palantir.md              <- press-ganged-navigator.md
          lone-hobbit.md                          <- skeleton-crew.md
          one-ring-two-bearers.md                 <- split-keel.md
          unmarked-peril.md                       <- unclassified-engagement.md
        last-alliance-protocols/
          escalation.md                           <- escalation.md
          fallen-companion.md                     <- man-overboard.md
          company-overrun.md                      <- crew-overrun.md
          return-to-rivendell.md                  <- session-resumption.md
          partial-retreat.md                      <- partial-rollback.md
          breaking-of-the-fellowship.md           <- scuttle-and-reform.md
```

## Usage

Invoke the skill with `$gandalf` followed by a quest description:

```
$gandalf Refactor the authentication module to use JWT tokens
```

Gandalf will:
1. **Declare the Quest** -- define outcome, metric, deadline, constraints
2. **Form the Fellowship** -- select mode (single-session/subagents/agent-team), size the team, assign Company names
3. **Hold the Council** -- break the quest into tasks with owners, deliverables, dependencies, and threat levels
4. **Run Council of Elrond Checkpoints** -- periodic progress reviews, blocker resolution, budget tracking
5. **Assess the Threat** -- apply threat-level controls (The Shire / The Wilds / Isengard / Mount Doom)
6. **Return to the Shire** -- archive sessions, produce a Red Book of Westmarch entry

### Governance Limits

- Fellowship cap: 10 agents (1 Gandalf + up to 9 Quest Leaders/Palantir-bearer)
- Max 4 companions per Company
- Max 2 allies (temporary sub-agents) per Company
- Isengard+ ally deployments require Gandalf approval
- Mount Doom tasks require explicit human (Valar) confirmation

## Verification Checklist

1. `$gandalf` invocation discovers the skill (agent `name` in frontmatter matches skill `name`)
2. All file cross-references in SKILL.md resolve to actual files
3. File count: 33 total (1 agent + 1 SKILL + 5 references + 8 templates + 12 laws + 6 protocols)
4. Operational rules preserved: team cap 10, max 4 per Company, max 2 allies, threat-level decision tree
5. Read-only roles (Legolas ES, Pippin HW) use `Explore` subagent_type; all others use `general-purpose`

## Key Design Decisions

- **Gandalf as Admiral** -- never fights when he can guide; coordinates, inspires, intervenes only at crisis
- **The Valar as human authority** -- highest powers in Tolkien's cosmology, rarely intervene but hold ultimate authority
- **Frodo is not an agent** -- represents the critical deliverable itself, the thing that must be carried to completion
- **Palantir-bearer (not a named character)** -- the seeing-stone concept for adversarial review, avoiding negative connotations of Saruman/Denethor who misused Palantiri
- **Companies named after locations** -- Rivendell/Lothlorien for critical-path, Weathertop for small tasks, Khazad-dum for high-risk
- **"Laws of the Wise"** -- Istari and Elven lords had codified knowledge about governance and restraint
- **"Last Alliance"** -- the desperate coalition formed when things went badly wrong, maps perfectly to recovery procedures
