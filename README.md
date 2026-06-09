# ideate

A Claude Code skill for turning a **fuzzy idea** (or an existing project you want to improve) into a **locked concept + phased roadmap** — captured in one living `CONCEPT_BRIEF.md`. It's the upstream partner to the [`prompt-pack`](https://github.com/nelsonwerd/prompt-pack.skill) skill:

> **ideate → `CONCEPT_BRIEF.md` → prompt-pack → execute**

It encodes a method reverse-engineered from real idea→ship journeys — *including the mistakes those journeys made*, so it improves on them instead of repeating them.

## What it does

Runs a disciplined funnel as a blunt, honest co-founder:

1. **Frame** — absorb the brain-dump, set the "what makes this worth doing" rubric, and force the two things people always skip: a real **success metric** and a **kill criterion**.
2. **Explore** — *greenfield:* 5–7 comparable options ranked to your criteria, then mine your own lived experience for the wedge. *Refinement:* a four-lens deep-dive (what is it / viability / quality / honest take) and narrow strategic forks.
3. **Pressure-test** (the gate) — two-sided honest assessment, competitor buckets, market + unit economics (cited fact vs estimate), feasibility tiers, a red-team pass, and verification against real artifacts. For high stakes it delegates to the `deep-dive` skill. Ends in a verdict and a **go / iterate / kill** decision.
4. **Converge** — lock decisions one at a time (with a decision log), scope IN/OUT with deferrals named, lock the spine and defer the rest.
5. **Handoff** — name it late, then offer to hand the brief to `prompt-pack`.

Its central mechanism is **one living `CONCEPT_BRIEF.md`, edited in place, never regenerated** — the fix for the #1 failure in unstructured ideation: the AI re-deriving the same assessment every session while decisions never settle.

Two modes: **greenfield** (fuzzy idea → concept) and **refinement** (evaluate/improve an existing thing, treating it as the "golden master" with an enforceable parity contract).

## Install

Skills live in `~/.claude/skills/` (all projects) or `.claude/skills/` (one project). Put the `ideate/` folder in either.

**From the packaged file:**

```bash
mkdir -p ~/.claude/skills
unzip ideate.skill -d ~/.claude/skills/
```

**Or from a clone of this repo:**

```bash
git clone https://github.com/nelsonwerd/ideate.skill.git
mkdir -p ~/.claude/skills
cp -r ideate.skill/ideate ~/.claude/skills/
```

No restart needed — Claude Code detects it in-session. Verify with `/skills`.

## Works in Claude *and* Codex

This follows the open **[Agent Skills](https://agentskills.io) standard**, so the same `SKILL.md` works in **Claude** and **OpenAI Codex**:

| You are… | Tool | How |
|---|---|---|
| **Non-technical** | Claude app (claude.ai / desktop) | Upload **`ideate.skill`** (a zip) in the app's **Skills / Capabilities** settings → [Agent Skills docs](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) |
| **Developer** | Claude Code | the install above (drop `ideate/` in `~/.claude/skills/`) |
| **Developer** | OpenAI Codex | copy `ideate/SKILL.md` (+ `references/`) into `.agents/skills/ideate/` in your repo, or `~/.agents/skills/ideate/` globally → [Codex skills docs](https://developers.openai.com/codex/skills) |
| **Anyone** | any agent | it's just instructions — open `SKILL.md` and point your agent at it |

<sub>Exact in-app menu names and commands shift between versions — the linked docs are the source of truth. Claude-specific behaviors (auto-activation by description) are invoked explicitly in Codex; the *methodology* itself is fully portable.</sub>

## Use it

- **Manually:** type `/ideate` and describe the idea (or point it at an existing project to evaluate).
- **Automatically:** Claude invokes it when you say things like "help me figure out what to build", "is this idea any good?", "should I rebuild X?", "where are we really at?", or "turn my idea into a plan."

Examples:

- "I have an idea for a scheduling tool for tutors — is it any good?"
- "Here's my repo. Deep-dive it: viability, quality, honest take — should I keep going?"
- "Help me figure out what to build; I want a subscription SaaS but don't have a lane yet."

It pairs directly with **[prompt-pack](https://github.com/nelsonwerd/prompt-pack.skill)**: when the concept is locked, `ideate` hands the `CONCEPT_BRIEF.md` to `prompt-pack`, which turns the roadmap into sequenced, self-contained build prompts.

## What's in this repo

- `ideate/` — the skill itself (`SKILL.md` + reference playbooks). This is what you install.
  - `references/concept-brief-template.md` — the canonical `CONCEPT_BRIEF` scaffold (the core output).
  - `references/facilitation-guide.md` — the honest-advisor stance + the pressure-test battery.
  - `references/modes-guide.md` — greenfield vs refinement, in detail.
  - `references/handoff-guide.md` — the exact contract for handing off to `prompt-pack`.
- `ideate.skill` — the same folder, zipped, for one-step install.
