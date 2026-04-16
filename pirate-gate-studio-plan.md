# Pirate Gate: One Piece — Studio Build Plan

## Context

Francisco (9) designed an ambitious 16-player extraction game called Pirate Gate: One Piece. The pitch meeting with the expert Claude Code instance produced excellent outputs — a vision doc and technical analysis. But when the instance transitioned to building, the output was underwhelming. No wow factor. Same failure pattern as Sebastian's first attempt.

The core problem: the instance created instructions for a building process instead of building something impressive. Claude Code winging Three.js in real-time produces mediocre output.

This plan applies the approach that worked for Sebastian's Shogun's Storm — vision-first, pre-engineered sessions, each session a complete experience — adapted for Francisco's game.

---

## Part 1: The Conversation with Francisco

### The Problem

Francisco designed a 16-player game. The technical reality is single-player first. If we frame this as "a simpler version," we lose him.

### The Language

**Never say:** "simplified," "prototype," "practice version," "for now," "scaled down," "baby steps."

**Use instead:** "Build 0.1," "the vertical slice," "studio build," "the campaign."

### The Framing

Use One Piece itself — Francisco knows it better than anything:

> "You know how Oda didn't start One Piece with all 1,100 chapters. Chapter 1 is just Luffy, alone, punching one guy, on one island. No crew, no Grand Line, no Haki. But that one chapter had EVERYTHING — the Gum Gum Fruit, Luffy's personality, the feeling of One Piece. That's what Oda showed his editors to prove the series was worth making.
>
> In game development, that's called a vertical slice — the one piece of the game that proves the whole thing works. Every game you've ever played started like this. The vertical slice is where you prove that Pirate Gate feels incredible. Once a Gum Gum Pistol sends a Marine flying and everyone who sees it says 'WHOA' — then you have something real. Then multiplayer has a foundation worth building on."

**Why this works:**
- References One Piece — Francisco's deepest knowledge
- Chapter 1 genuinely IS a vertical slice of the series
- Names a real industry concept (makes him feel like a game developer, not a kid being told to be patient)
- Connects single-player directly to multiplayer: this is "the path to," not "instead of"
- Puts the quality bar on the FEELING, not the feature count

### What NOT to Say

- Don't frame it as a learning journey ("you'll learn Three.js")
- Don't compare unfavorably to AAA studios ("even studios can't build your full game")
- Don't say "we can't do multiplayer" — say "we build the campaign first, like every studio does"

### The Title

**"Pirate Gate: One Piece — Studio Build."** Each session produces a numbered build (Build 0.1, Build 0.2, etc). These are real builds of his real game, not exercises.

---

## Part 2: Francisco's Design Decisions — The North Stars

Same approach as Sebastian's revised plan: start from the design decisions that make Pirate Gate special, work backward to technology. These are non-negotiable.

### 1. The Gum Gum Pistol
Luffy's arm STRETCHES — visibly, dramatically — snaps forward, connects, and the enemy FLIES back. This is the signature moment. If this doesn't feel incredible, nothing else matters.

**Requires:** Arm-stretch visual effect (shader or bone scaling), physics-based knockback, full juice stack (hitstop, screen shake, hit flash, particles, damage numbers, sound).

### 2. The Anime Ocean
Cel-shaded water. The Going Merry sailing on it. This is the first thing anyone sees. It needs to look like One Piece brought to life.

**Requires:** Stylized water shader (not photorealistic), cel-shaded toon materials, 3D ship model, third-person ship camera, controller input.

### 3. Ship-to-Island Transition
Sail to an island. Land. Walk around as Luffy. Two modes (ship/character) in one seamless experience. This is what makes the game feel like a WORLD, not an arena.

**Requires:** Ship controller, character controller, camera transition system, dock/landing trigger, island terrain.

### 4. Faction Identity
Picking Luffy vs Buggy vs Krieg vs Arlong isn't picking a skin — it's picking a completely different game. Luffy stretches. Arlong bites and swims. Buggy splits apart. Every faction's abilities come from the One Piece source material.

**Requires:** Per-character ability systems, per-character animations, faction select screen. (Sessions 6+ — not MVP.)

### 5. The Extraction
Someone finds the One Piece. Get it to your ship. Escape while being hunted. This is the endgame loop that makes every match tell a different story.

**Requires:** Objective pickup, carry mechanic, escape zone, win condition. (Session 8 — not MVP.)

---

## Part 3: Revised Tooling

### Core Engine: Three.js

**Why:** Francisco's game is 3D — third-person camera, anime cel-shaded ocean, ship sailing, island exploration. Three.js delivers all of this in the browser. Francisco already knows Three.js from AI Studio. Claude Code generates reliable Three.js code.

