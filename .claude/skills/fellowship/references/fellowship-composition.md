# Fellowship Composition Reference

Use this file to choose execution mode and team size.

## Mode Selection

Choose the first condition that matches.

1. If work is sequential, tightly coupled, or mostly in the same files, use `single-session`.
2. If work is parallel but each worker only needs to report to Gandalf, use `subagents`.
3. If workers must coordinate directly across task boundaries, use `agent-team`.

## Decision Matrix

| Condition | Preferred Mode | Why |
| --- | --- | --- |
| Single critical path, low ambiguity | `single-session` | Lowest coordination overhead |
| Parallel discovery, synthesis by Gandalf | `subagents` | Fast throughput without peer chatter |
| Parallel implementation with dependencies | `agent-team` | Supports teammate-to-teammate coordination |
| High threat or high blast radius | `agent-team` + Palantir-bearer | Adds explicit control points |

## Team Sizing

- Small mission: `1 Gandalf + 2-3 Quest Leaders`.
- Medium mission: `1 Gandalf + 4-5 Quest Leaders`.
- Large mission: `1 Gandalf + 6-7 Quest Leaders`.
- Add `1 Palantir-bearer` at medium/high threat.
- Keep one Gandalf only.
- Fellowship cap: 10 Fellowship-level agents (Gandalf, Quest Leaders, Palantir-bearer). Companions are additional — up to 4 per Quest Leader, governed by `references/fellowship-roles.md`.

## Role Guide

- `Gandalf`: Defines quest orders, delegates, tracks dependencies, resolves blockers, final synthesis.
- `Quest Leader`: Commands a Company. Breaks task into sub-tasks, musters roles, coordinates companions, verifies outputs. Implements directly only when the task is atomic (0 companions).
  - Companion roles: Aragorn (Ranger-King / RK), Gimli (Dwarf-Smith / DS), Legolas (Elf-Scout / ES), Boromir (Shield of Gondor / SG), Sam (Hobbit-Gardener / HG), Merry (Hobbit-Strategist / HS), Pippin (Hobbit-Watcher / HW). See `references/fellowship-roles.md` for role definitions and mustering rules.
- `Palantir-bearer`: Challenges assumptions, validates outputs, checks rollback readiness.

## Anti-Patterns

See the Laws of the Wise table in SKILL.md for the full list of Laws of the Wise and known anti-patterns.
