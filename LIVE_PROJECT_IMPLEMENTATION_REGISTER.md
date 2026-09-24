# LIVE_PROJECT_IMPLEMENTATION_REGISTER — ZMI 3D Fleet Product Demo

**Project:** ZMI Holdings — Unreal-Level 3D Vessel Demonstration  
**Workspace:** `D:\AI\_others\3d-vessels`  
**Objective:** Product demonstration through interactive 3D vessel (rotation control + dimensions + highlights + capabilities)  
**Status:** 🟢 LIVE  |  **Last Update:** 2026-09-24 21:11 IST  |  **Owner:** Muse Spark (OpenCode)  
**Source:** https://zmiglobal.com  |  77 vessels scraped (39 Jack-Ups + 38 OSVs) | Data: `zmi-fleet/`

---

## 📌 Phase Tracker

| Phase | Title | Status | Progress | Key Deliverable |
|-------|-------|--------|----------|-----------------|
| **1** | Live Project Implementation Register | ✅ COMPLETED | 100% | `live_project_implementation_register.json` + this MD |
| **2** | Vessel Selection & Spec Freeze | 🔄 IN_PROGRESS | 90% | Hero: **QMS Achiever** (flagship JUB) frozen |
| **3** | Unreal-Level Three.js Build | 🔄 IN_PROGRESS | 0% → building | `demo/qms-achiever/index.html` |
| **4** | QA & Demonstration | ⏳ QUEUED | 0% | Demo URL + presets + video |

---

## 🎯 2) Selected Hero Vessel — **QMS Achiever**

> **Why Achiever?** Largest DP-2 class (1950m²), deepest water (80m), highest POB (500), twin cranes (2×190T) — perfect product hero to showcase ZMI's world-leading self-propelled JUB capability. Sister ships Gladiator (1×400T) / Sentinel (2×300T) are variants; Achiever is the most balanced demo.

| Field | Value |
|-------|-------|
| **Name** | QMS Achiever |
| **URL** | https://zmiglobal.com/fleet/qms-achiever/ |
| **Category** | Self-Propelled Jack-Up Barge |
| **IMO** | 9769946 | **Class:** ABS A1 Self-Elevating Unit, AMS, DPS-2, CRC, CPS, HELIDK(SRF), ENVIRO-OS | **Flag/Port:** Panama |
| **Year** | 2017 |
| **Hull** | 101.2m (L) × 44m (B) × 6.5m (D), Hull only 82.3m, Draft 4.05m (incl. spudcans), DWT 3954.88, Deck 1950m² @ 5.0/7.5 MT/m², Var Load 2200MT |
| **Legs** | 4× Triangular K-braced lattice, 107m ex spudcans (110m incl., 90m usable under hull), Rectangular spudcans 11.43×9.6×2.9m, Jetting 50m³/hr 6MPa |
| **Jacking** | Electric Rack & Pinion, 0.8 m/min hull, 1.2 m/min leg, 18 pinions/leg = 72 total, Storm load 360t/pinion |
| **Machinery** | Diesel-Electric, 6× CAT 3516B 1717kW (690V), Emergency CAT C18 383kW |
| **Propulsion** | 3× Azimuth 1300kW Well-type FPP VFD + 3× Bow Tunnel CPP 1100kW |
| **DP** | Kongsberg DP-2 |
| **Cranes** | Main: **2× WMMP CCOC 4000-190-43-EH 190T @15m / 35T @43m** (API 2C Zone II) | Aux: 1× WMMP AOC 500-500-25-EH 50T @10m / 10T @25m |
| **Helideck** | Aluminium 22.2m dia, 12.6T, S92A/S61N, CAP437, ABS HELIDK(SRF) |
| **Accommodation** | **250 POB → 500 upgradeable** |
| **Water Depth** | 80m max |

**Alternatives (if switch needed):** QMS Gladiator (1×400T), QMS Sentinel (2×300T), HEA Titan (2500m² largest deck).

---

## 🧱 3) Build Spec — Unreal-Level Three.js Stack

**Target file:** `demo/qms-achiever/index.html`

**Framework mix (brilliant JS):**
- `three@0.160.0` + `OrbitControls` + `CSS2DRenderer`/`CSS3DRenderer` (labels/hotspots)
- `postprocessing` (UnrealBloomPass, SSAO, ACESFilmicToneMapping)
- `lil-gui` (tweak) + `gsap 3.12` (micro-animations)
- `stats.js` (optional perf) — CDN importmap, no build step

**Model fidelity:**
- Hull (101.2×44×6.5m) PBR steel, deck 1950m² marked, accommodation block 4-storey hotel-style, helideck 22.2m, 4× lattice legs with spudcans, jacking pinions, twin 190T pedestal cranes + aux 50T, 6 thrusters, railings, lifeboats.
- Ocean plane (displacement + foam), sky dome gradient, sun + IBL, shadows, AO, reflections.
- Scale: **1 unit = 1 meter** — true dimensions.

**Interaction:**
- Manual: OrbitControls (drag rotate, scroll zoom, right-drag pan) + touch
- Auto: Toggle auto-rotate + speed (0.2–3×), pause on interaction
- Presets: Bow / Stern / Port / Starboard / Top / Helideck / Crane / Under-hull / Exploded leg view — GSAP camera tween

**Product Demo Overlays:**
- Dimension Callouts (LOA 101.2m, Beam 44m, Deck 1950m², Leg 107m, WD 80m, Crane 190T @15m)
- 6 Hotspots: Hull/Deck, Legs & Spudcans, Jacking System, DP Thrusters, Twin Cranes, Helideck & Accommodation
- Capability Cards: Greenfield/Brownfield/Rigless/P&A/Accommodation + Spec table + Highlights ticker
- Animations: Leg jacking (0.8m/min scaled), crane slew 360° + luff, thruster spin, day/night

---

## ✅ Phase 1 Log (Live)

| TS | Event |
|----|-------|
| 2026-09-24 21:10 | Register created; 77 vessels scraped |
| 2026-09-24 21:11 | QMS Achiever selected as hero; specs frozen |
| 2026-09-24 21:11 | Starting Phase 3: Three.js build |

## 🔜 Next Actions

1. Execute `demo/qms-achiever/index.html` build
2. Smoke test: `python -m http.server 8000` in workspace
3. Update register → Phase 3 COMPLETED → Phase 4 QA

---
**Owner:** Muse Spark | **Contact:** via workspace | **Repo style:** `live_project_implementation_register.json` is source-of-truth, this MD is view.
