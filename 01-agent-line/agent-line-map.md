# Agent Line Map: Cortex PM Chief-of-Staff Agent

> Module 1 · The Agent Line
>
> ✅ **What this validates:** every risky action has a clear owner, by the end you'll have proven an above/below-the-line map with HITL checkpoints, scored on reversibility, blast radius, and measurability.

## The workflow, decision by decision

List every discrete decision or action in your agent's workflow, then score each one and place it **above** the line (a human owns it) or **below** (the agent owns it). Borderline calls get an HITL checkpoint.

| Decision / action | Reversibility (H/M/L) | Blast radius (H/M/L) | Measurability (H/M/L) | Above / Below | HITL? |
|---|---|---|---|---|---|
| Pull project state and activity | H | L | H | Below | no |
| Decide relevant context | M | M | L | Above | no |
| Draft the update | H | L | H | Below | no |
| Decide tone and commitment level | M | H | L | Above | no |
| Flag at-risk or escalation (rule-based internal flags) | M | M | H | HITL | yes |
| Choose what to escalate | L | H | L | Above | no |
| Propose a story batch (capped) | H | L | M | HITL | yes |
| Post an update, or approve a company-wide one | L | H | M | Above | no |

## Agent anatomy (sketch)

- **Model:** Mini by default, and a frontier model for the draft you will review. The expensive model is spent where the blast radius is high. Reads and capped proposals stay on the cheap model.
- **Tools:** `get_project`, `get_activity`, `search_past_updates`, `get_roadmap`, `get_norms`, and `propose_stories`. The story tool only queues. Reads and a capped proposal are allowed, and posting stays with you.
- **Memory:** Sources persist, drafts do not become facts. The roadmap, team norms, past updates, and decision log are the record. A held draft is still unapproved, so the next run should not treat it as what happened.
- **Loop:** _placeholder, defined in M2 loop-spec.md_
- **Bounds:** _placeholder, defined in M5 bounds-and-evals.md_
- **Evals:** _placeholder, defined in M5 bounds-and-evals.md_

## The golden rule, applied

Pull project state and activity sits below the line because it is easy to rerun, has a low blast radius, and is straightforward to verify against agreed sources, with reversibility deciding the verdict.

Decide relevant context sits above the line because reversibility is medium, its blast radius is medium, and relevance is difficult to verify, with measurability deciding the verdict because important omissions can go unnoticed.

Draft the update sits below the line because a private draft is easy to revise, has a low blast radius, and can be checked against approved context and sources, with reversibility deciding the verdict.

Decide tone and commitment level sits above the line because reversibility is medium, its blast radius is high, and appropriateness is difficult to verify, with blast radius deciding the verdict because other teams may act on a promise.

Flag at-risk or escalation sits at HITL because reversibility and blast radius are medium while agreed triggers make verification straightforward, with blast radius deciding the verdict because a missed flag can delay intervention.

Choose what to escalate sits above the line because it is hard to reverse, has a high blast radius, and is difficult to verify objectively, with blast radius deciding the verdict because escalation can redirect people and priorities.

Propose a story batch (capped) sits at HITL because the proposal is easy to revise and has a low blast radius, but measurability is medium, with measurability deciding the verdict because rule compliance alone cannot establish whether the batch fits current priorities.

Post an update, or approve a company-wide one sits above the line because publication is hard to reverse, has a high blast radius, and has medium measurability, with blast radius deciding the verdict because readers across the company may act before a correction reaches them.

## Hardest call

The hardest call is 5, Flag at-risk or escalation. Explicit triggers make it highly measurable, which initially supported placing it below. But reviewing only the flags Cortex produces would miss false negatives. HITL therefore means I review the trigger coverage and supporting project state as well as the proposed flags. That makes the human review meaningful for the medium blast radius that settled this placement.
