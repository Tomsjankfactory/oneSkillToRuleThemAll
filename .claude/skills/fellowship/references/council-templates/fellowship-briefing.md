# Fellowship Briefing Template

When spawning each teammate via `Task()`, include this briefing in their prompt. Teammates do not inherit the lead's conversation context — they start with a clean slate and need explicit mission context to operate independently.

Target size: ~500 tokens. Enough for the teammate to work without asking clarifying questions, but not so much that it wastes their context window.

```text
== FELLOWSHIP BRIEFING ==
Mission: [mission name from quest orders]
Your Role: Quest Leader [N] — [role description]
Company: [Company name from strategy of the council]
Your Task: [specific task from strategy of the council]
Deliverable: [what you must produce]
Threat Level: [0-3] — [The Shire / The Wilds / Isengard / Mount Doom]
File Ownership: [files you own — no other agent should edit these]
Dependencies: [tasks that must complete before yours / tasks waiting on yours]
Ally Capacity: [0-2, from Company manifest — omit line if 0]
Laws of the Wise:
- Do NOT implement work outside your assigned task scope
- Do NOT edit files not assigned to you
- Report blockers to Gandalf immediately with options and one recommendation
- When done, report: deliverable, validation evidence, failure modes, rollback note
- You may deploy Allies of the Free Peoples (short-lived sub-agents) for focused sorties.
  Deploy by calling the Task tool directly (NOT via bash/CLI — use the built-in Task tool).
  Ranger of the North: Task tool with subagent_type="Explore" (read-only recon).
  Rider of Rohan / Ent of Fangorn: Task tool with subagent_type="general-purpose".
  Include a deployment brief in the Task prompt (template below).
  Isengard+ ally deployments require Gandalf approval first.
  Max 2 allies at a time. Allies cannot deploy allies.
Ally Deployment Brief (include in ally's Task prompt):
  == ALLY DEPLOYMENT BRIEF ==
  Company: [your Company name]
  Detachment: [Ranger of the North / Rider of Rohan / Ent of Fangorn]
  Objective: [single clear sentence]
  Scope: [what to do, and explicitly what NOT to do]
  Report back: [what findings/outputs to return]
  Constraints: Do NOT modify files outside scope. Do NOT spawn sub-agents.
  == END BRIEF ==
== END BRIEFING ==
```

## Field notes

- **Mission** — Copy verbatim from quest orders so the teammate shares the same outcome/metric framing.
- **Company** — From the Company manifest in the strategy of the council. Gives the teammate identity and signals task weight (Outpost, Stronghold, etc.).
- **File Ownership** — Critical for preventing merge conflicts when multiple agents work in parallel. If no files are assigned, note "No file ownership — research/analysis only."
- **Dependencies** — List both blocking (what must finish first) and blocked-by (what waits on this task). If none, note "Independent — no dependencies."
- **Ally Capacity** — From the Company manifest. Tells the Quest Leader how many allies they may deploy (max 2). Omit if 0.
- **Laws of the Wise** — Keep these to 4-5 lines. Project-specific laws can be appended here. The ally law tells Quest Leaders they CAN deploy allies and where to find the rules — without this, Quest Leaders have no knowledge of allies.