**Why not Phaser (the initial recommendation):** Francisco didn't design a 2D game. He designed a 3D anime world with ships on an ocean. Phaser can't deliver the cel-shaded ocean, the third-person camera following the Going Merry, or the feeling of sailing toward an island growing on the horizon. The initial recommendation prioritized Claude Code reliability over Francisco's actual vision. That was wrong — same mistake as Sebastian's first plan.

### Character Pipeline: Gemini MCP + Meshy MCP (all in Claude Code)

Same pipeline proven for Sebastian:
1. Francisco describes character → Claude uses **Gemini MCP** to generate concept art → iterate through conversation
2. Locked concept art → **Meshy MCP** image-to-3D
3. Auto-rig (humanoid) → animation presets → FBX export
4. Load into Three.js with FBXLoader + AnimationMixer

**Two-image strategy:** Generate a "cool" image (dynamic pose, atmospheric — what Francisco sees) AND a "clean" image (neutral stance, solid background, even lighting — what Meshy gets).

### Physics: cannon-es
Lightweight physics for ship movement, knockback, collisions.

### Input: Gamepad API (native browser)
Controller support is critical for Francisco. Xbox controller mapping.

### Deployment: itch.io
Browser game, shareable URL.

### Juice Stack
Hitstop, screen shake, hit flash, knockback, hit spark particles, damage numbers. Applied to every attack. Individually trivial, together they make combat feel real.

---

## Part 4: The Sessions

### The Pre-Build / Live-Build Split

**The lesson from what failed:** If Claude Code generates Three.js from scratch during a session, the output is mediocre. The solution: Andres and Claude pre-build the technical foundation BEFORE each session. Francisco's session is the final 20% — creative direction, tuning, polish. The 80% that makes it possible is invisible to him.

**Pre-build (before each session — Andres + Claude):**
- All scaffolding code (project setup, shaders, physics, camera)
- 3D models loaded and working (Meshy generation, import, materials)
- Controller mapping wired up
- UI framework (health bars, cooldowns — containers, not content)
- Config/parameter system that lets the session instance change values instantly

**Live-build (during session — Francisco directs):**
- Art direction (colors, intensity, atmosphere)
- Combat feel tuning (knockback distance, screen shake, hitstop frames)
- Character design (concept art through conversation)
- Gameplay decisions (enemy behavior, difficulty, ability design)
- Sound selection

**The rule:** Francisco never watches scaffolding being built. He walks into something that already works and makes it his.

---

### Session 0: The Pitch (DONE)
Vision doc and technical analysis complete.

### Session 0.5: The Conversation
Andres talks to Francisco. Frames the studio build approach. Uses the One Piece / Chapter 1 / vertical slice framing. Gets Francisco excited about building Build 0.1. No Claude Code needed — this is a father-son conversation.

### Session 1: "Build 0.1 — The Grand Line"

**Theme:** Francisco's world comes to life in 3D.

**What Francisco sees when he sits down:**
A browser window. A cel-shaded anime ocean with waves. Clouds in the sky. An island in the distance. The Going Merry floating on the water — a real 3D ship model with toon shading. An Xbox controller is plugged in.

**What Francisco does:**
1. Picks up the controller. Pushes the stick. The Going Merry sails forward. Water sprays at the bow.
2. The instance asks art direction questions: "What color should the East Blue be? Deep navy or bright turquoise? How big should the waves be?" Each answer changes the scene in real-time.
3. He sails toward the island. It grows on the horizon.
4. The instance asks: "What does this island look like? Rocky? Jungle? A Marine base?" Francisco directs. The island appearance updates.
5. He reaches the island. A "dock" prompt appears. This is where Session 1 ends — or if energy is high, he steps onto the island as a placeholder character.

**The wow moment:** The first time Francisco pushes the analog stick and the Going Merry sails forward across an anime ocean. His ship, his ocean, his controller. This is the screenshot he sends to his friends.

**Deliverable:** A playable browser scene: sail the Going Merry across the Grand Line to an island.

**Pre-build requirements:**
| Component | Priority | Est. Effort | Risk |
|-----------|----------|-------------|------|
| Cel-shaded water shader | P0 | 2-3 hrs | HIGH — visual quality is everything |
| Going Merry 3D model (Meshy or Sketchfab, cel-shaded) | P0 | 1-2 hrs | MEDIUM — Meshy may need multiple attempts |
| Ship controller + simple physics | P0 | 1-2 hrs | LOW |
| Third-person ship camera | P0 | 30 min | LOW |
| Project scaffold (Three.js boilerplate) | P0 | 30 min | LOW |
| Island model (basic terrain, cel-shaded) | P1 | 1 hr | LOW |
| Skybox/atmosphere | P1 | 1 hr | LOW |
| Parameter config system (for live tuning) | P1 | 1 hr | LOW |
| Water spray particles at bow | P2 | 30 min | LOW |
| **Total** | | **~9-12 hrs** | |

