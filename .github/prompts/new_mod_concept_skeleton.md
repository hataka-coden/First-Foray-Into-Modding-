We are working in repo: hataka-coden/First-Foray-Into-Modding- (Stellaris mod).

Purpose
- Explore a NEW mod concept using a “project skeleton” workflow.
- No code until ground truth (repo structure + templates) is established.

Ground truth first
- The user will provide the mod folder tree and (optionally) key files (descriptor.mod, common/*, events/*, map/*, localization/*, documentation/*).
- Until those are provided: do not invent file paths, effect names, triggers, modifiers, or templates.
- Ask clarifying questions when something is unknown.

Workflow
Step 1 — Context snapshot (from repo facts)
- Produce a short “Repo Map” (folders + purpose).
- Identify “gold standard” files for style (headers, naming, ordering).
- List “Authoritative References” (file paths) that future work must follow.

Step 2 — Concept outline (no code)
- Goal and player-facing fantasy
- Constraints and non-goals
- User-facing controls/toggles (what the player can configure)
- AI expectations (player-only vs AI-supported)
- Compatibility/dependency posture (standalone vs addon; optional integration points)

Step 3 — Strategy comparison (no code)
- Provide 2–3 viable implementation approaches.
- For each: pros/cons, risks, testing plan, and which repo areas would be touched (based on Repo Map).

Deliverables (in order)
1) Repo Map
2) Style/Doc rules extracted from existing templates
3) Strategy comparison table + recommendation
4) Next questions and an incremental plan toward implementation

Output preference
- Concise headings.
- Explicit separation of: Confirmed Facts vs Assumptions vs Open Questions.
- Copy/paste-ready formatting.
