# Stellaris Mod Feasibility Question Register (War Overhaul + Storm/Hyperlane Dynamism)

Purpose: This document enumerates *feasibility questions* (not design wishes) for a Stellaris total-overhaul concept:
- dynamic wars with **joining/leaving**,
- **opportunistic wars** that reduce claim-grab exploits,
- **withdrawal / refusal** mechanics with political costs,
- and **Cosmic Storm-driven hyperlane mutation** (add/remove lanes).

This register is designed to be fed into a research workflow (e.g., VS Code Copilot browsing + local game file inspection) so we can quickly classify each question as:
- **Confirmed feasible** (documented effect / reproducible minimal mod),
- **Feasible via workaround** (parallel wars / events / modifiers),
- **Not feasible / hardcoded** (or only feasible with unacceptable side effects),
- **Unknown** (needs direct experiment).

---

## How to use this doc
For each question:
1) Search official modding docs / wiki / community notes.
2) Search GitHub/Workshop mod sources for keywords.
3) If unclear, run a *minimal test mod* in a throwaway environment.
4) Record the result and evidence (links, file paths, effect names, reproduction steps).

**Ground-truth rule:** Do not assume an effect exists until you find it in game script docs, game files, or in a working mod.

---

## Scope note (systems in play)
This register references these Stellaris systems:
- War engine (war participants, war leaders, peace, wargoals, warscore, occupation)
- Diplomacy actions and restrictions (federations, truces, pacts)
- Subjects / vassalization / contracts / loyalty
- Events, decisions, edicts, situations, on_actions
- Intel / espionage (if used for gating)
- Cosmic Storms system (DLC-dependent)
- Galaxy generation & hyperlane graph (connectivity/pathfinding/UX)

---

# Section A — War participation: joining an in-progress war

## A1) Can an empire be added to an *existing war object* mid-war?
**System(s):** War engine; scripted effects; diplomatic actions; on_actions.
**Why it matters:** This is the “true join” version vs parallel-war simulation.
**Research targets:**
- Look for effects/commands resembling: `add_to_war`, `join_war`, `add_war_participant`, `set_war_leader`, `force_join_war`.
- Search existing “intervene/join war” mods for any direct war participant mutation.

**Evidence to collect:**
- Exact effect names + syntax (if any)
- Limits (only allies? only subjects? only via certain war types?)
- UI updates (war screen roster, warscore contribution)

---

## A2) If true join is not possible, what *workarounds* are feasible?
**System(s):** War declarations (CB/wargoals), events, flags, scripted triggers/effects.
**Examples to validate:**
- “Join” by declaring a **parallel linked war** against the same enemies.
- “Join” by forced **call-to-arms** style mechanics.
- “Join” by granting military access + subsidies + special CBs (support-only).

**Research targets:**
- Determine which workaround is used by top “intervention” mods and why.

---

## A3) Can we reliably create a “support participant” role with limited agency?
**System(s):** War leadership; peace offers; diplomacy permissions; modifiers.
**Core feasibility sub-questions:**
- Can we prevent support members from separately negotiating peace?
- Can we prevent them from changing wargoals/claims?
- Can we track their contribution (occupation, kills, losses) for payouts?

---

## A4) Can we centralize peace authority to “war leaders” only?
**System(s):** Peace system; AI peace acceptance; war leader determination.
**Research targets:**
- Any scriptable rule for who can offer/accept peace.
- Whether peace authority is hardcoded to war leaders only (and if so, how to control war leader assignment).

---

# Section B — Leaving a war: withdrawal/refusal and partial cash-out

## B1) Can an empire “withdraw” from a war without ending it for everyone?
**System(s):** War participation; war status; truces; diplomatic states.
**Interpretations to test:**
- “Withdraw” = stop fighting but remain at war (soft exit).
- “Withdraw” = forced separate peace for that participant only.
- “Withdraw” = event-driven forced truce / enforced disengagement rules.

**Research targets:**
- Whether war participants can be removed mid-war (even if join is impossible).
- Whether separate peace exists outside certain special war types or is hardcoded.