Water shader is the riskiest item — tackle first, iterate on visual quality.

---

### Session 2: "Build 0.2 — Luffy Walks"

**Theme:** The captain enters his world.

**What Francisco sees:** The ocean from Session 1. But now when the ship reaches the island, Luffy steps off. Third-person camera. Controller controls the character. He runs, jumps, explores.

**What Francisco does:**
1. Sails to the island (already works).
2. Docks. Camera transitions from ship-follow to character-follow. Luffy is on the island.
3. Moves Luffy with the controller. Walk, run, jump.
4. The instance asks: "How fast should Luffy run? How high should he jump? How close should the camera be?" Francisco tunes in real-time.
5. If time: Francisco directs Luffy concept art creation through Gemini MCP. His Luffy, his design.

**Wow moment:** Walking around as Luffy on the island he sailed to, Going Merry visible at the dock. Two modes in one seamless experience.

**Deliverable:** Sail to island, walk around as Luffy. Ship mode + character mode.

**Pre-build requirements:**
- Luffy 3D model (Meshy image-to-3D from good concept art, or Sketchfab, cel-shaded)
- Character controller (third-person movement, jump, collision)
- Ship-to-character camera transition
- Walk/run/idle animations (Meshy or animation library)
- Island terrain with collision

---

### Session 3: "Build 0.3 — The Gum Gum Pistol" (MAKE OR BREAK)

**Theme:** Combat comes alive. This is the most important session.

**What Francisco sees:** Luffy on the island. A training dummy or static Marine. The instance says: "Today we give Luffy his powers. Your job is to make the Gum Gum Pistol feel right."

**What Francisco does:**
1. Presses attack. Luffy's arm stretches forward, connects. The dummy slides back a little. Flat — no juice. Intentional.
2. The instance walks him through adding feel, one layer at a time:
   - Screen shake: "How hard should the screen shake?" Francisco picks. Tests.
   - Hitstop: "The game freezes for a split second on impact. How many frames?" Picks. Tests.
   - Knockback: "How far does the enemy fly?" Picks. Tests.
   - Hit flash, particles, damage numbers, sound — each one added, tested, tuned.
3. By the end, the same punch has gone from flat to CRUNCHY. Francisco tuned every variable.
4. If time: Gum Gum Gatling (rapid multi-hit) with its own juice.

**Wow moment:** The before-and-after. Flat punch → same punch with full juice. The transformation happens in real-time and Francisco controlled every parameter.

**Deliverable:** Luffy with a Gum Gum Pistol that feels incredible. A screen recording of the punch is what he shows people.

