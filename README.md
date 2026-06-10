# Ghost Cubes — Retro Neon FPS v2.0

> **Play online:** [https://eduardofierroduque-sudo.github.io/ghost-cubes/](https://eduardofierroduque-sudo.github.io/ghost-cubes/)

A cyberpunk-horror first-person shooter built with Three.js. Hunt ghost cubes across five procedurally-designed labyrinth maps in a neon-drenched retro aesthetic — the full evolution from the original Ghost Cat prototype.

### Companion Pages

| Page | Link | Description |
|------|------|-------------|
| **Aerial Map Viewer** | [Open →](https://eduardofierroduque-sudo.github.io/ghost-cubes/vista-aerea-juego.html) | Top-down view of all 5 maps with element indicators |
| **Ghost Catalog** | [Open →](https://eduardofierroduque-sudo.github.io/ghost-cubes/catalogo-fantasmas.html) | Interactive 3D renders of all 15 ghost variants |
| **Weapon Arsenal** | [Open →](https://eduardofierroduque-sudo.github.io/ghost-cubes/catalogo-armas.html) | 3D weapon catalog with stats for all 7 weapons |

---

## Table of Contents

- [From Ghost Cat to Ghost Cubes](#from-ghost-cat-to-ghost-cubes)
- [What's New in v2.0](#whats-new-in-v20)
- [Features](#features)
- [Maps](#maps)
- [Ghosts](#ghosts)
- [Weapons](#weapons)
- [How to Play](#how-to-play)
- [Technical Stack](#technical-stack)
- [Leaderboard (Supabase)](#leaderboard-setup-supabase)
- [Project Structure](#project-structure)
- [Methodology](#methodology)
- [First Version Archive](#first-version-archive)

---

## From Ghost Cat to Ghost Cubes

| | v1.0 — Ghost Cat | v2.0 — Ghost Cubes |
|---|---|---|
| **Maps** | 1 (10x10) | 5 (30x30 each) |
| **Ghosts** | Single type | 15 variants across 3 roles |
| **Weapons** | 1 (pistol) | 6 (Default, Rapid, Bomb, Shotgun, Laser, Ray) |
| **Sound** | External audio file | Web Audio API procedural synthesis |
| **Portals** | None | Random teleportation between maps |
| **UI** | Basic overlay | Glassmorphism + particles + hacker glitch |
| **Leaderboard** | None | Supabase + localStorage |
| **Height** | Flat | Multi-level platforms (Map 4) |
| **Tools** | None | Aerial map viewer + ghost catalog |
| **Codebase** | ~500 lines | ~1,650 lines |
| **Scope** | Prototype | Full game |

### Evolution Timeline

1. **Prototype** — Single-map maze FPS with basic movement, shooting, and enemy AI. Ghost Cat was a proof of concept validating Three.js as a browser game engine.

2. **Expansion** — Added 4 more maps with unique themes, 6 weapons with distinct mechanics, 15 ghost variants, portal teleportation, and procedural audio.

3. **Polish** — Glassmorphism UI redesign, floating particles, hacker-style glitch animations, pause system, background music crossfade, green-fluorescent name input.

4. **Infrastructure** — Supabase PostgreSQL leaderboard with localStorage fallback, GitHub Pages deployment, map viewer and ghost catalog companion pages.

---

## What's New in v2.0

### 5 Unique Labyrinth Maps
Every map has its own visual theme (wall colors, fog, lighting, ground grid) and layout complexity.

### 15 Ghost Variants
3 types per map (Scout, Soldier, Tank) × 5 maps = 15 unique configurations with different sizes, speeds, HP, face textures, and colors. [Browse catalog →](catalogo-fantasmas.html)

### 6 Weapons
Each with unique mechanics: spread shot, area damage, piercing, continuous beam, burst fire. Green-fluorescent pickups glow on the map.

### Random Portal System
Glowing ring on every map. Walk through it — teleported to a random other map. No fixed chain = unpredictable exploration.

### Glassmorphism UI
Translucent glass panels with `backdrop-filter: blur(20px)`, floating cyan/magenta particles, and hacker-style glitch animation (text-shadow + hue-rotate + skew, zero clip-path cuts).

### Global Leaderboard
Scores saved to Supabase PostgreSQL with automatic localStorage fallback. Players from anywhere see the same top 10.

### Companion Tools
- [**Aerial Map Viewer**](https://eduardofierroduque-sudo.github.io/ghost-cubes/vista-aerea-juego.html) — Top-down orthographic view of all 5 maps with color-coded indicators (portals, medkits, weapons, spawn).
- [**Ghost Catalog**](catalogo-fantasmas.html) — Interactive 3D renders of all 15 ghost variants with full stats.

---

## Features

- **Two Game Modes** — Massacre (80 ghosts, hardcore) and Little Hen (25 ghosts, easy) with visual theme switch and different soundtracks
- **5 Unique Maps** — Celestial Crypt, Amber Abyss, Alabaster Labyrinth, Stepped Bastion, Kaleidoscope Prism
- **6 Weapons** — Default, Rapid Burst, Bomb (AoE), Shotgun (5 pellets), Laser (continuous beam), Ray (piercing) with "GUN" floating labels
- **15 Ghost Variants** — Scouts (fast, 1 HP), Soldiers (balanced, 2 HP), Tanks (slow, 3-4 HP), each with unique face textures and colors per map
- **5 Portals Per Map** — Gold donut portals with "TUNNEL" labels, random teleportation between maps
- **Sprint Mechanic** — Hold `SHIFT` to run 1.8× faster
- **Random Spawn** — Player starts at a random open cell on each map
- **Medkit Pickups** — 14 per map, heal 30 HP each
- **Global Leaderboard** — Supabase PostgreSQL integration for cross-player scores
- **Procedural Sound** — Web Audio API synthesizer for every weapon and explosion
- **Dual Soundtrack** — Different original music per game mode
- **Glassmorphism UI** — Translucent panels with backdrop blur, floating particles, hacker-style glitch effects
- **Mode-Based Color Themes** — Cyan/blue for Massacre, pink/rose for Little Hen
- **Aerial Map Viewer** — Separate HTML page to inspect all 5 maps top-down
- **Ghost Catalog** — [Interactive 3D viewer](https://eduardofierroduque-sudo.github.io/ghost-cubes/catalogo-fantasmas.html) showing all 15 enemy variants with stats

---

## Maps

| # | Name | Theme | Size |
|---|------|-------|------|
| 1 | **Celestial Crypt** | Cyan on black, open corridors | 30×30 |
| 2 | **Amber Abyss** | Orange/amber on dark, tight passages | 30×30 |
| 3 | **Alabaster Labyrinth** | White/gray, complex maze | 30×30 |
| 4 | **Stepped Bastion** | Earthy tones, multi-height platforms | 30×30 |
| 5 | **Kaleidoscope Prism** | Magenta/black, flat layout, colorful enemies | 30×30 |

| Celestial Crypt | Amber Abyss | Alabaster Labyrinth |
|:---:|:---:|:---:|
| ![](escenario%20celestial%20crypt.png) | ![](escenario%20amber%20abyss.png) | ![](escenario%20alabaster%20labyrinth.png) |

| Stepped Bastion | Kaleidoscope Prism |
|:---:|:---:|
| ![](escenario%20steepped%20bastion.png) | ![](escenario%20kaleidoscope%20prism.png) |

---

## Ghosts

Ghost count depends on the selected game mode:

| Mode | Ghosts per Map |
|------|---------------|
| **Massacre** | 80 |
| **Little Hen** | 25 |

Each map spawns ghosts from 3 variant pools:

| Type | Face | HP | Speed | Role |
|------|------|-----|-------|------|
| **Scout** | Happy | 1 | Fast | Swarm attacker |
| **Soldier** | Normal | 2 | Medium | Balanced threat |
| **Tank** | Angry | 3-4 | Slow | Bullet sponge |

- **Attack**: Contact (<1.5 units), 15 damage, 300ms invulnerability window
- **Chase**: Within 25 units of player
- [View complete catalog →](https://eduardofierroduque-sudo.github.io/ghost-cubes/catalogo-fantasmas.html)

---

## Weapons

| Weapon | Damage | Special |
|--------|--------|---------|
| Default | Single shot | Standard green bullet |
| Rapid | 3-bullet burst | Hold fire, every 5 frames |
| Bomb | AoE explosion | 4-unit blast radius |
| Shotgun | 5 pellets | Wide spread |
| Laser | Continuous beam | Fires every 4 frames |
| Ray | Piercing | Hits multiple ghosts |

---

## Game Modes

| | Massacre | Little Hen |
|---|---|---|
| **Ghosts** | 80 per map | 25 per map |
| **Difficulty** | Hardcore | Easy |
| **UI Color** | Cyan/blue neon | Pink/rose neon |
| **Soundtrack** | Concrete Syntax (×2) | Little Hen Runs / Fleeing |
| **Spawn** | Random cell | Random cell |

Select the mode on the start screen below the name input. The entire UI theme switches instantly.

| Control | Action |
|---------|--------|
| `W A S D` | Move |
| `SHIFT` | Sprint (1.8× speed) |
| `Mouse` | Look around |
| `Left Click` | Shoot |
| `Space` | Jump |
| `ESC` | Pause / Resume |

- **Goal**: Kill as many ghosts as possible. Each ghost kill = +1 score.
- **Portals**: Gold donut rings labeled "TUNNEL" — walk through to teleport to a random map (5 per level).
- **Pickups**: Green crosses = medkits (+30 HP). Colored rings with "GUN" labels = weapon upgrades.
- **Spawn**: Random open cell on each map entry.

---

## Technical Stack

| Layer | Technology |
|-------|-----------|
| **Rendering** | Three.js r132 (WebGL) |
| **Audio** | Web Audio API (procedural synthesis) |
| **Database** | Supabase (PostgreSQL) |
| **UI** | CSS Glassmorphism + animations |
| **Architecture** | Single-file HTML (no build tools) |

---

## Leaderboard

The game is connected to a **Supabase** PostgreSQL database for global cross-player scores. The leaderboard is fully operational — all players see the same top 10 rankings.

### How it works
- On death, the player's score is saved to Supabase + `localStorage` (offline fallback)
- The leaderboard fetches and merges both sources, sorted by kills descending
- If Supabase is unreachable, the game continues working with local scores only

### The anon key is public
The `SUPABASE_KEY` visible in `index.html` is an **anon/public key** — it is designed by Supabase to be embedded in client-side code. It has `SELECT` and `INSERT` permissions only (no DELETE/UPDATE). The admin key is never exposed.

### Self-hosting
To use your own Supabase project:
1. Create a free project at [supabase.com](https://supabase.com)
2. Run the SQL below in the SQL Editor:
```sql
CREATE TABLE scores (id SERIAL PRIMARY KEY, name TEXT, score INT, time FLOAT, maps INT, date BIGINT);
CREATE POLICY "public_read" ON scores FOR SELECT USING (true);
CREATE POLICY "public_insert" ON scores FOR INSERT WITH CHECK (true);
ALTER TABLE scores ENABLE ROW LEVEL SECURITY;
```
3. Replace `SUPABASE_URL` and `SUPABASE_KEY` in `index.html` with your project values

---

## Project Structure

```
├── index.html                     # Main game
├── vista-aerea-juego.html         # Aerial map viewer
├── catalogo-fantasmas.html        # Ghost catalog (3D viewer)
├── MUSICA/                        # Massacre soundtrack (2 tracks)
│   └── MUSICA LITTLE HEN/         # Little Hen soundtrack (2 tracks)
├── escenario *.png                # Map screenshots
├── v1/                            # Ghost Cat v1.0 (archive)
│   ├── index.html                 # Original prototype
│   └── README.md                  # Original documentation
└── README.md                      # This file
```

---

## Methodology

### Development Approach
- **Iterative prototyping**: Started with minimal FPS (v1) → expanded to multi-map survival → polished UI/UX
- **Single-file architecture**: All HTML/CSS/JS in one file for zero-config deployment
- **Data-driven design**: Maps, themes, ghost configs, weapon stats defined as JavaScript arrays — easy to extend
- **Progressive enhancement**: Base game works offline (localStorage); Supabase adds global features without breaking

### Design Principles
- **Neon/Tron aesthetic** with cyberpunk glassmorphism
- **Brutalist typography** (font-weight 900, wide letter-spacing)
- **Hacker-style glitch** effects via pure CSS (no canvas tricks)
- **Performance-first**: MeshBasicMaterial for ghosts/walls, no PointLights, explosion particle limit ≤8

### Comparison v1 → v2.0

| Metric | v1.0 | v2.0 | Improvement |
|--------|------|------|-------------|
| Maps | 1 | 5 | 5× |
| Map size | 10×10 | 30×30 | 9× area |
| Ghost variants | 1 | 15 | 15× |
| Weapons | 1 | 6 | 6× |
| Game modes | 1 | 2 (Massacre / Little Hen) | 2× |
| Ghosts per map | Fixed | 80 / 25 per mode | Dynamic |
| Portals per map | None | 5 with "TUNNEL" labels | New |
| Movement | Walk | Walk + Sprint (SHIFT) | New |
| Lines of code | ~500 | ~1,750 | 3.5× |
| UI style | Basic overlay | Glassmorphism + dual themes | Complete redesign |
| Sound | External file | Procedural synth + dual soundtrack | Zero dependencies |
| Leaderboard | None | Supabase + local | New feature |
| Tools | None | Viewer + Catalog | New companion pages |

---

## First Version Archive

The original **Ghost Cat — Neon Protocol v1.0** prototype is preserved in the [`v1/`](v1/) directory. It served as the proof of concept:

- Single-map maze FPS (10×10)
- Basic WASD movement + mouse look
- Single ghost enemy type
- Simple health system
- Neon cyberpunk aesthetic

[View v1 source →](v1/index.html) | [Read v1 docs →](v1/README.md)

---

## Credits

- **Design & Development**: Eduardo Fierro
- **Website**: [www.fierroduque.com](https://www.fierroduque.com)
- **Engine**: [Three.js](https://threejs.org/)
- **Leaderboard**: [Supabase](https://supabase.com/)

---

*Ghost Cubes — Retro FPS. Kill ghosts. Survive. Repeat.*
