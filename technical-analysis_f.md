# Technical Analysis — Pirate Gate: One Piece

## What Francisco Designed

A 16-player (4 crews of 4) PvPvE extraction game set in the One Piece universe. Third-person, anime cel-shaded, controller support. Players pick a captain and get that captain's full faction (ship, crew, abilities). Sail the Grand Line, fight Marines, find Devil Fruits, race to extract the One Piece. Ship destruction eliminates the whole crew.

This is an ambitious, multiplayer, 3D game with asymmetric factions, ship combat, ground combat, AI enemies, and an extraction objective. The full vision is a commercial-scale game. The question is: what can we build NOW that captures the core fantasy and keeps Francisco excited?

---

## Honest Scope Assessment

The full game Francisco described — 16 players online, open ocean, ship physics, boarding, faction AI, extraction — is a AAA/large-indie scope project (Wildgate had a full studio, Moonshot Games). We cannot build the multiplayer networking layer in Claude Code sessions.

**But here's the good news:** the FEEL of the game — the part that makes it exciting — can be captured in a single-player or local prototype. The combat, the character abilities, the ship sailing, the faction identity. That's all buildable. And if the prototype is strong, there are paths toward multiplayer later.

---

## Recommended Tooling: Three.js (Browser-Based 3D)

### Why Three.js

1. **Francisco already knows the pipeline.** He used Three.js on AI Studio Day 5-6. He used Meshy for text-to-3D models. The pipeline is: Meshy generates a 3D character model → export as GLB → Three.js loads it → anime cel-shader applied → character is in the game.

2. **Claude Code generates excellent Three.js code.** It dominated the 2025 Vibe Coding Game Jam (10,000+ entries). Francisco's workflow — talk to Claude Code, see results in browser — maps directly to Three.js development.

3. **Anime cel-shading is achievable.** Three.js has toon/cel-shading materials built in. Bold outlines + flat color + expressive animation = the One Piece look Francisco wants, without needing photorealistic rendering.

4. **Third-person camera, controller input, physics** — all well-supported in Three.js with libraries (cannon-es for physics, standard Gamepad API for controllers).

5. **No install required.** Runs in the browser. Francisco can share a link with friends to show them his game.

6. **Three.js MCP exists** — can render scenes directly in the Claude Code conversation for rapid iteration.

### What Three.js Can't Do (Yet)
- **Multiplayer networking.** Three.js is a rendering engine, not a game engine with built-in netcode. For the first version, this is single-player or local split-screen. Multiplayer would require adding a networking layer (Socket.io, WebRTC) later — doable but a separate project.
- **Complex AI pathfinding out of the box.** Marine AI will need a navigation system. Libraries exist (yuka, three-pathfinding) but it's medium-difficulty.

### Setup
- Three.js + cannon-es (physics) + toon shader materials
- Meshy account for 3D model generation
- Gamepad API for controller support
- All runs in browser — no engine install

---

## MVP Definition: "First Playable"

The minimum build that captures the core fantasy: **I'm a One Piece character, I'm on my ship, I sail to an island, I fight, my abilities feel amazing.**

### MVP Includes:
- **1 playable character: Luffy.** Gum Gum Pistol (stretch punch with knockback), Gum Gum Gatling (rapid hits), basic melee combo. Third-person camera.
- **The Going Merry.** Sailable ship. Steer, accelerate, brake. One cannon you can fire.
- **1 island.** Landable. Walk around. Return to ship.
- **Marines (AI).** 3-4 marine types. Basic patrol and attack behavior. Spawn on the island.
- **Combat juice.** Hit impact, knockback, screen shake, damage numbers, hit flash. THIS IS WHERE THE WOW LIVES. A Gum Gum Pistol that sends a Marine flying with screen shake and a satisfying sound is worth more than 10 features without juice.
- **Controller support.** Left stick move, right stick camera, buttons for attacks and abilities.

### MVP Does NOT Include:
- Other playable characters (added in subsequent sessions)
- Other ships or factions
- Other players or multiplayer
- Devil Fruit pickups
- The One Piece extraction objective
- Ship-to-ship combat (ship just sails in MVP)

### Why This MVP Works
Francisco plays as Luffy. He sails the Going Merry across the ocean. He lands on an island. Marines attack. He punches them with stretchy arms and they fly back. The camera shakes. It feels incredible. THAT is the core fantasy. Everything else builds on top of it.

