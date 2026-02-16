# One Skill to Rule Them All

A Lord of the Rings-themed multi-agent coordination skill for [Claude Code](https://docs.anthropic.com/en/docs/claude-code). Based on the [Nelson skill](https://github.com/harrymunro/nelson) by Harry Munro, which uses Royal Navy metaphors to orchestrate parallel agent teams. This replaces all the naval stuff with Middle-earth equivalents because, honestly, why wouldn't you.

Gandalf coordinates your agents. Aragorn leads the companies. Gimli does the heavy lifting. Legolas scouts the codebase. You get the idea.

## What it actually does

When you have a big task that benefits from multiple agents working in parallel, you invoke `$gandalf` and it:

1. Defines the quest (scope, constraints, success criteria)
2. Forms a fellowship (picks the right agents for the job)
3. Holds a council (breaks work into tasks, assigns owners)
4. Runs checkpoints (tracks progress, unblocks issues)
5. Assesses threat levels (The Shire through Mount Doom, basically low risk to "we need a human to confirm this")
6. Writes the Red Book of Westmarch when it's done (a log of what happened and why)

## Install

You need [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed. If you don't have that, none of this will make sense.

### Option 1: Clone it into your project

```bash
git clone https://github.com/Tomsjankfactory/oneSkillToRuleThemAll.git
```

Then copy the `.claude` folder into the root of whatever project you want to use it in:

```bash
cp -r oneSkillToRuleThemAll/.claude /path/to/your/project/
```

If you already have a `.claude` folder in your project (you probably do), just merge the contents:

```bash
cp oneSkillToRuleThemAll/.claude/agents/gandalf.md /path/to/your/project/.claude/agents/
cp -r oneSkillToRuleThemAll/.claude/skills/fellowship /path/to/your/project/.claude/skills/
```

### Option 2: Just download the zip

Go to the green "Code" button on this repo, click "Download ZIP", unzip it, and copy the `.claude` folder into your project like above.

### Verify it works

Open Claude Code in your project directory. You should see `gandalf` available as a skill. Run:

```
$gandalf do something trivial to test this works
```

If Gandalf starts talking about forming a fellowship, you're good.

## The Fellowship

| Role | Character | What they do |
|---|---|---|
| Coordinator | Gandalf | Delegates and tracks. Never implements. Like the books. |
| Quest Leader | Aragorn | Leads a company, makes tactical calls |
| Core Implementer | Gimli | Writes the actual code |
| Scout | Legolas | Explores the codebase (read-only) |
| Tester | Boromir | Testing and validation |
| Infra/Config | Sam | The real hero. Handles config and infrastructure |
| Docs/Deps | Merry | Documentation and dependencies |
| Quality Review | Pippin | Standards review (read-only) |

There's also a Palantir-bearer for adversarial review on riskier tasks, and temporary allies (Rangers, Riders of Rohan, Ents) that get spawned for short-lived subtasks.

## Threat Levels

| Level | Name | When |
|---|---|---|
| 0 | The Shire | Low risk. Renaming things, comments, safe refactors |
| 1 | The Wilds | Moderate. User-facing changes, coupled systems |
| 2 | Isengard | High. Security, compliance, things that matter |
| 3 | Mount Doom | Critical. Irreversible stuff. Gandalf asks you before proceeding |

## Credits

Based on [Nelson](https://github.com/harrymunro/nelson) by Harry Munro. All the operational logic, decision trees, governance rules and templates are his -- I just replaced boats with hobbits.
