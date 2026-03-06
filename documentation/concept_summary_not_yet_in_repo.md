# Comprehensive Concept Summary (Not Yet Implemented / Not Yet in Repo)

**Status:** Brainstorming-only summary for later reuse.  
**Intent:** Capture all major concept threads discussed so far so they can be reintroduced into specs later, without assuming feasibility.

---

## 1) Dynamic War Overhaul (core pillar)

### 1.1 Two-tier war participation model
- **War Leaders**: primary belligerents who own war goals and control peace negotiations.
- **Support Participants**: join a side to fight and contribute, but have limited/no peace agency.
- Motivation: allows **join/leave churn** without constantly rewriting peace logic.

### 1.2 Joining a war = material + intel integration (not abstract)
- Joining cost should be paid **to the war leader**, not “to nothing.”
- Candidate join costs:
  - **Alloys** (resupply / logistics)
  - **Intel sharing** (forced wartime comms/sensor integration; can be simulated if actual treaties are infeasible)
  - optional energy/resources as upkeep
- The intent is to reduce “free opportunism” and create real coalition politics.

### 1.3 Opportunistic war goals (anti-exploit)
- New **Opportunistic CB/Wargoal** to separate opportunism from vanilla “quick claim snipe.”
- Intended to reduce the exploit:
  - “target is distracted → I grab claims fast → I exit before fleets return.”
- Desired behavior:
  - opportunists can’t easily cash out quickly without consequences,
  - rewards should depend on commitment to the broader conflict (or paying a high cost to exit).

### 1.4 Leaving a war
- **Withdrawal / refusal** mechanics:
  - refuse to join (penalties)
  - withdraw after joining (bigger penalties)
- “Cowardice / unreliable” reputation concept:
  - affects future diplomacy and coalition invitations
  - creates anti-churn guardrails

### 1.5 Independence-style exit (coalition-break)
- “Independence” is used as a *conceptual analogue* for leaving coalition leadership:
  - **Non-violent break** (contract break) or
  - **Violent breakaway** (civil-war-like split conflict)
- “Independence during overlord’s war” is specifically flagged as a **high-risk feasibility unknown**.

---

## 2) War Pressure / Domestic Cost (internal politics pillar)

### 2.1 War Pressure (aka War Strain)
- War generates accumulating internal costs:
  - stability/happiness penalties
  - influence drain (political capital)
  - possible economic impacts
- Civics/policies/traits can mitigate or redirect pressure.
- Purpose:
  - make joining wars a serious decision,
  - create strategic reasons to seek peace/withdraw,
  - prevent endless war snowball.

### 2.2 Escalation ladder for internal failure states
- Proposed tiers:
  1) **Strain** (manageable debuffs)
  2) **Crisis** (serious unrest, production/approval issues)
  3) **Breakdown** (rare): separatism, rebellion, civil war, or sector breakaways
- This creates the emergent storytelling: empires overextend and fracture.

---

## 3) Sector Autonomy / Internalized Vassals (state cohesion pillar)

### 3.1 Sectors as semi-autonomous regions (“internalized vassals”)
- Large empires have meaningful internal regional politics.
- Sectors accumulate **Autonomy Pressure** based on:
  - neglect / low investment
  - distance/logistics
  - war pressure
  - instability/crime
- Sectors can demand concessions, resist policy, or eventually break away.

### 3.2 “Investment” approaches (kept for later investigation)
- **Option A (implicit investment)**: investment is represented by development proxies (buildings/districts, stability, governor presence) + a few explicit projects/stances.
- **Option B (explicit sector budget + AI builder)**: allocate resources to sectors which then use AI logic to develop (high complexity).
- **Hybrid Option C (top priority)**: a sector AI governor leader that steers specialization via traits/modifiers and triggers curated projects/situations.

---

## 4) Sector AI Governor System (Hybrid Option — top testing priority)

### 4.1 Sector AI Governor as a unique leader/tool
- A special “AI Governor” concept that can be installed per sector (or empire-capped).
- Higher cost and upkeep than normal governors.
- Provides:
  - strong modifier packages,
  - specialization guidance,
  - war-pressure mitigation tools,
  - and autonomy management effects.

