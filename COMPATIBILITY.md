# SNEmulDS Compatibility & Game Fixes Guide

[Español](COMPATIBILIDAD.md) | [English](COMPATIBILITY.md)

This guide details the compatibility level of Super Nintendo (SNES) games running via **SNEmulDS** on **Nintendo DSi and DSi XL** systems under **TWiLight Menu++**, along with step-by-step instructions to fix common issues in popular games.

---

## Contents
1. [How to Fix Problematic Games (Top Gear & The Mask)](#how-to-fix-problematic-games)
   - [Top Gear 1 & 2 (and Top Racer)](#1-top-gear-1--2-and-top-racer)
   - [The Mask](#2-the-mask)
   - [Missing Textures & Backgrounds in Any Game](#3-fixing-missing-textures--backgrounds-in-any-game)
2. [Master Compatibility List](#master-compatibility-list)
   - [Tier 1: 100% Compatible (60 FPS / Flawless)](#tier-1-100-compatible-60-fps--flawless)
   - [Tier 2: Playable with Minor Tweaks](#tier-2-playable-with-minor-tweaks)
   - [Tier 3: Incompatible Games (Special Chips)](#tier-3-incompatible-games-special-chips)
3. [Official Community Database](#official-community-database)

---

## How to Fix Problematic Games

### 1. Top Gear 1 & 2 / Top Racer

#### The Problem
When starting a race, the asphalt track appears split in half, flickers with grey/black artifacts, or the split-screen obscures the horizon.

#### Technical Cause
*Top Gear* uses raster line interrupts (HDMA) on **Background Layer 2 (BG2)** of the SNES to render pseudo-3D curved road perspective. The Nintendo DS 2D graphics engine has a limited hardware layer pipeline that cannot composite this rasterization in real time, causing corrupt tiles across the road.

#### The Fix
Disable layer **BG2** and synchronize with hardware **VBlank**:
* **Automatic Fix:** Pre-configured in our `snemul.cfg`:
  ```ini
  [TOP GEAR]
  BGLayers = 10101
  Transparency = 0
  Vblank = 1
  SpeedHacks = 0
  Scaled = 2
  YScroll = 16
  Sound = 1
  ```
  *(Setting `BGLayers = 10101` keeps BG1, BG3, BG4, and Sprites active while disabling only BG2).*
* **How to configure live on console:**
  1. Boot the game and touch the bottom screen to bring up the SNEmulDS touch menu.
  2. Tap **Avanzado** (or **Options** -> **Layers**).
  3. Uncheck **BG2** (Layer 2).
  4. Turn off **Transparency** (`Transparency: OFF`).
  5. Ensure **Vblank** is enabled (`Vblank: 1`).
  6. The road will render cleanly and the game will maintain a rock-solid 60 FPS!

> [!NOTE]
> **What about Top Gear 3000?**
> *Top Gear 3000* cannot run on SNEmulDS because its cartridge houses the proprietary **DSP-4** co-processor chip. SNEmulDS lacks DSP-4 emulation support (see Special Chips section below).

---

### 2. The Mask

#### The Problem
During gameplay, The Mask (Jim Carrey) and several enemy sprites flicker, become invisible, or render behind walls and floors, rendering the game unplayable.

#### Technical Cause
*The Mask* utilizes per-tile priority mechanisms and alpha blending modes for comic-book shadow effects. On Nintendo DS hardware, the blending engine misinterprets the character sprite channel, culling it or pushing it behind lower background planes.

#### The Fix
Disable color blending and enforce background priority ordering:
* **Automatic Fix:** Pre-configured in our `snemul.cfg`:
  ```ini
  [THE MASK]
  Transparency = 0
  BGPriorities = 1
  Vblank = 1
  SpeedHacks = 1
  Scaled = 2
  YScroll = 16
  Sound = 1
  ```
* **How to configure live on console:**
  1. Touch the bottom screen to open the SNEmulDS menu.
  2. Go to **Options** -> **Graphics Settings**.
  3. Toggle **Transparency** to **OFF** (`Transparency = 0`).
  4. Enable **BG Priorities** (`BGPriorities = 1`).
  5. Save game settings. The Mask and all enemies will remain fully visible and solid.

---

### 3. Fixing Missing Textures & Backgrounds in Any Game

#### Why do some SNES games have missing textures or tiles on Nintendo DS?
1. **The 4th Layer (BG4) Disabled by Default:** In the original 2007 emulator, SNES Background Layer 4 was disabled (`BGLayers = 10111`) to conserve battery on Nintendo DS Lite. In our bundle, we enabled it globally (`BGLayers = 11111`) leveraging the 133 MHz DSi ARM9 CPU, restoring skies, clouds, HUD elements, and secondary textures.
2. **Transparency Blending Conflicts (Alpha Math):**
   * The original Super Nintendo could add and subtract lighting across 4 simultaneous layers (e.g., fog + water + sprites + background).
   * The Nintendo DS 2D hardware engine can only blend **two layers simultaneously**.
   * When a game attempts complex multi-layer blending, the DS cannot composite the result and calculates full transparency (`Alpha = 0`) or solid black, making **entire blocks of textures, text boxes, or sprites invisible**.
   * **Fix:** Turn transparency off (`Transparency: OFF`). Disabling it immediately draws all underlying textures solid and sharp.
3. **Per-Tile Priorities:**
   * On SNES, individual 8x8 tiles have their own priority bit. On Nintendo DS, priority applies to an entire layer.
   * If ground or wall textures render behind scenery, changing **BG Priorities** to `1` or `3` in the touch menu brings them back to the foreground.

#### Step-by-Step Fix Live on Console Touchscreen:
1. During gameplay, touch the bottom screen to open the SNEmulDS touch menu.
2. Tap **Options** (or **Advanced**).
3. Switch **Transparency** to **OFF** (`Transparency: OFF`). *(This fixes ~80% of missing texture issues in SNES games).*
4. Open **Layers** and make sure all layers are checked: `BG1`, `BG2`, `BG3`, `BG4`, and `Sprites`.
5. If a character or floor tile is covered by background scenery, tap **BG Priorities** and test between `1`, `2`, or `3` until the ordering is correct.

---

## Master Compatibility List

### Tier 1: 100% Compatible (60 FPS / Flawless)

These games run at full native 60 frames per second, with crystal-clear 32 kHz audio and no critical glitches:

| Title | Genre | Recommended Settings |
| :--- | :--- | :--- |
| **Super Mario World** | Platformer | `SpeedHacks = 1`, `Scaled = 2`, `YScroll = 16` |
| **Donkey Kong Country 1, 2 & 3** | Platformer | `BGPriorities = 3`, `Vblank = 1`, `Scaled = 2` |
| **The Legend of Zelda: A Link to the Past** | Action / RPG | `Transparency = 0`, `Scaled = 2`, `YScroll = 16` |
| **Chrono Trigger** | JRPG | `Vblank = 1`, `Sound = 1`, `Scaled = 2` |
| **Final Fantasy IV, V & VI** | JRPG | `Scaled = 2`, `Vblank = 1`, `Sound = 1` |
| **Super Metroid** | Adventure | `SpeedHacks = 1`, `Vblank = 1`, `Scaled = 2` |
| **Super Castlevania IV** | Action | `Vblank = 1`, `Scaled = 2`, `YScroll = 16` |
| **TMNT IV: Turtles in Time** | Beat 'em up | `SpeedHacks = 1`, `Scaled = 2` |
| **F-Zero** | Mode 7 Racing | `Scaled = 2`, `Vblank = 1` |
| **Secret of Mana** | Action / RPG | `Vblank = 1`, `Scaled = 2` |
| **Aladdin (Capcom)** | Platformer | `Vblank = 1`, `Scaled = 2` |
| **The Lion King** | Platformer | `Vblank = 1`, `Scaled = 2` |
| **Goof Troop** | Puzzle / Adventure | `Vblank = 1`, `Scaled = 2` |
| **Mega Man X (X1)** | Action | `SpeedHacks = 1`, `Vblank = 1`, `Scaled = 2` |
| **Zombies Ate My Neighbors** | Action | `Vblank = 1`, `Scaled = 2` |
| **Sunset Riders** | Run & Gun | `Vblank = 1`, `Scaled = 2` |
| **Super Bomberman 1 through 5** | Arcade / Party | `Vblank = 1`, `Scaled = 2` |
| **Contra III: The Alien Wars** | Action / Shooter | `Transparency = 0`, `Vblank = 1`, `Scaled = 2` |
| **Top Gear 1 & 2 / Top Racer** | Racing | `BGLayers = 10101`, `Transparency = 0`, `Vblank = 1` |
| **The Mask** | Action / Platformer | `Transparency = 0`, `BGPriorities = 1`, `Vblank = 1` |
| **Super Mario All-Stars** | Platformer | `Scaled = 2`, `Vblank = 1` |
| **Super Punch-Out!!** | Sports / Boxing | `SpeedHacks = 1`, `Scaled = 2` |
| **Demon's Crest** | Action | `Vblank = 1`, `Scaled = 2` |
| **Wild Guns** | Arcade Shooter | `Vblank = 1`, `Scaled = 2` |
| **NBA Jam / Tournament Edition** | Sports | `Vblank = 1`, `Scaled = 2` |
| **Earthworm Jim 1 & 2** | Action | `Vblank = 1`, `Scaled = 2` |

---

### Tier 2: Playable with Minor Tweaks

Games that can be completed from start to finish with minor visual compromises in backgrounds or transparencies:

* **Super Mario Kart:** Mode 7 track rendering works well and is fully playable. Minor texture jitter on distant horizon. Requires `Vblank = 1` and `Scaled = 2`.
* **EarthBound:** Fully playable; psychedelic battle background swirl effects are simplified due to DS matrix limitations.
* **Killer Instinct:** Smooth gameplay with `SpeedHacks = 1` enabled.
* **Mortal Kombat II & 3:** Very fluid; toggle `Transparency = 0` if shadow blending produces box artifacts.
* **Super Street Fighter II:** High framerate; subtle lines under character shadow sprites on select stages.
* **Breath of Fire I & II:** 100% playable throughout.
* **ActRaiser 1 & 2:** Smooth performance across both action and simulation sequences.

---

### Tier 3: Incompatible Games (Special Chips)

Unlike newer platforms, the Nintendo DS/DSi runs SNEmulDS using hand-tuned ARM assembly emulation specifically optimized for the primary SNES CPU (65816) and audio unit (SPC700).

Certain SNES cartridges incorporated **custom co-processor chips directly onto the cartridge board**. SNEmulDS **does not emulate these secondary silicon chips**, so the following games will not boot or will hang on a black screen:

| Special Chip | Affected Games | Technical Explanation |
| :--- | :--- | :--- |
| **SuperFX / SuperFX 2** | *Star Fox*, *Super Mario World 2: Yoshi's Island*, *Doom*, *Stunt Race FX*, *Vortex*, *Dirt Trax FX* | Secondary 21 MHz RISC coprocessor for 3D polygonal geometry and sprite scaling. |
| **SA-1 (Super Accelerator)** | *Super Mario RPG*, *Kirby Super Star*, *Kirby's Dream Land 3*, *Dragon Ball Z: Hyper Dimension* | Secondary 65C816 CPU clocked at 10.74 MHz with fast memory DMA controller. |
| **DSP-3 / DSP-4** | ***Top Gear 3000***, *SD Gundam GX* | DSP coprocessor for real-time AI vehicle route tracing and pseudo-3D perspective math. *(This is why Top Gear 1 & 2 work great, but Top Gear 3000 cannot boot).* |
| **S-DD1** | *Street Fighter Alpha 2*, *Star Ocean* | Real-time hardware ROM decompression chip. |
| **Cx4** | *Mega Man X2*, *Mega Man X3* | Math DSP for 3D wireframe transformations during boss battles. |
| **OBC1** | *Metal Combat: Falcon's Revenge* | Hardware sprite processor for the Super Scope light gun. |

---

## Official Community Database

The Nintendo DS homebrew community has curated the official compatibility list over years of real-hardware testing:

* **[SNEmulDS Official Compatibility List on GBAtemp](https://wiki.gbatemp.net/wiki/SNEmulDS_Compatibility_List)**

Use this list to look up any specific title alphabetically and check community-tested layer settings and speed hacks.
