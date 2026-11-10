# Step-by-Step Installation Guide

[Español](GUIA_INSTALACION.md) | [English](INSTALLATION_GUIDE.md)

This guide shows you how to install and configure the Super Nintendo (SNES) emulator package on your **Nintendo DSi or Nintendo DSi XL** running **TWiLight Menu++ (version v27.25.1 or newer)**.

---

## Prerequisites

1. A **Nintendo DSi or DSi XL** console with an SD card (formatted as FAT32).
2. **TWiLight Menu++** installed and working on your console.
3. The official release package: [SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip](https://github.com/Luisigle97/snes-dsi-twilightmenu/releases/download/v1.0.0/SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip)

---

## Installation Process

### Step 1: Connect the SD Card to your PC
* Turn off the console, remove the SD card, and insert it into your computer's card reader.

### Step 2: Copy the Files
* Open the downloaded ZIP file: `SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip`.
* Extract or copy all files and folders directly to the **root** of your SD card (e.g. `E:\`).
* If prompted to merge folders or replace existing files, choose **Yes to all / Replace**.

The resulting folder structure on your SD card will look like this:
```text
sd:/
|-- _nds/
|   \-- TWiLightMenu/
|       |-- addons/Virtual Console
|       |-- emulators/
|       |   |-- snemulds-shim.nds
|       |   |-- snemulds-shim.ini
|       |   |-- SNEmulDS.srl
|       |   |-- SNEmulDS.nds
|       |   |-- SNEmulDS_0.6a.nds
|       |   |-- SNEmulDS-legacy.nds
|       |   |-- SNEmulDS-legacy-twlm-path.nds
|       |   \-- snemul.cfg
|       \-- extras/
|           |-- config.sfc.ini
|           \-- config.smc.ini
|-- snes/
|   \-- snemul.cfg
\-- snemul.cfg
```

### Step 3: Add Your Games (ROMs)
* You can place your SNES ROMs (`.sfc` or `.smc`) wherever you prefer on your SD card.
* Common recommended locations:
  * `sd:/snes/`
  * `sd:/roms/snes/`
  * `sd:/games/snes/`
* Thanks to direct argument passing (`ARG=%PATH%`), TWiLight Menu++ will launch ROMs from any directory without restriction.

> **Tip:** Ensure game filenames do not contain trailing spaces before the extension (e.g. use `Super Mario World.sfc` instead of `Super Mario World .sfc`).

### Step 4: Configure CPU Clock Speed in TWiLight Menu++ (Recommended)
1. Reinsert the SD card into your Nintendo DSi / DSi XL and power it on.
2. Open **TWiLight Menu++**.
3. Press `SELECT` to open the **TWiLight Menu++ Settings**.
4. Navigate to the **Games/Homebrew Settings** page:
   * **ARM9 CPU Speed:** Set to `133 MHz (TWL)`.
   * **VRAM Boost:** Set to `Enabled`.
5. Press `(B)` to save and exit settings.

---

## How to Play

1. In the TWiLight Menu++ file browser, navigate to your games directory (e.g. `snes/`).
2. Highlight your game with the SNES cartridge icon.
3. Press **(A)** to boot the game.
4. The game will launch directly into full-speed DSi mode (133 MHz) with bilinear scaling adapted to the DSi display.

---

## Shortcuts and Frequently Asked Questions

* **Save state at any time:** Tap the bottom touchscreen during gameplay and tap **Guardar Juego / Save State**. To resume later, tap **Cargar Juego / Load State**.
* **Battery saves (SRAM):** After saving inside the game (e.g. overworld map in *Super Mario World* or a sanctuary in *Zelda*), tap the touchscreen, go to **Options**, and confirm SRAM writing before turning off the console.
* **Switching scaling modes:** Tap the touchscreen during play and tap the scaling toggle to cycle between `Scaled 2` (full screen), `Scaled 0` (1:1 pixel perfect with HUD squish), and `Scaled 1` (half scaled).
* **Firmware Language Auto-Detection:** The bottom touch menu automatically detects your console's system language (Japanese, English, French, German, Italian, Spanish).