**Pre-build requirements:**
- Attack animation system with arm-stretch effect (THIS IS THE HARD PART — Luffy's arm literally stretches. Pre-solve this.)
- Target dummy or static Marine model
- Juice system with individually tunable parameters: screen shake (intensity, duration), hitstop (frame count), knockback (distance, speed), hit flash (color, duration), particle burst (count, size, color), damage numbers (font, float speed)
- Sound effects library (3-4 hit sounds to choose from)
- Controller attack button mapped
- CRITICAL: Each juice parameter must be adjustable via simple config change — the session instance modifies values, the scene updates instantly.

---

### Session 4: "Build 0.4 — The Marines" (BUILD 1.0)

**Theme:** Real enemies. Real fights. Real stakes.

**What Francisco sees:** Luffy on the island. Marines patrolling. They haven't noticed him yet.

**What Francisco does:**
1. Walks toward a Marine. Marine spots him, draws a weapon, charges. Combat begins with the juice-tuned attacks from Session 3.
2. Marine attacks back. Luffy has a health bar. Stakes are real.
3. Francisco directs AI behavior: "How aggressive should Marines be? Rush immediately or patrol first?"
4. More Marines spawn. Francisco fights a group. Discovers crowd control.
5. Francisco picks death effects: ragdoll? fly off edge? dissolve?
6. Clear all Marines = win.

**Wow moment:** Fighting three Marines at once and sending them all flying with the Gum Gum Pistol he personally tuned.

**Deliverable:** Complete loop: sail → land → fight Marines → clear island. **THIS IS BUILD 1.0. Declare victory.** Pirate Gate is a real playable game.

**Pre-build:**
- Marine 3D model (Meshy or Sketchfab, cel-shaded)
- Marine AI state machine (patrol → detect → approach → attack → stagger → die)
- Marine attack with its own juice
- Health system (player + enemy, health bar UI)
- Death effect system (2-3 options)
- Wave spawning

---

### Session 5: "Build 1.1 — Full Arsenal"

**Theme:** Luffy becomes a complete fighter.

- Gum Gum Gatling (rapid multi-hit — Francisco directs speed, hit count, visual feel)
- Gum Gum Bazooka (heavy charged attack — charge time, massive knockback, unique screen effect)
- Ability cooldowns with UI
- Controller mapping: Francisco maps his own control scheme
- Fights Marines with the full kit, discovers combos

**Wow moment:** Charged Gum Gum Bazooka sends three Marines flying in different directions.

---

### Session 6: "Build 1.2 — Zoro Joins"

**Theme:** The roster begins. Second character = proof that different characters feel different.

- Francisco designs Zoro concept art through Gemini MCP → Meshy → rig → animate
- Zoro has sword combat: slash combos, Oni Giri special
- Character select screen: Luffy or Zoro
- Playing as Zoro feels fundamentally different from Luffy

**Wow moment:** Switching from Luffy to Zoro and the game feels like a different game.

---

### Session 7: "Build 1.3 — Ship Cannons"

**Theme:** Naval combat comes alive.

- Cannons on the Going Merry
- Aim and fire cannonballs at a target ship
- Explosion particles, ship damage, screen shake
- Coup de Burst ability (the Going Merry's unique ability — massive speed boost)

**Wow moment:** First cannonball impact with full juice. The naval part of the game comes alive.

---

### Session 8: "Build 2.0 — The Full Loop"

**Theme:** The extraction objective. The game becomes what Francisco designed.

- The One Piece placed on the island
- Pick it up, carry it to the ship
- Escape zone at map edge
- Timer (30 minutes)
- Win screen
- This is Pirate Gate v2.0 — deploy to itch.io

**Wow moment:** Francisco sends a link to his friends. They open it. They're playing Pirate Gate: One Piece.

---

## Part 5: Session Instance Design

### CLAUDE.md Structure for Each Session

1. **Identity & Tone** — Formal, substantive, short exchanges. "You are running a BUILD session. Show, don't describe. When Francisco makes a decision, implement it and show the result."

2. **Who You're Talking To** — Francisco profile. Emphasize: "He gives specific feedback. He doesn't need handholding. He designed an extraction game with asymmetric factions."

3. **The Mission** — Exactly what this session produces. Written as a vivid narrative.

4. **What Already Exists** — CRITICAL section. Precise inventory of pre-built code: file paths, what each file does, what parameters are tunable. The instance must NEVER rebuild what exists.

5. **Session Flow** — Step-by-step sequence. Not rigid, but the instance knows the progression and the planned wow moment.

6. **Technical Reference** — How to modify parameters, file locations, fallback plans.

7. **Rules:**
   - **Rule 1:** Never show a planning document. Output is always the thing itself.
   - **Rule 2:** Never generate scaffolding during the session. Everything structural is pre-built.
   - **Rule 3:** Every 5 minutes, Francisco should see something new in the browser.
   - **Rule 4:** When Francisco gives feedback, implement immediately. Don't ask "how much bigger?" Just make it bigger.
   - **Rule 5:** The controller must always work. Never disable input while making changes.
   - **Rule 6:** Frame creative decisions, not technical ones. "How far should enemies fly?" not "What knockback value?"
   - **Rule 7:** If something breaks, fix it silently. Francisco sees "Let me adjust that," not error messages.
   - **Rule 8:** End with a declaration. "This is Build 0.1 of Pirate Gate: One Piece."
   - **Rule 9:** Never wing Three.js code from scratch. You have pre-built systems. Modify them.
   - **Rule 10:** The wow moment is engineered, not discovered. Make sure it lands.

---

## Part 6: Immediate Deliverable — AI Game Studio 1

### What We're Building Now

Francisco's first AI Game Studio session: **"Forge Your Captain"** — adapted from Sebastian's "Forge Your Warrior" but for Pirate Gate.

**Why character creation first (not the ocean scene):**
- The ocean/ship scene requires heavy pre-engineering (water shader, ship model, physics) — that's weeks of prep
- Character creation uses the Gemini MCP + Meshy MCP pipeline that's already available
- Francisco's interaction model is conversation — designing Luffy through dialogue is his wheelhouse
- The deliverable (animated 3D Luffy) is an artifact he can see, hold, and show people
- It proves the pipeline before we invest in the game engine work
- Same sequencing that worked for Sebastian (character first, world second)

### The Deliverables

1. **`CLAUDE-session-1.md`** — The session instance prompt. Includes:
   - Opening with the vertical slice / studio build framing (since we don't know if Francisco's been told yet, the session instance handles it naturally)
   - Francisco's profile (adapted from the pitch meeting CLAUDE.md)
   - The character creation mission (concept art → 3D → rig → animate)
   - One Piece-specific knowledge (Luffy's visual features, straw hat, scar, rubber body)
   - Gemini → Meshy pipeline technical reference (same pattern as Sebastian's, adapted for One Piece characters)
   - Two-image strategy (cool image for Francisco, clean image for Meshy)
   - Session rules (celebrate the artifact not the process, keep momentum, fix failures silently, connect to Pirate Gate)
   - Pre-flight MCP checks

2. **`mission-1-forge-your-captain.html`** — The briefing page Francisco sees. Beautiful UI (same design system as Sebastian's briefing). Frames the mission, shows the phases, previews what's next. NOT instructions — a mission briefing that gets him excited.

3. **Pre-session checklist for Andres** — What to test before Francisco sits down (MCP tools working, test image gen, test Meshy pipeline with a throwaway model).

### Key Differences from Sebastian's "Forge Your Warrior"

| | Sebastian | Francisco |
|---|---|---|
| **Character** | Jin Sakai (samurai, katana, Ghost armor) | Luffy (straw hat, red vest, rubber stretch, scar under left eye) |
| **Art style** | Atmospheric, dark, Ghost of Tsushima palette | Anime cel-shaded, bold colors, One Piece proportions |
| **Scope framing** | Not needed (fighting game MVP is natural) | Needed (16-player → single-player is a big gap) |
| **What connects to the game** | "This Jin will stand in Castle Shimura with cherry blossoms" | "This Luffy will sail the Going Merry and punch Marines with the Gum Gum Pistol" |
| **Bonus characters** | Mongol enemy or Yuna | A Marine (Luffy needs someone to fight) or Zoro |
| **Concept art prompts** | Samurai armor, dark palette, katana details | Anime proportions, straw hat, red vest, simple sandals, the scar |

### The Vertical Slice Framing (Built into Session Opening)

The session instance opens with a brief framing before diving into the mission. Something like:

> "Welcome to the Pirate Gate studio. Every game ever made starts the same way — with a vertical slice. One Piece Chapter 1: just Luffy, one island, one fight, one Devil Fruit. That chapter proved the whole series was worth making. We're building Pirate Gate's Chapter 1. Today — we forge the captain. By the end of this session, you'll have YOUR Luffy, in 3D, with combat animations, ready to load into the game engine. Let's start. Describe Luffy to me — not the anime Luffy. YOUR Luffy. The one who stands on the deck of the Going Merry in Pirate Gate."

Then straight into the mission. The framing takes 30 seconds, not 5 minutes.

---

## Key Differences from Sebastian's Plan

| | Sebastian (Shogun's Storm) | Francisco (Pirate Gate) |
|---|---|---|
| **Core mechanic** | Parry timing + Ghost Mode | Gum Gum Pistol stretch + ship sailing |
| **Visual identity** | Atmospheric (cherry blossoms, lighting) | Anime cel-shaded (bold colors, ocean) |
| **Scope gap** | Moderate (fighting game → MVP fighting game) | Large (16-player extraction → single-player prototype) |
| **Ship/vehicle** | No | Yes — ship sailing is core |
| **Two gameplay modes** | No (arena only) | Yes (ship + on-foot) |
| **Critical risk** | Ghost Mode post-processing | Arm-stretch effect + water shader |
| **Framing challenge** | Low (fighting game MVP is still a fighting game) | High (16-player vision vs single-player reality) |

The framing conversation (Part 1) is more critical for Francisco than it was for Sebastian. Sebastian's MVP naturally looks like a smaller version of his game. Francisco's MVP strips away the multiplayer extraction that IS his game's identity. The vertical slice framing — proving the FEEL first — is essential.

---

## Files to Create/Modify

- `Documents/gamestudio/pirate-gate-studio-plan.md` — This plan, saved as reference
- `Documents/francisco-game-studio/` — New directory for Francisco's build
- `Documents/francisco-game-studio/CLAUDE-session-1.md` — Session 1 instance prompt
- `Documents/francisco-game-studio/src/` — Pre-built Three.js project
- `Documents/francisco-game-studio/assets/` — 3D models, textures
