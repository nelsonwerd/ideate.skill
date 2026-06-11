# ideate

An **Agent Skill — for Claude and OpenAI Codex** — for turning a **fuzzy idea** (or an existing project you want to improve) into a **locked concept + phased roadmap** — captured in one living `CONCEPT_BRIEF.md`. It's the upstream partner to the [`prompt-pack`](https://github.com/nelsonwerd/prompt-pack-skill) skill:

> **ideate → `CONCEPT_BRIEF.md` → prompt-pack → execute**

It encodes a method reverse-engineered from real idea→ship journeys — *including the mistakes those journeys made*, so it improves on them instead of repeating them.

## What it does

Runs a disciplined funnel as a blunt, honest co-founder:

1. **Frame** — absorb the brain-dump, set the "what makes this worth doing" rubric, and force the things people always skip: a real **success metric**, a **kill criterion**, and — when feel is the wedge — **how load-bearing the design is** (a substantive design direction carried into the brief).
2. **Explore** — *greenfield:* 5–7 comparable options ranked to your criteria, then mine your own lived experience for the wedge. *Refinement:* a four-lens assessment (what is it / viability / quality / honest take) and narrow strategic forks.
3. **Pressure-test** (the gate) — two-sided honest assessment, competitor buckets, viability economics fit to the concept's type (market + unit economics if it's commercial; reach + cost-to-sustain if it's free/OSS/internal — cited fact vs estimate), feasibility tiers, a red-team pass, and verification against real artifacts. For high stakes it delegates to the `deep-dive` skill. Ends in a verdict and a **go / iterate / kill** decision — and before any *kill* it steelmans the idea's best case and frames the call as *park-with-a-revisit-trigger*, so it won't talk you out of a good idea on a confident hunch.
4. **Converge** — lock decisions one at a time (with a decision log), scope IN/OUT with deferrals named, lock the spine and defer the rest.
5. **Handoff** — name it late, then offer to hand the brief to `prompt-pack`.

Its central mechanism is **one living `CONCEPT_BRIEF.md`, edited in place, never regenerated** — the fix for the #1 failure in unstructured ideation: the AI re-deriving the same assessment every session while decisions never settle.

Two modes: **greenfield** (fuzzy idea → concept) and **refinement** (evaluate/improve an existing thing, treating it as the "golden master" with an enforceable parity contract).

## Quickstart — try this first

> **You type:** "I have an idea for *<your idea>* — help me decide if it's worth building."
>
> **You get back:** a living **`docs/CONCEPT_BRIEF.md`** — a locked concept, a forced success metric and kill criterion, and a phased roadmap. ideate will pressure-test the idea (and push back) before it writes a line of roadmap.

## Install

This is an open **[Agent Skill](https://agentskills.io)** — the same `ideate/` folder works in **Claude** and **OpenAI Codex**. Pick your tool:

| You use… | Install it by… |
|---|---|
| **Claude Code** — terminal, the **Code** tab of the Claude desktop app, [claude.ai/code](https://claude.ai/code), or a VS Code / JetBrains IDE | dropping `ideate/` into `~/.claude/skills/` (all projects) or `.claude/skills/` (one project) |
| **OpenAI Codex** — CLI, app, or IDE | dropping `ideate/` into `~/.agents/skills/` (all repos) or `.agents/skills/` (one repo), then restarting Codex |
| **Claude chat** — the **Chat** tab of the desktop app, or [claude.ai](https://claude.ai) | uploading **`ideate.skill`** (the zip in this repo) under **Customize → Skills** |
| **Any other agent** | pointing it at `ideate/SKILL.md` — it's just instructions |

The `.skill` file is just the `ideate/` folder zipped, so one `unzip` drops it into either skills home:

```bash
# Claude Code — detected in-session (verify with /skills):
unzip ideate.skill -d ~/.claude/skills/

# OpenAI Codex — the current skills path is ~/.agents/skills/; restart Codex after:
mkdir -p ~/.agents/skills && unzip ideate.skill -d ~/.agents/skills/
```

Prefer a clone? `git clone https://github.com/nelsonwerd/ideate-skill.git`, then `cp -r ideate-skill/ideate` into whichever skills folder above.

<sub>Menu names and exact paths shift between versions — the [Claude Skills](https://support.claude.com/en/articles/12512180-use-skills-in-claude) and [Codex Skills](https://developers.openai.com/codex/skills) docs are the source of truth. Auto-activation by description is native to Claude; in Codex you invoke the skill explicitly. The methodology is identical across both.</sub>

## Runtime support

| | Claude chat | Claude Code | OpenAI Codex | Other agents |
|---|---|---|---|---|
| **ideate** | Strong — concept work; brief kept inline when there's no file tree | **Best** | Strong — with a local workspace for the brief | Works — full method; keep the brief in a file or inline |

## Use it

- **Manually:** type `/ideate` and describe the idea (or point it at an existing project to evaluate).
- **Automatically:** Claude invokes it when you say things like "help me figure out what to build", "is this idea any good?", "should I rebuild X?", "where are we really at?", or "turn my idea into a plan."

Examples:

- "I have an idea for a scheduling tool for tutors — is it any good?"
- "Here's my repo. Deep-dive it: viability, quality, honest take — should I keep going?"
- "Help me figure out what to build; I want a subscription SaaS but don't have a lane yet."

It pairs directly with **[prompt-pack](https://github.com/nelsonwerd/prompt-pack-skill)**: when the concept is locked, `ideate` hands the `CONCEPT_BRIEF.md` to `prompt-pack`, which turns the roadmap into sequenced, self-contained build prompts.

## What's in this repo

- `ideate/` — the skill itself (`SKILL.md` + reference playbooks). This is what you install.
  - `references/concept-brief-template.md` — the canonical `CONCEPT_BRIEF` scaffold (the core output).
  - `references/facilitation-guide.md` — the honest-advisor stance + the pressure-test battery.
  - `references/modes-guide.md` — greenfield vs refinement, in detail.
  - `references/handoff-guide.md` — the exact contract for handing off to `prompt-pack`.
- `ideate.skill` — the same folder, zipped, for one-step install.