---

## B2) Can we implement “refuse to join” when called into war?
**System(s):** Defensive pacts/federations/subjects; call-to-arms; on_actions; diplomacy AI.
**Research targets:**
- Hooks that fire when a call-to-arms occurs.
- Can a refusal be chosen by player via event/decision?
- Can penalties be applied (influence, trust, cohesion, opinion)?

---

## B3) Can we implement “exit concessions” (cash-out early) in a coherent way?
**System(s):** Occupation ownership; claims; peace terms; war goal resolution.
**Key feasibility risk:** Keeping territory/benefits while leaving may fight peace logic.

**Research targets:**
- Can we transfer system ownership via script during war/after withdrawal?
- Can we create “temporary occupation ownership” that becomes permanent via event?
- Can we reliably revoke gains on withdrawal (more feasible than granting)?

---

# Section C — Opportunistic wars (realpolitik)

## C1) Can we define a new casus belli + wargoal specifically for opportunism?
**System(s):** `common/casus_belli`, `common/war_goals`, scripted triggers/effects, localization.
**Research targets:**
- Adding CB availability gated by target conditions (war exhaustion, stability, etc.).
- Restricting status quo / enforcing minimum war duration (if possible).

---

## C2) Can we detect “target is overstretched” using scriptable triggers?
**System(s):** war exhaustion, stability, economy deficits, fleet losses, occupation.
**Research targets:**
- Which of these values are accessible in triggers?
- Are enemy fleet losses/strength visible without intel?
- Are occupation percentages accessible?

---

## C3) Can opportunism be gated by intel level?
**System(s):** intel / espionage triggers.
**Research targets:**
- Trigger access to “intel level >= X” on target.
- Whether intel can be used as a hard gate for CB availability.

---

# Section D — Independence wars during overlord’s war (subject exploitation)

## D1) Can a subject declare an independence war while the overlord is at war?
**System(s):** subjects/contracts; war declaration restrictions; federation leadership rules; diplomacy restrictions.
**Why it matters:** This is a key “leave coalition violently” pathway.

**Research targets:**
- Hard rules: “cannot declare war while at war” (who does it apply to?)
- Contract settings that block diplomacy or war declarations
- Federation/hegemony presidency effects that block independence

**Desired outputs:**
- A decision tree: if blocked, which condition is responsible?
- Whether mod scripts can override the restriction or must simulate independence as a separate “coalition break war”.

---

## D2) Can we emulate “independence” without actual subject status?
**System(s):** parallel war creation; modifier-driven “membership” system; events.
**Research targets:**
- Can we create a “coalition membership” state that behaves like subject war obligations?
- Can we trigger a “break away” war reliably even if subject independence is blocked?

---

# Section E — Coalition system architecture (parallel to subjects)

## E1) Can we build a coalition system without repurposing subject contracts?
**System(s):** flags, modifiers, scripted triggers/effects, situations, edicts/decisions, on_actions.
**Research targets:**
- Persistent “coalition leader” and “member” markers
- A clean join/leave flow with cooldowns and penalties
- AI hooks (optional) for joining/leaving

---

## E2) If we *do* repurpose subject contracts, can it be isolated as a parallel system?
**System(s):** subject types/contracts; diplomacy permissions; war participation rules.
**Research targets:**
- Create “wartime coalition subject” type that does NOT:
  - alter economy heavily,
  - enable holdings/integration,
  - break diplomacy UI,
  - cause permanent subject entanglement.
- Can subject creation/removal be done safely and reversibly?

---

# Section F — War Pressure (domestic cost) feasibility

## F1) Can we model “war pressure” as a scalable, persistent state while at war?
**System(s):** modifiers, scripted variables, situations, on_actions periodic pulses.
**Research targets:**
- Can we detect “is_at_war” and increment a variable periodically?
- Can we apply tiered modifiers at thresholds?
- Can we reduce pressure when leaving/peace occurs?

---

