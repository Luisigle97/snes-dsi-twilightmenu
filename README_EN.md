# SNEmulDS DSi TWL Bundle for TWiLight Menu++

[Español](README.md) | [English](README_EN.md)

[![Platform](https://img.shields.io/badge/Platform-Nintendo%20DSi%20%7C%20DSi%20XL-e60012.svg)](https://en.wikipedia.org/wiki/Nintendo_DSi)
[![Compatibility](https://img.shields.io/badge/TWiLight%20Menu%2B%2B-v27.25.1%2B-blue.svg)](https://github.com/DS-Homebrew/TWiLightMenu)
[![License](https://img.shields.io/badge/License-GPL--2.0-green.svg)](LICENSE)
[![Release](https://img.shields.io/badge/Release-v1.0.0-orange.svg)](https://github.com/Luisigle97/snes-dsi-twilightmenu/releases/tag/v1.0.0)

Optimized and modern **SNEmulDS (TWL DSi Mode @ 133 MHz)** bundle featuring native, direct integration for **TWiLight Menu++**.

This project resolves historical boot crashes, touchscreen lockups, empty ROM lists, and vertical scaling/jitter errors when emulating Super Nintendo (SNES) on Nintendo DSi and DSi XL consoles.

---

## Key Features and Improvements

1. **Native DSi Performance (TWL Mode @ 133 MHz):**
   * Uses the authentic `SNEmulDS.srl` binary with valid DSi header (`UnitCode = 0x02`), unlocking the full 133 MHz CPU speed and 16 MB of console RAM (bypassing the legacy 4 MB / 67 MHz DS Lite limitations).
2. **Direct ROM Launching (`autoboot = true`):**
   * Integrated via `snemulds-shim` (by Sanrax). Launching any `.sfc` or `.smc` game directly from TWiLight Menu++ boots straight into gameplay without stopping at the "Select ROM" screen.
3. **Flexible ROM Directory Support:**
   * Place your games wherever you prefer on your SD card (`sd:/snes/`, `sd:/roms/snes/`, `sd:/games/`, etc.). TWiLight Menu++ handles any custom path seamlessly via `ARG=%PATH%`.
4. **Firmware Auto-Language Detection (`Language = -1`):**
   * The touchscreen menu automatically detects the console's system language (Japanese, English, French, German, Italian, Spanish).
5. **Jitter-Free Centered Screen (`YScroll = 16`):**
   * Eliminated interlacing/shimmering vertical artifacts by setting vertical scroll to the exact mathematical center (`YScroll = 16`).
   * Configured global full-screen scaling (`Scaled = 2`) with bilinear filtering and per-game HUD protection (`BG3Squish`).
6. **Modernized Touch Interface:**
   * Clean, centered **SNEmulDS** title header.
   * Proportional button grid with modern 8px margins and balanced layout on the bottom touch screen.

---

## Repository Structure

```text
snes-dsi-twilightmenu/
|-- sd_card_package/             <-- Files ready to copy to your SD card
|   |-- _nds/
|   |   \-- TWiLightMenu/
|   |       |-- addons/Virtual Console
|   |       |-- emulators/
|   |       |   |-- snemulds-shim.nds
|   |       |   |-- snemulds-shim.ini
|   |       |   |-- SNEmulDS.srl
|   |       |   |-- SNEmulDS.nds
|   |       |   |-- SNEmulDS_0.6a.nds
|   |       |   |-- SNEmulDS-legacy.nds
|   |       |   |-- SNEmulDS-legacy-twlm-path.nds
|   |       |   \-- snemul.cfg
|   |       \-- extras/
|   |           |-- config.sfc.ini
|   |           \-- config.smc.ini
|   |-- snes/
|   |   \-- snemul.cfg
|   \-- snemul.cfg
|-- release/
|   \-- SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip
|-- README.md                    <-- Main documentation (Spanish)
|-- README_EN.md                 <-- Main documentation (English)
|-- GUIA_INSTALACION.md          <-- Step-by-step installation guide (Spanish)
|-- INSTALLATION_GUIDE.md        <-- Step-by-step installation guide (English)
|-- CONFIGURACION_PANTALLA.md    <-- Scaling modes & screen profiles (Spanish)
|-- SCREEN_CONFIG.md             <-- Scaling modes & screen profiles (English)
|-- CREDITS.md                   <-- Upstream authors and credits
|-- LICENSE                      <-- GNU GPL v2.0 License
\-- .gitignore
```

---

## Detailed Guides

* [Step-by-Step Installation Guide](INSTALLATION_GUIDE.md) | [Guia Paso a Paso de Instalacion](GUIA_INSTALACION.md)
* [Screen Scaling & Touch Menu Guide](SCREEN_CONFIG.md) | [Guia de Escalado de Pantalla y Menu Tactil](CONFIGURACION_PANTALLA.md)
* [Compatibility & Game Fixes Guide](COMPATIBILITY.md) | [Guia de Compatibilidad y Solucion de Juegos](COMPATIBILIDAD.md)
* [Credits & Attributions](CREDITS.md)

---

## Quick Download

You can download the complete bundle ready to extract to the root of your SD card from the Releases tab:

* **[Download SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip](https://github.com/Luisigle97/snes-dsi-twilightmenu/releases/download/v1.0.0/SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip)**

---

## Credits

This package was configured, patched, and optimized by **Luisigle97**, built upon the work of the homebrew community:
* **archeide:** Original creator of SNEmulDS.
* **bubble2k:** CPU emulation core.
* **gladius:** SPC audio emulation engine.
* **coto:** SNEmulDS DSi / TGDS modern core updates.
* **Sanrax:** Development of `snemulds-shim` and direct boot compatibility patches.
* **RocketRobz and TWiLight Menu++ team:** TWiLight Menu++ system and direct launchers.

---

## License

Distributed under the **GNU General Public License v2.0 (GPL-2.0)**. See [LICENSE](LICENSE) for details.