---

## Build Sequence

Each session should end with something visible and playable. Wow-factor moments are marked with a star.

### Session 1: The Ocean and the Ship
- Create a cel-shaded ocean (Three.js water shader with toon look)
- Place the Going Merry (Meshy-generated 3D model or placeholder)
- Player controls the ship: sail forward, turn, stop
- Third-person camera follows the ship
- Add a visible island in the distance

**End state:** You're sailing a ship on an anime ocean toward an island. Looks beautiful.
**Wow moment: The ocean.** A cel-shaded anime ocean with the Going Merry sailing on it will look incredible in a browser. This is the screenshot Francisco shows his friends.

### Session 2: The Character ⭐
- Generate Luffy model (Meshy text-to-3D, or load a pre-made GLB)
- Third-person character controller: move, jump, camera orbit
- Land on island: transition from ship to on-foot
- Basic environment on the island (ground plane, some rocks/trees)

**End state:** You sail to the island, get off the ship, and run around as Luffy.

### Session 3: Combat Feel ⭐⭐⭐
- Basic punch combo (3-hit chain)
- Gum Gum Pistol: arm stretches, hits, enemy flies back short distance
- Screen shake on hit (2-3 frames)
- Hit flash (white frame)
- Knockback with physics
- Damage numbers floating up
- Hit spark particles at contact point
- Sound effects

**End state:** Luffy punches things and it feels AMAZING. This is the most important session. If the combat juice is right, the game has a soul.
**Wow moment: The first Gum Gum Pistol that sends an enemy flying with screen shake.** This is THE moment. Everything before this is setup. This is where Francisco will feel like he has a real game.

### Session 4: Enemies
- Marine character model (Meshy or placeholder)
- Basic AI: patrol, detect player, approach, attack
- Marine attacks deal damage to Luffy
- Health bar UI for Luffy
- Marines have health bars too
- Enemy death animation/effect
- Wave spawning: clear a group, more appear

**End state:** Full combat loop. Sail to island, land, fight Marines, win or lose. THIS IS VERSION 1.0. Declare victory here.

### Session 5: Luffy's Full Kit
- Gum Gum Gatling (rapid multi-hit, hold button)
- Gum Gum Bazooka (big charged attack, major knockback)
- Ability cooldowns with UI indicators
- Ability button mapping for controller

**End state:** Luffy has three distinct abilities. Each feels different. Combat has variety.

### Session 6: Second Character — Zoro ⭐⭐
- Zoro model (Meshy)
- Unique sword combat: slash combos, different from Luffy
- Oni Giri (three-sword special attack)
- Character select screen: pick Luffy or Zoro

**End state:** Two playable characters that feel completely different. This is the moment it starts feeling like a real One Piece game.

### Session 7: Ship Combat
- Cannons on the Going Merry
- Aim and fire cannonballs
- An enemy ship (AI-controlled or stationary target)
- Cannonball impact: explosion particle, damage to ship, screen shake

**End state:** Ship-to-ship shooting works. The naval part of the game comes alive.

### Session 8: The Full Loop
- Place the One Piece (or a treasure stand-in) on the island
- Pick it up, carry it back to the ship
- Escape zone at the edge of the map
- Win screen when you extract
- Timer (30 minutes)

**End state:** The full game loop — sail, land, fight, grab objective, escape. This is version 2.0.

---

## The Wow-Factor Map

| Session | Wow Moment | Technique |
|---------|-----------|-----------|
| 1 | Anime ocean with ship sailing | Cel-shaded water shader, toon materials |
| 2 | Walking around as Luffy in 3rd person | Character controller + Meshy model |
| 3 | **Gum Gum Pistol sends enemy flying** | Hitstop + screen shake + knockback + particles |
| 4 | Fighting waves of Marines | AI state machine + wave spawning |
| 6 | Zoro plays totally different from Luffy | Unique movesets, different attack feel |
| 7 | Ship cannons firing with explosions | Projectile physics + particle effects |
| 8 | Extracting the One Piece and winning | Full loop closure |

Session 3 is the make-or-break moment. If the Gum Gum Pistol feels right, everything after that is expansion of something that already works. If it doesn't feel right, that's where to invest extra time tuning.

---

## Risk Points