### 4.2 Governor “Attitudes” / templates
Sector AI Governor types discussed:
- **Military AI**: frontier defense sectors
- **Extraction AI**: basic resources (energy/minerals/food)
- **Industry/Development AI**: industrial throughput (alloys/CG)
- **Stability AI**: unity, stability, crime reduction
- **Research AI**: science output and sustainability
- **Balanced/Generalist**: weaker but safe for mixed sectors

### 4.3 Guided specialization (preferred over auto-building)
Preferred approach: **Option 2: guided specialization** to reduce open-ended AI economic decisions.
- Instead of “AI builds everything,” the governor:
  - applies strong incentives for on-plan jobs/buildings,
  - applies mild inefficiency penalties for off-plan mixes,
  - supports stability/amenities to sustain specialization.
- Rationale:
  - avoids janky automation,
  - reduces AI planning complexity,
  - helps AI empires perform closer to human players without cheating resources,
  - reduces the player nuisance of conquering barren/collapsed AI planets.

### 4.4 Sector-level + planet-level control (via sector interface concept)
- Desired management model:
  - Sector stance sets the default plan,
  - Planet stances are overrides for special worlds,
  - All accessed via “sector management” flow (sector view can access planets).
- Planet-level overrides can be weaker “local administrations” to keep mixed sectors workable.

### 4.5 AI empires must use this system (universal feature requirement)
Hard requirement: the mechanic must not be player-only.
Feasibility questions exist for whether AI can:
- pick appropriate governor types,
- trigger the install mechanism (decision/situation/building),
- pay upkeep sensibly,
- avoid thrashing.

---

## 5) Post-Conquest Transitional Administration (occupation realism + QoL)

### 5.1 Temporary authoritarian-style “colonial government” for conquered planets
- Recently conquered planets can enter a time-limited governance mode:
  - “Military Occupation”
  - “Re-education Authority”
  - “Collaboration Government”
  - “Reconstruction Administration”
- Goal:
  - make conquest politics feel real,
  - prevent conquered planets from instantly being stable,
  - provide a structured stabilization path with tradeoffs.
- Strong integration with war pressure and sector autonomy:
  - heavy-handed rule stabilizes short-term but may increase long-term separatism risk.

### 5.2 Situations/decisions preferred for orchestration
- Situations are preferred for:
  - clear stages and duration,
  - warning thresholds,
  - controlled pacing without popup spam.

---

## 6) Cosmic Storms ↔ Hyperlane Dynamism (dynamic theater pillar)

### 6.1 Storm-touched systems can mutate hyperlanes (core concept)
- When storms pass through a region, affected systems get a chance to:
  - **create** hyperlanes to nearby systems
  - **delete** hyperlanes (with strict safety guardrails)
- This makes wars more dynamic by changing theaters and chokepoints over time.

### 6.2 Guardrails for hyperlane mutation
- Avoid isolating systems / breaking galaxy connectivity.
- Cap number of changes per storm and per system.
- Avoid long “ugly” lanes; prefer nearest-neighbor/local edits.
- Prefer summary notifications to avoid spam.

### 6.3 Alternative storm effects (kept as backup)
- “Storm interdiction” concept: keep lanes but make travel costly/dangerous instead of rewiring topology.
- “Temporary corridors” concept: ephemeral bypass-style links during storms.

---

## 7) “Bug as capability probe” investigation workflow (research approach)
- Use a broken patch branch (kept open by Paradox) and compare against working branch to learn:
  - where determinism or selection ordering exists,
  - whether galaxy-gen behavior is influenced by mod-accessible knobs.
- Treated strictly as research; no assumptions that it yields stable mod hooks.

---

## 8) Cross-cutting implementation style preference (conceptual)
- Favor **situations + decisions + events** as primary orchestration tools.
- Avoid systems requiring heavy custom UI where possible.
- Make systems AI-usable by:
  - using contextual auto-prompts/events,
  - using AI weights rather than open-ended optimization,
  - using caps/cooldowns to prevent thrashing.

---

## 9) Key “unknown feasibility” hotspots (not answers, just reminders)
- True “join an existing war object” vs parallel-war simulation
- Separate peace / partial cash-out for support participants
- Independence wars while overlord is already at war
- Sector/planet scoping and automation hooks
- AI empires’ ability to select and operate governor/situation mechanisms reliably
- Safety of hyperlane deletion without isolating systems

---
End of summary.
