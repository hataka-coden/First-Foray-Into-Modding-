# LLM Collaboration Guide — hataka-coden (Stellaris modding)

This document describes how I (the repository owner) prefer to collaborate with an LLM when generating and validating concepts for Stellaris modding. It is intended to reduce drift, improve output usefulness, and ensure ideas remain implementable.

## 1) My goals for LLM usage
- Use the LLM to **discover and refine a vision** when my idea is still vague.
- Use the LLM to **turn ideas into structured, testable design specs** (not just “cool concepts”).
- Use the LLM to **help validate feasibility** against Stellaris modding constraints and expected repo realities.
- Use the LLM as a **backup brain / brainstorming log**, but with guardrails against hallucination.

## 2) My interaction style (what works best)
- Prefer **short question rounds** with periodic summaries over long speculative monologues.
- Prefer **clear section separation** and copy/paste-friendly formatting.
- I’m comfortable with iterative work; I’d rather get:
  - “Version 0.3 design spec” quickly,
  - then refine with targeted follow-up questions,
  than wait for a perfect first pass.
- When I say “save it” or “it’s been saved,” I typically mean **I copied text into my repo** (not necessarily that it’s committed, indexed, or canonical yet).

## 3) Ground-truth rules (non-negotiable)
- **Do not invent repository facts**:
  - No made-up file paths, templates, scripted effects/triggers, IDs, localization keys, folder structures, or existing helpers.
- If implementation details are requested, first ask for:
  - folder tree and relevant file contents (examples: `descriptor.mod`, `common/*`, `events/*`, `map/*`, `localisation/*`, etc.)
- If uncertain, ask explicit clarifying questions rather than guessing.

## 4) Concept generation rules (how to propose ideas)
When proposing a mechanic or feature, include:
- **Player action**: what the player does (inputs, UI, triggers).
- **Game response**: what changes, what feedback is shown (outputs, visibility).
- **Constraints / non-goals**: what the mechanic must *not* do.
- **Balance levers**: costs, timers, caps, cooldowns, gates (tech, civics, starbase level).
- **AI expectations**: player-only vs AI-supported; what guardrails keep AI sane.
- **Performance / UX risk**: any likely pain points (spam, clutter, pathfinding, MP determinism).
- **MVP vs expansion**: smallest version that’s still fun, plus optional upgrades.

## 5) Validation approach (how to test ideas early)
Use “validation passes” before we talk code:
- **Exploit check**: can the mechanic produce instant traps, uncounterable moves, or unfair edge cases?
- **Connectivity check** (for travel/network ideas): can it isolate systems or break pathing?
- **Readability check**: can a player understand cause/effect and plan around it?
- **Pacing check**: is it early/mid/late game? does it create snowballing?
- **AI check**: can AI use it? if not, does it still remain fair?
- **Multiplayer check** (if relevant): deterministic outcomes, no desync-prone randomness at runtime.

## 6) Output format preferences
- Prefer **one text block** outputs when asked, with **clear separators** so I can split into files later.
- When drafting docs/prompts, use:
  - strong headings
  - bullet lists
  - explicit “Facts vs Assumptions vs Open Questions”
- When suggesting edits, provide either:
  - full file replacement text, or
  - a clearly delimited section to paste (with where it goes).

## 7) How to run a “vague idea → solid spec” session with me
### Phase A — Discovery (I don’t know the vision yet)
Ask 5–10 concise questions, then summarize:
- What is the player fantasy?
- What do I want to change about vanilla Stellaris?
- What do I hate / want to avoid?
- What part of the game should this touch (map gen, diplomacy, warfare, etc.)?
- What are the “must have” and “nice to have” outcomes?

Deliverable: **Vision Statement + Goals + Non-Goals + Glossary**

### Phase B — Design candidates
Propose 2–3 candidate mechanics that could satisfy the vision.
Deliverable: **comparison table + recommendation + open questions**

### Phase C — Constraints and guardrails
Lock in anti-exploit rules, pacing, and AI posture.
Deliverable: **guardrails checklist + MVP definition**

### Phase D — Implementation planning (only if I ask)
Request repo ground truth, then propose file touch list and milestones.

## 8) Stellaris-specific preferences (based on our discussions so far)
- Prefer mechanics that are **planning-focused**, not instant/reactive “gotcha” traps.
- For galaxy/travel concepts:
  - guard against **connectivity breakage**
  - avoid “visual clutter everywhere” (sparse visuals preferred)
  - layered networks are best modeled as **hyperlanes + bypass-style links** unless a better approach is proven.
- If there are multiple reasonable approaches, show trade-offs rather than forcing one.

## 9) “Stop conditions” (when you should pause and ask)
Pause and ask me before proceeding if:
- you need to assume repo structure, file names, or existing templates
- the idea depends on a specific Stellaris scripting capability you are not sure exists
- there are multiple plausible interpretations of my request
- the design is at risk of breaking AI/pathfinding/connectivity and you need a decision on guardrails

## 10) Quick prompt to start a session (optional)
If I say “new concept, not sure what I want yet,” respond by:
1) asking 5–10 short questions
2) returning:
   - Vision Statement (1–2 paragraphs)
   - Goals / Non-Goals
   - Glossary
   - 2–3 Candidate Mechanics (1 paragraph each)
   - Open Questions list
