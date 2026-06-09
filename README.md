# Ghost Cubes — Retro Neon FPS

> A cyberpunk-horror first-person shooter built with Three.js. Hunt ghost cubes across five procedurally-designed labyrinth maps in a neon-drenched retro aesthetic.

![Ghost Cubes](escenario%20celestial%20crypt.png)

## Description

**Ghost Cubes** is a fast-paced FPS where you navigate dark neon mazes, fight 50 ghostly cube enemies per map, collect weapons and medkits, and jump through portals to survive as long as possible. Every map has a unique visual theme, enemy variants, and layout — no two runs are the same.

Built entirely in a single HTML file using **Three.js** (WebGL), with procedural Web Audio sound effects, CSS-driven glassmorphism UI, and a Supabase-powered global leaderboard.

## Features

- **5 Unique Maps** — Celestial Crypt, Amber Abyss, Alabaster Labyrinth, Stepped Bastion, Kaleidoscope Prism
- **6 Weapons** — Default, Rapid Burst, Bomb (AoE), Shotgun (5 pellets), Laser (continuous beam), Ray (piercing)
- **15 Ghost Variants** — Scouts (fast, 1 HP), Soldiers (balanced, 2 HP), Tanks (slow, 3-4 HP), each with unique face textures and colors per map
- **Random Portal Teleportation** — Enter a portal to warp to a random different map
- **Height System (Map 4)** — Multi-level platforms with smooth player Y adjustment
- **Medkit Pickups** — 14 per map, heal 30 HP each
- **Global Leaderboard** — Supabase integration for cross-player scores
- **Procedural Sound** — Web Audio API synthesizer for every weapon and explosion
- **Glassmorphism UI** — Translucent panels with backdrop blur, floating particles, hacker-style glitch effects
- **Aerial Map Viewer** — Separate HTML page to inspect all 5 maps top-down with element indicators
- **Ghost Catalog** — Interactive 3D viewer showing all 15 enemy variants with stats

## How to Play

| Control | Action |
|---------|--------|
| `W A S D` | Move |
| `Mouse` | Look around |
| `Left Click` | Shoot |
| `Space` | Jump |
| `ESC` | Pause / Resume |

- **Goal**: Kill as many ghosts as possible. Each ghost kill = +1 score.
- **Portals**: Glowing rings on each map — walk through them to teleport to a random different map.
- **Pickups**: Green crosses = medkits (+30 HP). Colored rings = weapon upgrades.
- **Death**: 100 HP. Ghosts deal 15 damage on contact. When you die, your score is saved to the leaderboard.

## Maps

| # | Name | Theme | Size |
|---|------|-------|------|
| 1 | **Celestial Crypt** | Cyan on black, open corridors | 30×30 |
| 2 | **Amber Abyss** | Orange/amber on dark, tight passages | 30×30 |
| 3 | **Alabaster Labyrinth** | White/gray, complex maze | 30×30 |
| 4 | **Stepped Bastion** | Earthy tones, multi-height platforms | 30×30 |
| 5 | **Kaleidoscope Prism** | Magenta/black, colorful enemies | 30×30 |

### Map Screenshots

| Celestial Crypt | Amber Abyss | Alabaster Labyrinth |
|:---:|:---:|:---:|
| ![Map 1](escenario%20celestial%20crypt.png) | ![Map 2](escenario%20amber%20abyss.png) | ![Map 3](escenario%20alabaster%20labyrinth.png) |

| Stepped Bastion | Kaleidoscope Prism |
|:---:|:---:|
| ![Map 4](escenario%20steepped%20bastion.png) | ![Map 5](escenario%20kaleidoscope%20prism.png) |

## Ghost Variants

Every map spawns 3 ghost types with different colors, sizes, and behaviors:

| Type | Face | HP | Speed | Role |
|------|------|-----|-------|------|
| **Scout** | Happy | 1 | Fast | Swarm attacker |
| **Soldier** | Normal | 2 | Medium | Balanced threat |
| **Tank** | Angry | 3-4 | Slow | Bullet sponge |

[View complete Ghost Catalog →](catalogo-fantasmas.html)

## Weapons

| Weapon | Damage | Special |
|--------|--------|---------|
| Default | Single shot | Standard green bullet |
| Rapid | 3-bullet burst | Hold fire, every 5 frames |
| Bomb | AoE explosion | 4-unit blast radius |
| Shotgun | 5 pellets | Wide spread |
| Laser | Continuous beam | Fires every 4 frames |
| Ray | Piercing | Hits multiple ghosts |

## Technical Stack

- **Three.js r132** — 3D rendering (WebGL)
- **Web Audio API** — Procedural sound synthesis (no external audio files)
- **Supabase** — Global leaderboard (PostgreSQL)
- **CSS Glassmorphism** — UI design with backdrop-filter blur
- **Single-file architecture** — No build tools, no dependencies beyond Three.js CDN

## Aerial Map Viewer

Open [`vista-aerea-juego.html`](vista-aerea-juego.html) to see all 5 maps from a top-down orthographic view. Shows walls, portal locations, medkit positions, weapon pickups, and spawn points with a color-coded legend.

## Leaderboard Setup (Supabase)

The game includes a global leaderboard using **Supabase** (PostgreSQL). To enable it:

1. Create a free project at [supabase.com](https://supabase.com)
2. Go to **SQL Editor** and run:
```sql
CREATE TABLE scores (
  id SERIAL PRIMARY KEY,
  name TEXT NOT NULL,
  score INTEGER NOT NULL,
  time FLOAT NOT NULL,
  maps INTEGER NOT NULL,
  date BIGINT NOT NULL
);
CREATE POLICY "public_read" ON scores FOR SELECT USING (true);
CREATE POLICY "public_insert" ON scores FOR INSERT WITH CHECK (true);
ALTER TABLE scores ENABLE ROW LEVEL SECURITY;
```
3. Copy your **Project URL** and **anon key** from Settings > API
4. Paste them in `index.html` at the `SUPABASE_URL` and `SUPABASE_KEY` constants

Without Supabase configured, scores are saved in `localStorage` and work offline.

## Run Locally

Just open `index.html` in any modern browser. No server required.

For the aerial viewer: open `vista-aerea-juego.html`.
For the ghost catalog: open `catalogo-fantasmas.html`.

## Project Structure

```
ghost-cubes/
├── index.html                     # Main game (FPS)
├── vista-aerea-juego.html         # Aerial map viewer (top-down)
├── catalogo-fantasmas.html        # Ghost variant catalog (3D viewer)
├── escenario celestial crypt.png  # Map screenshot
├── escenario amber abyss.png      # Map screenshot
├── escenario alabaster labyrinth.png
├── escenario steepped bastion.png
├── escenario kaleidoscope prism.png
└── MUSICA/                        # Background music (not included)
```

## Credits

- **Game Design & Development**: Eduardo Fierro
- **Website**: [www.fierroduque.com](https://www.fierroduque.com)
- **Engine**: Three.js
- **Leaderboard**: Supabase

---

*Ghost Cubes — Retro FPS. Kill ghosts. Survive. Repeat.*
