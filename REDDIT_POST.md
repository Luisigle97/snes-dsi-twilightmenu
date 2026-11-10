# [Release] SNEmulDS DSi TWL v1.1.0 – Fixed "couldnt find mem" Save Crash, Anti-Jitter Screen Fix, Auto-SRAM & Optimized TWiLight Menu++ Bundle!

**Target Subreddits:** `r/NDSHacks`, `r/NintendoDS`, `r/emulation`

---

## 🇬🇧 English Version (Copy & Paste for Reddit)

**Post Title:**
> [Release] SNEmulDS DSi TWL v1.1.0 – Fixed "couldnt find mem" Save Crash, Screen Anti-Jitter, Auto-SRAM & Pre-configured TWiLight Menu++ Bundle!

**Post Body:**

Hey everyone! 👋

If you have ever tried running Super Nintendo games on a **Nintendo DSi or DSi XL** using **TWiLight Menu++**, you probably ran into the same frustrating bugs that have plagued SNEmulDS builds for years:
* Attempting to Save State crashed the console with `couldnt find mem 66048/3840` and left a 0-byte corrupt save.
* Full-screen scaling had annoying scanline jitter (vibrating up and down 60 times per second).
* Characters and textures turning semi-transparent or invisible (like Mario on the map screen, Samus in liquid, or The Mask).
* Missing sky/cloud background layers due to disabled BG4.

We've spent time disassembling the emulator, diagnosing the root causes in ARM assembly, and putting together a plug-and-play **v1.1.0 bundle** that solves all of these issues!

---

### 🛠️ What's New & Fixed in v1.1.0:

1. **Fixed the Infamous Save State Freeze (`couldnt find mem 66048/3840`):**
   * *The Cause:* Upstream cotodevel SNEmulDS attempted a 66,048-byte dynamic heap allocation (`TGDSARM9Malloc(0x10200)`) for an SPC700 audio dump. With only ~3.8 KB of free heap during gameplay, this failed and triggered an upstream bug: `memset(NULL, 0, 0x10200)` which zeroed out ARM exception vectors at `0x00000000`, hard-locking the DSi immediately.
   * *The Fix:* Clean ARM assembly patch on `write_snapshot` and `read_snapshot` bypassing this allocation. State saving and loading now completes in **under 0.1 seconds with ZERO crashes**.

2. **Screen Anti-Jitter Patch (Rock-Solid Full Screen):**
   * *The Cause:* A legacy 2006 "temporal filter" in `ppu.c` toggled `lBG_Y0 += GFX.DSFrame & 1` on alternating frames. On DSi XL IPS screens, this looked like annoying screen vibration.
   * *The Fix:* Patched at `0x01B0BC` to remove the 1-pixel frame vibration. Full-screen scaling (`Scaled = 2`) and semi-scaled (`Scaled = 1`) are now **completely rock-solid, sharp, and flicker-free**.

3. **Automatic Battery Saves (`AutoSRAM = 1`):**
   * Previously set to `0` (off) by default. Now, whenever you save at an in-game save point (e.g. Castle in *Super Mario World*, Diary in *EarthBound*, Save Point in *Chrono Trigger*), SNEmulDS automatically commits the `.SRM` battery save to your SD card!

4. **Ghost Sprite & Missing Texture Fixes:**
   * Because Nintendo DS hardware lacks SNES-style per-pixel color math, SNES alpha blends caused entire character sprites to turn into translucent ghosts.
   * Disabled problematic transparencias (`Transparency = 0`) and enabled full BG4 (`BGLayers = 11111`) across top titles (*Super Mario World*, *Donkey Kong Country*, *The Mask*, *Aladdin*, *Super Metroid*, *Sunset Riders*, *Earthworm Jim*, *Zombies Ate My Neighbors*, etc.), keeping textures 100% opaque, sharp, and running at **solid 60 FPS**.

5. **Freeze-Free Exit:**
   * Safe dialog on touch menu with physical **POWER** button quick-exit instructions, avoiding unhandled DSi TWL BIOS soft-reset traps.

---

### 📦 Download & Source Code:

* **GitHub Repository:** [https://github.com/Luisigle97/snes-dsi-twilightmenu](https://github.com/Luisigle97/snes-dsi-twilightmenu)
* **Release v1.1.0 (.zip):** [https://github.com/Luisigle97/snes-dsi-twilightmenu/releases/tag/v1.1.0](https://github.com/Luisigle97/snes-dsi-twilightmenu/releases/tag/v1.1.0)

### 🚀 How to Install:
1. Download `SNEmulDS-DSi-TWiLightMenu-v1.1.0.zip`.
2. Extract the files directly onto the root of your SD card (merge folders if prompted).
3. Place your SNES ROMs into `/snes/` or `/ROMS/SNES/`.
4. Launch your games through TWiLight Menu++ and enjoy!

Huge thanks to the original creators (**archeide**, **bubble2k**, **gladius**, **coto**, **Sanrax**, and the **TWiLight Menu++** team) for laying the groundwork for DS homebrew!

Feel free to test it out and report your experience! 🎮

---

## 🇪🇸 Versión en Español (Para Foros / Reddit en Español)

**Título:**
> [Release] SNEmulDS DSi TWL v1.1.0 – ¡Solución al fallo de guardado "couldnt find mem", Pantalla Completa sin temblor, Auto-SRAM y Texturas arregladas!

**Cuerpo del Post:**

¡Hola a todos! 👋

Si alguna vez habéis intentado emular Super Nintendo en **Nintendo DSi o DSi XL** usando **TWiLight Menu++**, seguro que os habréis topado con fallos que llevaban años sin resolverse:
* Al intentar guardar partida (*Save State*), salía el error `couldnt find mem 66048/3840` y la consola se congelaba.
* En pantalla completa, las líneas horizontales vibraban arriba y abajo sin parar (efecto temblor/flicker).
* Personajes semitransparentes como fantasmas (*Mario*, *La Máscara*, *Aladdin*, *Samus*).
* Fondos o nubes desaparecidos por falta de la Capa 4.

Hemos estado analizando el código en ensamblador ARM, corrigiendo los bugs de memoria y preparando un paquete listo para usar: **v1.1.0**.

### 🛠️ ¿Qué incluye la versión v1.1.0?
1. **Solución definitiva al cuelgue al guardar:** Parche en ensamblador en `write_snapshot` y `read_snapshot`. Guarda y carga estados en < 0.1 segundos sin congelamientos.
2. **Parche Anti-Jitter en pantalla completa:** Eliminada la vibración artificial de 1 píxel. Modos `Scaled = 1` y `Scaled = 2` completamente estables y nítidos.
3. **Guardado automático de batería (`AutoSRAM = 1`):** Guarda automáticamente en tu SD al salvar en castillos, libretas o puntos de guardado.
4. **Texturas y personajes 100% sólidos:** Desactivadas transparencias problemáticas y activada la capa 4 (`BGLayers = 11111`) para que los juegos se vean con colores vivos a 60 FPS estables.
5. **Salida segura sin cuelgues:** Instrucciones claras en pantalla táctil para salir con el botón físico POWER.

### 📦 Enlaces:
* **Repositorio:** [https://github.com/Luisigle97/snes-dsi-twilightmenu](https://github.com/Luisigle97/snes-dsi-twilightmenu)
* **Descarga directa v1.1.0:** [https://github.com/Luisigle97/snes-dsi-twilightmenu/releases/tag/v1.1.0](https://github.com/Luisigle97/snes-dsi-twilightmenu/releases/tag/v1.1.0)
