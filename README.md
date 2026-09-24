# ZMI 3D Fleet — Product Demonstration Platform

**Live Demo:** `http://localhost:8765/demo/qms-achiever/` → `demo/qms-achiever/index.html`  
**Register:** `live_project_implementation_register.json` + `LIVE_PROJECT_IMPLEMENTATION_REGISTER.md`

## Quick Start
```bash
cd D:\AI\_others\3d-vessels
python -m http.server 8765
# open http://localhost:8765/demo/qms-achiever/
```

## What's Built

### Step 1 — Live Project Implementation Register ✅
- `live_project_implementation_register.json` — source-of-truth (4 phases, live log, KPIs, demo_url)
- `LIVE_PROJECT_IMPLEMENTATION_REGISTER.md` — human view with Phase Tracker
- Tracks 77 vessels scraped from zmiglobal.com (39 Jack-Ups + 38 OSVs)

### Step 2 — Hero Vessel → QMS Achiever ✅
Selected flagship **QMS Achiever** (IMO 9769946, 2017, Panama):
- **Hull 101.2×44×6.5m** (82.3m hull only), Draft 4.05m, DWT 3954.88, Deck **1,950m²** @ 5.0/7.5 MT/m², Var 2200MT
- **4× K-braced lattice legs 107m** (90m usable, 110m incl. spudcans), spudcans 11.43×9.6×2.9m, 80m WD
- **Electric rack & pinion 72 pinions** (0.8/1.2 m/min, 360t storm)
- **Twin WMMP 190T @15m / 35T @43m** (API 2C) + Aux 50T @10m
- **Kongsberg DP-2**, 3×1300kW azimuth + 3×1100kW bow, Diesel-Electric 6× CAT3516B
- **Helideck Ø22.2m** ALU 12.6T (S92A/S61N CAP437) + **250→500 POB**

Full specs in `zmi-fleet/` and register.

### Step 2 — Unreal-Level 3D Model ✅

**File:** `demo/qms-achiever/index.html` (47.9 KB, single-file, no build)

**Stack (brilliant JS):**
- `three@0.160.0` + `OrbitControls` + `CSS2DRenderer` + `RoomEnvironment` + `EffectComposer` (RenderPass + SSAOPass + UnrealBloomPass + OutputPass)
- `gsap@3.12.5` (camera/leg/crane tweens)
- `lil-gui@0.19` (exposure/bloom/speed)
- `es-module-shims` (importmap)

**Unreal-level fidelity:**
- PBR materials (hull steel, deck, accommodation glass, helideck green, lattice legs red, crane yellow), ACESFilmicToneMapping, PCFSoftShadowMap 2048, fog, envMap, ocean plane + sky dome + grid, SSAO + Bloom
- True scale: 1 unit = 1 meter. Hull + deck + 4-deck accommodation (bridge, lifeboats) + helideck with supra structure + 4× detailed K-braced triangular lattice legs (3 chords, horizontals + diagonals every 6m, rack teeth, jack houses, rectangular spudcans with points) + twin 31m ped. cranes (pedestal, slew ring, boom lattice, hook) + aux crane + 6 thrusters with spinning props + railings + deck markings

**Dimensions / Highlights / Capabilities (product demo overlays):**
- Left panel: 10 spec cards (Hull/Legs/Cranes/Helideck/DP/POB) + pills
- Right panel: 6 interactive hotspots (Hull→Port, Legs→Port, Cranes→Crane, DP→Starboard, Heli→Helideck, Jacking) + 5 capability cards (Greenfield/Brownfield/Rigless/P&A/Accommodation) + Fleet context
- 7 CSS2D dimension labels (LOA 101.2m, Beam 44m, Deck 1950m², Leg 107m, WD 80m, Crane 190T, Helideck Ø22.2m) + 6 pulsating hotspot dots with tooltips + bottom dimension callouts

**Rotation Control — Auto / Manual:**
- Manual: OrbitControls (drag rotate, scroll zoom, shift-drag pan, touch)
- Auto: Toggle `Auto ON/OFF` + speed slider 0.1–2.5× (0.6× default), pauses on interaction, resumes on release
- Presets: Bow / Stern / Port / Starboard / Top / Helideck / Crane (GSAP 1.1s power3 ease)
- Extra: Jacking Elevated↔Transit (-38m leg travel + vessel bob), Crane Slew (continuous 360°), Exploded (+6m legs, +6m cranes, +8m accom), Ocean/bloom/exposure GUI

**Product Demo Mode:**
- One-click `▶ Product Demo` cycles 7 steps: Port (hull) → Crane (twin 190T) → Bow (legs) → Starboard (DP) → Helideck (POB) → Jacking transit→elevated → complete. Each with toast + camera preset + animation. 1.7s per step.

## Controls Cheat Sheet

| Action | How |
|--------|-----|
| **Rotate** | Drag (or auto-toggle) |
| **Zoom** | Scroll / pinch |
| **Pan** | Right-drag |
| **Auto Rotate** | Toggle + slider 0.1–2.5× |
| **Presets** | Bow/Stern/Port/Starboard/Top/Helideck/Crane buttons |
| **Jacking** | Button or lil-gui → Elevated vs Transit |
| **Slew** | Slew Cranes button (continuous) |
| **Exploded** | Exploded button or lil-gui |
| **Demo** | Top CTA `▶ Product Demo` |
| **Tweak** | lil-gui top-right (bloom, exposure, ocean) |

## Data Source

Scraped 2026-09-24: `https://zmiglobal.com/fleet-sitemap.xml` (77 URLs) → 77 product sheets → `zmi-fleet/fleet_raw.json`, `fleet_summary.json`, `fleet_detailed.csv`, `jackups.csv`, `osvs.csv`, `FLEET_REPORT.md`

Timeline/claims from `/our-story/` (2024: 39+63=102 vessels, 1984 foundation, ADNOC L&S 2022).

## Next (Phase 4)

- Handover screenshots/video
- Clone for second vessel (Gladiator 1×400T or Titan 2500m²) — duplicate folder and swap specs

---
Owner: Muse Spark (OpenCode) — 2026-09-24
