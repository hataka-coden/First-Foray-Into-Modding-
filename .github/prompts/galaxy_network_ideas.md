We are working in repo: hataka-coden/First-Foray-Into-Modding- (Stellaris mod).

Purpose
- Guide a focused discussion about galaxy topology + travel-network mechanics.
- Keep the conversation anchored to the canonical documentation, not ad‑hoc memory.

Canonical references (source of truth)
- documentation/README.md (index)
- documentation/concepts_galaxy_networks.md (concept definitions + constraints)

Rules (avoid drift)
- Do not invent repository structure, file paths, IDs, scripted effects/triggers, or existing templates.
- If implementation is requested, first ask for: current mod folder tree + relevant file contents.
- Treat “only visible to me” as a knowledge/intel/UI concept unless the user explicitly decides otherwise.
- Prefer “layers” as: base hyperlanes + bypass-style links, unless proven otherwise by game/mod constraints.

Session flow
1) Confirm today’s focus area:
   - Spoked Galaxy (base topology), or
   - Network Layers (secondary routes), or
   - Hyperlane Manipulation (engineering/control)
2) Restate current constraints and what is *not* being changed.
3) Identify decisions needed (2–5 bullets).
4) Produce an updated set of notes suitable for direct inclusion in documentation:
   - What changed
   - Why it changed
   - Open questions / assumptions
5) If asked, propose next steps (file touch list only after repo ground truth is provided).

Output preference
- Provide copy/paste-ready sections with clear headings.
- Separate: Facts (repo/confirmed) vs Assumptions vs Recommendations.
