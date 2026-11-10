# Screen Scaling and Touch Menu Guide

[Español](CONFIGURACION_PANTALLA.md) | [English](SCREEN_CONFIG.md)

This guide details how Super Nintendo graphic rendering works on Nintendo DSi and DSi XL screens, and how to customize the visual experience to your preference.

---

## The Resolution Difference

| Console | Native Resolution | Aspect Ratio |
| :--- | :--- | :--- |
| **Super Nintendo (SNES)** | 256 x 224 (NTSC) / 256 x 239 (PAL) | 4:3 on CRT TVs (8:7 internal) |
| **Nintendo DSi / DSi XL** | 256 x 192 | 4:3 native per screen |

Notice a crucial detail: **The horizontal width is identical (256 pixels)**. Therefore, there is zero horizontal loss of sharpness. The only difference is the vertical height: the DSi screen has **32 fewer vertical lines** than SNES (224 - 192 = 32).

---

## Available Scaling Modes

In `snemul.cfg` or from the in-game touch menu, you can select between three scaling modes:

### 1. Full Screen Mode (`Scaled = 2`) - *Recommended Default*
* **How it works:** The emulator scales the 224 vertical lines down to 192 using a hardware-assisted bilinear filter.
* **Benefits:**
  * Displays 100% of the game picture.
  * No cropped life bars, text boxes, or HUD elements.
  * Fills the entire DSi XL upper screen.
* **Best suited for:** Text-heavy RPGs (*Chrono Trigger*, *Final Fantasy*), racing titles (*Top Gear*), or games with complex interfaces.

### 2. 1:1 Pixel-Perfect Mode with HUD Squish (`Scaled = 0`)
* **How it works:** Renders SNES graphics without compression (1 SNES pixel = 1 DSi pixel) for maximum crispness.
* **`BG3Squish` and `YScroll` technique:**
  * `BG3Squish = 1`: Compresses HUD layer 3 down by 16 pixels.
  * `BG3Squish = 2`: Compresses HUD layer 3 down by 32 pixels.
  * `YScroll = 16`: Perfectly centers the vertical viewport by cropping 16 lines from the top and 16 from the bottom (eliminating any scrolling jitter or interlacing shimmering).
* **Best suited for:** Fast action platformers (*Super Mario World*, *Donkey Kong Country*, *Castlevania IV*, *Super Metroid*).

### 3. Half-Scaled Mode (`Scaled = 1`)
* **How it works:** Applies minimal vertical compression, cropping only an 8-pixel border at the top and bottom.

---

## Live On-Screen Adjustments (Touch Menu)

You do not need to edit config files to test different modes:
1. During gameplay, **tap the bottom touchscreen** with your stylus or finger.
2. The modernized SNEmulDS touch interface appears.
3. Tap the **Scaling** button to cycle between `Scaled 0`, `Scaled 1`, and `Scaled 2`.
4. Changes apply in real time on the top screen so you can immediately find the best look for each game.

---

## Recommended Per-Game Presets

The bundled `snemul.cfg` includes pre-tuned settings for popular classics:

* **Super Mario World:**
  `SpeedHacks = 1 | Transparency = 0 | Scaled = 2 | BG3Squish = 0 | YScroll = 16`
* **Donkey Kong Country 1, 2 & 3:**
  `SpeedHacks = 0 | BGPriorities = 3 | Scaled = 2 | Vblank = 1 | YScroll = 16`
* **Chrono Trigger:**
  `Scaled = 2 | Vblank = 1 | Sound = 1 | YScroll = 16`
* **The Legend of Zelda: A Link to the Past:**
  `Scaled = 2 | Transparency = 0 | YScroll = 16`
* **Super Metroid:**
  `Scaled = 2 | SpeedHacks = 1 | Vblank = 1 | YScroll = 16`
* **Top Gear 1 & 2 / Top Racer:**
  `BGLayers = 10101 | Transparency = 0 | Vblank = 1 | SpeedHacks = 0 | Scaled = 2 | YScroll = 16`
  *(Note: Disabling layer BG2 prevents road glitches and split-screen flickering).*
* **The Mask:**
  `Transparency = 0 | BGPriorities = 1 | Vblank = 1 | SpeedHacks = 1 | Scaled = 2 | YScroll = 16`
  *(Note: Disabling transparencies prevents character sprites from vanishing).*
