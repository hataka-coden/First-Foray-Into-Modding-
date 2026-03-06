```markdown name=.github/prompts/conversation_opener_new_concept_general.md
We are working in repo: hataka-coden/First-Foray-Into-Modding- (Stellaris mod).

Goal of this chat
- I have an early/unclear mod idea (or only a vibe). Help me discover, refine, and validate the vision.
- Do NOT jump to implementation. We will converge on a written design first.

Step 0 — Ground truth only (no invented repo facts)
- I will provide the mod folder tree + selected file contents when ready (descriptor.mod, common/*, events/*, map/*, localization/*, documentation/*).
- Until you see them, do not invent file paths, scripted effects, triggers, modifiers, IDs, localization keys, or existing templates.
- If you need repo context, ask for it explicitly before proposing file edits.

Step 1 — Capture the “vision” (discovery phase)
Ask me short, targeted questions and summarize after each round:
- Player fantasy: what do I want to feel like I’m doing?
- Scope: is this a small mechanic, a system rework, or a new game mode?
- Constraints/non-goals: what must NOT happen (balance, performance, AI, MP, early-game pacing)?
- Where it lives: galaxy generation, diplomacy, economy, warfare, UI, events, etc.
- Required knobs: what settings/toggles should exist?

Deliverable A (end of Step 1)
- A 1–2 paragraph “Vision Statement”
- A bullet list of Design Goals + Non-Goals
- A short Glossary (terms we will reuse consistently)

Step 2 — Build the context snapshot (repo + style)
Once I provide repo files:
- Summarize the repo structure as a short “Repo Map” (folders + purpose).
- Identify the “gold standard” template files for style (headers/comments/doc style).
- Output a list of “Authoritative References” (file paths) future work must follow.

Deliverable B (end of Step 2)
- Repo Map
- Style/Doc rules extracted from existing templates
- Authoritative References list

Step 3 — Turn the vision into a design spec (no code)
Propose 2–3 “mechanic candidates” that could fulfill the vision.
For each candidate:
- What the player does (inputs)
- What the game does (outputs)
- Key rules/limits
- Balance levers (costs, timers, caps, cooldowns)
- AI expectations
- Performance risks
- Minimum viable version (MVP) vs later expansions

Deliverable C (end of Step 3)
- Strategy comparison table (Candidate A/B/C)
- Recommendation + rationale
- Open questions / assumptions

Step 4 — Implementation planning (still no code unless I ask)
Only after we agree on the spec:
- List the minimal set of files/folders likely to be touched (based on Repo Map).
- Provide an incremental plan: “first milestone” → “second milestone” → “tests”.

Output rules
- Separate: Confirmed Facts vs Assumptions vs Recommendations.
- When suggesting text to commit, provide copy/paste-ready sections or full-file replacements.
- Keep questions concise; avoid long speculative essays before we lock goals/constraints.
```
