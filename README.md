# SNEmulDS DSi TWL Bundle para TWiLight Menu++

[Español](README.md) | [English](README_EN.md)

[![Plataforma](https://img.shields.io/badge/Plataforma-Nintendo%20DSi%20%7C%20DSi%20XL-e60012.svg)](https://es.wikipedia.org/wiki/Nintendo_DSi)
[![Compatibilidad](https://img.shields.io/badge/TWiLight%20Menu%2B%2B-v27.25.1%2B-blue.svg)](https://github.com/DS-Homebrew/TWiLightMenu)
[![Licencia](https://img.shields.io/badge/Licencia-GPL--2.0-green.svg)](LICENSE)
[![Release](https://img.shields.io/badge/Release-v1.0.0-orange.svg)](https://github.com/Luisigle97/snes-dsi-twilightmenu/releases/tag/v1.0.0)

Paquete optimizado y modernizado de **SNEmulDS (Modo TWL DSi a 133 MHz)** con integracion nativa directa para **TWiLight Menu++**.

Este proyecto soluciona todos los problemas historicos de arranque, congelamiento de pantalla tactil, listas de ROMs vacias y errores de vibracion/escalado visual al emular Super Nintendo en consolas Nintendo DSi y DSi XL.

---

## Caracteristicas y Mejoras Aplicadas

1. **Rendimiento Nativo DSi (TWL Mode a 133 MHz):**
   * Emplea el binario legitimo `SNEmulDS.srl` con identificador DSi (`UnitCode = 0x02`), duplicando la velocidad del procesador de 67 MHz a 133 MHz y accediendo a los 16 MB de memoria RAM completa de la consola (evitando el modo legado de DS Lite de 4 MB).
2. **Arranque Directo sin Menus Intermedios (`autoboot = true`):**
   * Integracion mediante el puente `snemulds-shim` (desarrollado por Sanrax). Al seleccionar cualquier juego `.sfc` o `.smc` en TWiLight Menu++, arranca directamente la partida sin quedarse trabado en la pantalla de *"Seleccionar ROM"*.
3. **Libertad Total de Directorio de Juegos:**
   * Gracias al paso de argumentos dinamicos (`ARG=%PATH%`), puedes organizar tus juegos en la carpeta que prefieras en tu tarjeta SD (`sd:/snes/`, `sd:/roms/snes/`, `sd:/juegos/`, etc.) sin estar atado a una ruta fija.
4. **Deteccion Automatica del Idioma de la Consola (`Language = -1`):**
   * El menu inferior lee y detecta automaticamente el idioma del firmware de la consola (Espanol, Ingles, Frances, Aleman, Italiano, Japones).
5. **Centrado Vertical sin Entrelazado ni Jitter (`YScroll = 16`):**
   * Elimina las lineas de vibracion/intervalencia que causaba el desplazamiento asimetrico. La imagen queda centrada de forma matematica (16 pixeles arriba y abajo).
   * Escalado global en pantalla completa (`Scaled = 2`) con filtrado bilineal y proteccion de HUD (`BG3Squish`).
6. **Menu Tactil Modernizado:**
   * Barra de titulo superior limpia y centrada con el rotulo **SNEmulDS**.
   * Botones tactiles redisenados con proporciones y margenes modernos en la pantalla tactil inferior.

---

## Juegos Compatibles y Optimizados

Todos los siguientes titulos cuentan con perfiles nativos pre-configurados en `snemul.cfg`, optimizados para pantalla completa (`Scaled = 2`), centrado vertical (`YScroll = 16`), sincronizacion por hardware VBlank y audio a 32 kHz:

| Titulo | Estado | Optimizaciones Clave Aplicadas |
| :--- | :--- | :--- |
| **Super Mario World** | 🟢 60 FPS Perfecto | `SpeedHacks = 1`, `Scaled = 2`, `YScroll = 16` |
| **Donkey Kong Country 1, 2 y 3** | 🟢 60 FPS Perfecto | `BGPriorities = 3`, `Vblank = 1`, `Scaled = 2` |
| **The Legend of Zelda: A Link to the Past** | 🟢 60 FPS Perfecto | `Transparency = 0`, `Scaled = 2`, `YScroll = 16` |
| **Chrono Trigger** | 🟢 60 FPS Perfecto | `Vblank = 1`, `Sound = 1`, `Scaled = 2` |
| **Final Fantasy IV, V y VI** | 🟢 60 FPS Perfecto | `Vblank = 1`, `Sound = 1`, `Scaled = 2` |
| **Super Metroid** | 🟢 60 FPS Perfecto | `SpeedHacks = 1`, `Vblank = 1`, `Scaled = 2` |
| **Super Castlevania IV** | 🟢 60 FPS Perfecto | `Vblank = 1`, `Scaled = 2`, `YScroll = 16` |
| **TMNT IV: Turtles in Time** | 🟢 60 FPS Perfecto | `SpeedHacks = 1`, `Scaled = 2` |
| **Top Gear 1 y 2 / Top Racer** | 🟢 60 FPS Perfecto | `BGLayers = 10101` *(Capa BG2 apagada para reparar pista y division)* |
| **The Mask (La Mascara)** | 🟢 60 FPS Perfecto | `Transparency = 0`, `BGPriorities = 1` *(Sprites solidos sin parpadeo)* |
| **F-Zero** | 🟢 60 FPS Perfecto | `Scaled = 2`, `Vblank = 1` |
| **Aladdin (Capcom)** | 🟢 60 FPS Perfecto | `Vblank = 1`, `Scaled = 2` |
| **Goof Troop** | 🟢 60 FPS Perfecto | `Vblank = 1`, `Scaled = 2` |
| **Sunset Riders** | 🟢 60 FPS Perfecto | `SpeedHacks = 1`, `Vblank = 1`, `Scaled = 2` |
| **Super Bomberman 1 al 5** | 🟢 60 FPS Perfecto | `Vblank = 1`, `Scaled = 2` |
| **Contra III: The Alien Wars** | 🟢 60 FPS Perfecto | `Transparency = 0`, `Vblank = 1`, `Scaled = 2` |
| **Super Mario All-Stars** | 🟢 60 FPS Perfecto | `Scaled = 2`, `Vblank = 1` |
| **Earthworm Jim 1 y 2** | 🟢 60 FPS Perfecto | `Vblank = 1`, `Scaled = 2` |
| **Zombies Ate My Neighbors** | 🟢 60 FPS Perfecto | `Vblank = 1`, `Scaled = 2` |
| **Super Mario Kart** | 🟡 Jugable | Modo 7 funcional con ligero temblor de horizonte (`Vblank = 1`) |
| **EarthBound** | 🟡 Jugable | Efectos psicodelicos de batalla simplificados por matrices de DS |
| **Killer Instinct** | 🟡 Jugable | Rendimiento fluido con `SpeedHacks = 1` |

> 📖 Para ver el analisis tecnico completo de compatibilidad, soluciones a glitches y la lista de juegos con chips especiales no compatibles (SuperFX, SA-1, DSP-4), consulta la [Guia de Compatibilidad y Solucion de Juegos](COMPATIBILIDAD.md).

---

## Estructura del Repositorio

```text
snes-dsi-twilightmenu/
|-- sd_card_package/             <-- Archivos listos para copiar a tu SD
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
|-- README.md                    <-- Documentacion principal (Espanol)
|-- README_EN.md                 <-- Main documentation (English)
|-- GUIA_INSTALACION.md          <-- Guia paso a paso de instalacion
|-- INSTALLATION_GUIDE.md        <-- Step-by-step installation guide
|-- CONFIGURACION_PANTALLA.md    <-- Resoluciones, modos de escalado y perfiles
|-- SCREEN_CONFIG.md             <-- Resolutions, scaling modes & profiles
|-- CREDITS.md                   <-- Creditos de autores originales
|-- LICENSE                      <-- Licencia GNU GPL v2.0
\-- .gitignore
```

---

## Guias Detalladas

* [Guia Paso a Paso de Instalacion](GUIA_INSTALACION.md) | [Step-by-Step Installation Guide](INSTALLATION_GUIDE.md)
* [Guia de Escalado de Pantalla y Menu Tactil](CONFIGURACION_PANTALLA.md) | [Screen Scaling & Touch Menu Guide](SCREEN_CONFIG.md)
* [Guia de Compatibilidad y Solucion de Juegos](COMPATIBILIDAD.md) | [Compatibility & Game Fixes Guide](COMPATIBILITY.md)
* [Creditos y Reconocimientos](CREDITS.md)

---

## Descarga Rapida

Puedes descargar el paquete completo listo para descomprimir en la raiz de tu SD desde la pestana de Releases:

* **[Descargar SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip](https://github.com/Luisigle97/snes-dsi-twilightmenu/releases/download/v1.0.0/SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip)**

---

## Creditos

Este paquete fue configurado, parcheado y optimizado por **Luisigle97**, construido sobre el trabajo de la comunidad homebrew:
* **archeide:** Creador original de SNEmulDS.
* **bubble2k:** Nucleo de emulacion de CPU.
* **gladius:** Motor de emulacion de sonido SPC.
* **coto:** Actualizaciones del nucleo SNEmulDS DSi / TGDS.
* **Sanrax:** Desarrollo de `snemulds-shim` y parches de compatibilidad de arranque directo.
* **RocketRobz y equipo TWiLight Menu++:** Sistema TWiLight Menu++ y lanzadores directos.

---

## Licencia

Distribuido bajo la licencia **GNU General Public License v2.0 (GPL-2.0)**. Consulta [LICENSE](LICENSE) para mas detalles.