## F2) Can we use pressure to influence war participation (join/withdraw availability)?
**System(s):** decisions gating; AI weights; event availability.
**Research targets:**
- Gate join/withdraw behind pressure thresholds.
- Prevent exploit churn by minimum commitment durations and cooldown tracking.

---

# Section G — Cosmic Storms → hyperlane mutation (dynamic topology)

## G1) Can scripts detect storm presence in a system / storm touching a system?
**System(s):** Cosmic Storms DLC; system modifiers; on_actions; event targets.
**Research targets:**
- Triggers/events fired on storm entering/leaving a system.
- Access to “storm id/type/strength” if applicable.
- Whether storms can apply a per-system marker we can read.

---

## G2) Can we add a hyperlane between two systems by script?
**System(s):** galaxy graph; scripted effects; system scope.
**Research targets:**
- Confirm effect(s) and required parameters.
- Distance/adjacency constraints (if any).
- Does it update immediately or after reload/month tick?
- Does AI/pathfinding react correctly?

---

## G3) Can we remove an existing hyperlane by script?
**System(s):** same as above.
**Research targets:**
- Confirm effect(s) and limitations.
- What happens to fleets mid-transit or with queued orders?

---

## G4) Can we guarantee “no isolation” when deleting hyperlanes?
**System(s):** graph connectivity; triggers (system neighbors); pathfinding.
**Research targets:**
- Is there a scriptable way to test if removing a lane would disconnect the galaxy graph or isolate a system?
- If not, can we implement conservative rules:
  - only remove if system has >= N other lanes,
  - only remove 1 lane per system per storm,
  - only add lanes (never delete) for MVP?

---

## G5) Can we limit visual clutter and prevent “ugly long lanes”?
**System(s):** hyperlane rendering; system distance queries.
**Research targets:**
- Script access to system distance or nearest-neighbor selection.
- Methods used by existing hyperlane-generation mods to constrain link length.

---

## G6) DLC gating and fallback strategy
**System(s):** DLC checks, game rules.
**Research targets:**
- How to check whether the storms DLC is active.
- Fallback: event-driven “turbulence” without actual storms (still can mutate lanes or only apply interdiction).

---

# Section H — Galaxy generation determinism & post-gen passes (research thread)

## H1) Can we run a “post-galaxy-gen hyperlane pass” at game start?
**System(s):** on_actions at game start; system iteration; galaxy setup events.
**Research targets:**
- Hook timing: earliest safe moment to mutate hyperlanes without breaking initialization.
- Whether system iteration over all systems is feasible/performance-safe.

---

## H2) Can we control or influence galaxy seed / empire selection ordering?
**System(s):** galaxy generation; RNG; empire spawn selection.
**Research targets:**
- Whether seed is exposed or purely internal.
- Whether any “determinism bugs” reveal mod-accessible configuration.
- Likely outcome: treat as non-modifiable unless proven otherwise.

---

# Section I — Mod-source inspection checklist (explicit TODO per project direction)

## I1) Intervention/join-war mods: what do they *actually* do?
**System(s):** workshop mod source analysis.
**Tasks:**
- Identify 5–10 “join/intervene” mods to inspect.
- For each:
  - list entry points (decisions/edicts/events)
  - identify whether they call `declare_war` (parallel war) or a true join effect
  - identify cleanup logic (ending linked wars when main war ends)

**Outputs:**
- A comparative table: mod name → mechanism → limitations → evidence.

---

# Evidence log template (copy/paste for each question)
For each question ID (e.g., G2):
- **Status:** Confirmed / Workaround / Not feasible / Unknown
- **Evidence type:** docs / game file / working mod / reproducible test
- **Evidence link(s):**
- **Relevant file(s):**
- **Effect/trigger names:**
- **Test steps (if applicable):**
- **Caveats / edge cases:**

---

# Current priority order (recommended)
1) G2/G3/G4 (hyperlane add/remove + safety)
2) A1/A2 (true join vs workaround)
3) D1 (independence while overlord is at war)
4) B1/B3 (withdrawal and concessions)
5) G1 (storm system hooks)
6) F1/F2 (war pressure tracking)
7) H1/H2 (post-gen pass, determinism research)