### Scope Creep (HIGH RISK)
Francisco has designed a 16-player multiplayer game. The gap between vision and buildable-now is large. The risk is that the single-player prototype feels "small" compared to what he imagined. **Mitigation:** Frame each session's output as a version of HIS game, not a compromise. "This is Pirate Gate version 1.0" not "this is a practice version."

### 3D Model Quality (MEDIUM RISK)
Meshy text-to-3D generates models of varying quality. One Piece characters are stylized and specific — Luffy's straw hat, Zoro's three swords, Arlong's saw nose. If the models don't look right, it'll break immersion. **Mitigation:** Generate models early (Session 1-2). If Meshy output isn't good enough, use pre-made GLB models from free repositories (Sketchfab has One Piece fan models). Or use simpler placeholder models with strong cel-shading — style can compensate for detail.

### Combat Feel Tuning (MEDIUM RISK)
The juice stack (hitstop, screen shake, knockback, particles, sound) is individually simple but needs TUNING to feel right. Too much screen shake is nauseating. Too little knockback feels flat. **Mitigation:** Build all juice effects with adjustable parameters. Spend time in Session 3 tweaking numbers. Francisco's feedback here is critical — he'll know when it feels right.

### Controller Mapping (LOW RISK)
The Gamepad API is well-supported in browsers. Three.js handles it cleanly. This is mostly configuration, not engineering.

### Multiplayer (FUTURE RISK)
The full vision needs networking. This is a fundamentally different technical challenge from everything else on this list. Not a Session 9 task — it's a separate project phase. **Mitigation:** Build the single-player version first. If Francisco wants multiplayer, the options are: (a) add Socket.io/WebRTC networking to the Three.js game, (b) port to a multiplayer-ready engine (Roblox Studio, Unity with networking), or (c) build local split-screen as a stepping stone.

---

## Integration with Francisco's Existing Skills

| Skill | How It Feeds Into This Project |
|-------|-------------------------------|
| **Meshy (text-to-3D)** | Generate character models (Luffy, Zoro, Marines), ship models (Going Merry), environment props |
| **Nano Banana (image gen)** | Concept art for characters/scenes, UI elements, texture generation |
| **Three.js** | The entire game engine — rendering, animation, shaders, camera |
| **Claude Code workflow** | Primary development interface — describe what you want, iterate |
| **Game design thinking** | Already has the design doc mindset from Day 4. This project extends it |

---

## Growth Path

### After Version 2.0 (the full single-player loop)
- **More characters:** Sanji, Nami, Usopp (complete Straw Hat roster)
- **More factions:** Buggy Pirates, Don Krieg Pirates, Arlong Pirates (as designed)
- **Devil Fruit pickups:** Find fruits on islands, eat them for new abilities
- **Marine bosses:** Captain Morgan, Smoker — tougher AI enemies
- **Multiple islands:** Larger map with several landable locations

### Multiplayer Path
- **Local split-screen:** Two players, same computer. Doable in Three.js.
- **LAN/online:** Requires networking layer. Socket.io for turn-based, WebRTC for real-time. Significant engineering.
- **Roblox port:** If friends-playing-online becomes the priority, Roblox Studio with MCP gives multiplayer for free. One Piece fighting games are literally the #1 genre on Roblox. Trade-off: Roblox visual style, platform lock-in.

### Version 3.0: Grand Line Expansion
- New captains: Crocodile, Enel, Doflamingo, Katakuri, Big Mom, Kaido
- **Haki system introduced** as a new combat mechanic
- Admiral bosses (Akainu, Kizaru, Aokiji)
- Weather systems (Grand Line storms, Calm Belt)
- Sea Kings as environmental hazards
- Larger maps, more islands, more complex extraction routes

---

## Summary

Francisco has designed a game with a clear identity: One Piece factions racing to extract the One Piece across the Grand Line, with ship combat and ground combat. The faction system (captain = crew + ship + abilities) is genuinely clever asymmetric design.

The build path is: Three.js in the browser, Meshy for 3D models, Claude Code as the development interface. 8 sessions to a complete single-player prototype with full combat, ship sailing, enemies, and the extraction objective. The combat juice in Session 3 is the critical moment — if the Gum Gum Pistol feels right, the game has a future.

Multiplayer is the long-term goal but not the first milestone. Build something that feels amazing for one player first. The multiplayer conversation happens after that foundation is solid.
