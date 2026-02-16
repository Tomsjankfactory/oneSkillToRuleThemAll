# Fellowship Roles Reference

Use this file to decide whether a Quest Leader should muster a fellowship or implement directly, and which roles to muster.

## Fellowship-or-Direct Decision

Choose the first condition that matches.

1. If the task is atomic and can be completed in a single pass, Quest Leader implements directly (0 companions).
2. If the task has one clear deliverable with no research or testing needs, muster 1 Gimli (Dwarf-Smith).
3. If the task needs exploration, testing, or a second specialism, muster Gimli (Dwarf-Smith) + 1 specialist.
4. If the task has multiple interdependent sub-tasks, muster Aragorn (Ranger-King) + Gimli (Dwarf-Smith) + up to 2 specialists.

Never exceed 4 companions per Company. If the task demands more, split it into two Companies.

## Fellowship Sizing

| Companions | When | Typical Manifest |
|---|---|---|
| 0 | Atomic task, single-pass fix | Quest Leader implements directly |
| 1-2 | Typical task | Gimli (Dwarf-Smith), optionally + 1 specialist |
| 3 | Complex task with research or testing needs | Gimli (Dwarf-Smith) + 2 specialists |
| 4 | Multi-part task requiring internal orchestration | Aragorn (Ranger-King) + Gimli (Dwarf-Smith) + 2 specialists |

## Role Definitions

| Role | Abbr | Function | subagent_type | When to Muster |
|---|---|---|---|---|
| Aragorn (Ranger-King) | RK | Integration & orchestration across sub-tasks | general-purpose | 3+ companions or interdependent sub-tasks |
| Gimli (Dwarf-Smith) | DS | Core implementation work | general-purpose | Almost always (default doer) |
| Legolas (Elf-Scout) | ES | Codebase research & exploration | Explore | Unfamiliar code, large codebase |
| Boromir (Shield of Gondor) | SG | Testing & validation | general-purpose | Weathertop+ or non-trivial verification |
| Sam (Hobbit-Gardener) | HG | Config, infrastructure, systems integration | general-purpose | Significant config or infrastructure work |
| Merry (Hobbit-Strategist) | HS | Documentation & dependency management | general-purpose | Docs as deliverable, dependency management |
| Pippin (Hobbit-Watcher) | HW | Standards review & quality enforcement | Explore | Weathertop+ with established conventions |

### Read-Only Roles

Legolas (Elf-Scout) and Pippin (Hobbit-Watcher) use the `Explore` subagent type. They cannot modify files. They report findings to the Quest Leader or Aragorn (Ranger-King), who decides how to act on them.

### Role Boundaries

Each companion works strictly within their role definition. A Gimli (Dwarf-Smith) does not run tests (that is Boromir (Shield of Gondor)). A Legolas (Elf-Scout) does not write code (they report findings). See Law of the Wise `laws-of-the-wise/wrong-burden.md` for the anti-pattern.

## Company Name Registry

Gandalf assigns a Company name to each Quest Leader during Fellowship formation. Companies are named after the peoples and forces of Middle-earth. Choose names that roughly match task weight.

### Patrols (small tasks)

Bombadil's Folk, The Bree-folk, The Lake-men, Beorn's Folk, The Shire-muster

### War-bands (general-purpose tasks)

The Dunedain, The Rohirrim, The Men of Dale, The Beornings, The Green Elves, The Woodmen, The Wildermen, The Drúedain

### Hosts (high-tempo or high-risk tasks)

The Galadhrim, The Guard of the Citadel, The Dwarves of Erebor, The Ents of Fangorn, The Host of the Mark, The Swan Knights

### Grand Alliances (critical-path tasks)

The White Council, The Last Alliance, The Grey Company, The Vanguard of the King

### Shadow-walkers (stealth or research tasks)

The Rangers of Ithilien, The Watchers in the Wood, The Pathfinders of Arnor, The Dead of Dunharrow

## Fellowship Laws of the Wise

The following Laws of the Wise apply specifically to fellowship operations:

- `laws-of-the-wise/aragorn-at-the-anvil.md` — Quest Leader must not implement when companions are mustered.
- `laws-of-the-wise/mustering-all-races.md` — Do not muster roles the task does not need (too many companions).
- `laws-of-the-wise/lone-hobbit.md` — Do not spawn a single companion for an atomic task (too few companions).
- `laws-of-the-wise/wrong-burden.md` — Do not assign companions work outside their designated role (wrong companion).

## Allies of the Free Peoples

Allies are NOT companions. They are short-lived sub-agents a Quest Leader deploys for discrete objectives outside the fellowship's task scope. See `references/allies-of-the-free-peoples.md` for deployment rules and specialisations.

Key distinction: Companions subdivide the Company's deliverable. Allies execute independent sorties in support of the Company's task.
