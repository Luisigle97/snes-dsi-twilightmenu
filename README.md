# ðŸŽ® SNEmulDS DSi TWL Bundle para TWiLight Menu++

[![Plataforma](https://img.shields.io/badge/Plataforma-Nintendo%20DSi%20%7C%20DSi%20XL-e60012.svg)](https://es.wikipedia.org/wiki/Nintendo_DSi)
[![Compatibilidad](https://img.shields.io/badge/TWiLight%20Menu%2B%2B-v27.25.1%2B-blue.svg)](https://github.com/DS-Homebrew/TWiLightMenu)
[![Licencia](https://img.shields.io/badge/Licencia-GPL--2.0-green.svg)](LICENSE)
[![Release](https://img.shields.io/badge/Release-v1.0.0-orange.svg)](https://github.com/Luisigle97/snes-dsi-twilightmenu/releases/download/v1.0.0/SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip)

Paquete optimizado y actualizado de **SNEmulDS (Modo TWL DSi a 133 MHz)** con integraciÃ³n nativa directa para **TWiLight Menu++**.

Este proyecto soluciona todos los problemas histÃ³ricos de arranque, congelamiento de pantalla tÃ¡ctil, listas de ROMs vacÃ­as y errores de escalado visual al emular Super Nintendo en consolas Nintendo DSi y DSi XL.

---

## ðŸŒŸ CaracterÃ­sticas y Mejoras Aplicadas

1. **Rendimiento Nativo DSi (TWL Mode a 133 MHz):**
   * Emplea el binario legÃ­timo `SNEmulDS.srl` con identificador DSi (`UnitCode = 0x02`), duplicando la velocidad del procesador de 67 MHz a 133 MHz y accediendo a los 16 MB de memoria RAM completa de la consola (evitando el modo legado de DS Lite de 4 MB).
2. **Arranque Directo sin MenÃºs Intermedios (`autoboot = true`):**
   * IntegraciÃ³n mediante el puente `snemulds-shim` (por Sanrax). Al seleccionar cualquier juego `.sfc` o `.smc` en TWiLight Menu++, arranca directamente la partida sin quedarse trabado en la pantalla de *"Seleccionar ROM"*.
3. **Parcheo en Memoria RAM DinÃ¡mico:**
   * Corrige el fallo crÃ­tico del ejecutable DSi oficial donde la pantalla tÃ¡ctil dejaba de responder.
   * Restaura y desmutea los canales de audio por hardware de la DSi en la transiciÃ³n de arranque.
4. **Escalado de Pantalla Optimizado:**
   * Configurado globalmente en `Scaled = 2` (pantalla completa adaptada a los 192 pÃ­xeles verticales de la DSi) con filtrado bilineal para evitar deformaciones bruscas.
   * Compatibilidad con recorte 1:1 pixel-perfect y compresiÃ³n de HUD (`BG3Squish`) para juegos como *Super Mario World*, *Donkey Kong Country*, *Chrono Trigger* y *The Legend of Zelda*.
5. **MenÃº TÃ¡ctil Modernizado en EspaÃ±ol:**
   * MenÃº inferior configurado en EspaÃ±ol (`Language = 5`), con diseÃ±o centrado y accesible al tocar la pantalla tÃ¡ctil.

---

## ðŸ“¦ Estructura del Repositorio

```text
snes-dsi-twilightmenu/
â”œâ”€â”€ sd_card_package/             <-- Archivos listos para copiar a tu tarjeta SD
â”‚   â”œâ”€â”€ _nds/
â”‚   â”‚   â””â”€â”€ TWiLightMenu/
â”‚   â”‚       â”œâ”€â”€ addons/Virtual Console
â”‚   â”‚       â”œâ”€â”€ emulators/
â”‚   â”‚       â”‚   â”œâ”€â”€ snemulds-shim.nds
â”‚   â”‚       â”‚   â”œâ”€â”€ snemulds-shim.ini
â”‚   â”‚       â”‚   â”œâ”€â”€ SNEmulDS.srl       (TWL 133 MHz)
â”‚   â”‚       â”‚   â”œâ”€â”€ SNEmulDS.nds       (NTR Fallback)
â”‚   â”‚       â”‚   â”œâ”€â”€ SNEmulDS_0.6a.nds  (ClÃ¡sico 2007)
â”‚   â”‚       â”‚   â””â”€â”€ snemul.cfg
â”‚   â”‚       â””â”€â”€ extras/
â”‚   â”‚           â”œâ”€â”€ config.sfc.ini     (Lanzador directo)
â”‚   â”‚           â””â”€â”€ config.smc.ini     (Lanzador directo)
â”‚   â”œâ”€â”€ snes/                          <-- Carpeta donde van tus juegos .smc / .sfc
â”‚   â”‚   â””â”€â”€ snemul.cfg
â”‚   â””â”€â”€ snemul.cfg                     <-- ConfiguraciÃ³n global con perfiles optimizados
â”œâ”€â”€ release/
â”‚   â””â”€â”€ SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip  <-- Paquete comprimido listo para descargar
â”œâ”€â”€ GUIA_INSTALACION.md          <-- GuÃ­a paso a paso para usuarios
â”œâ”€â”€ CONFIGURACION_PANTALLA.md    <-- Manual tÃ©cnico de escalado y pantalla tÃ¡ctil
â”œâ”€â”€ CREDITS.md                   <-- Atribuciones y licencias originales
â””â”€â”€ README.md
```

---

## ðŸš€ InstalaciÃ³n RÃ¡pida

1. Descarga el archivo comprimido desde la carpeta [[SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip](https://github.com/Luisigle97/snes-dsi-twilightmenu/releases/download/v1.0.0/SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip)](https://github.com/Luisigle97/snes-dsi-twilightmenu/releases/download/v1.0.0/SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip).
2. Descomprime su contenido en la raÃ­z de la tarjeta SD de tu Nintendo DSi / DSi XL (combinando las carpetas `_nds` y `snes`).
3. Coloca tus juegos de Super Nintendo (`.sfc` o `.smc`) dentro de la carpeta `sd:/snes/`.
4. Enciende tu Nintendo DSi XL, entra a **TWiLight Menu++**, selecciona tu juego y Â¡listo!

Para una guÃ­a mÃ¡s detallada con resoluciÃ³n de dudas, consulta la [GuÃ­a de InstalaciÃ³n Completa](GUIA_INSTALACION.md).

---

## ðŸŽ® Opciones de Escalado y MenÃº TÃ¡ctil

| Modo | Ajuste en `snemul.cfg` | Comportamiento | Recomendado para |
| :--- | :--- | :--- | :--- |
| **Pantalla Completa (Full Scaled)** | `Scaled = 2` *(Por defecto)* | Ajusta las 224 lÃ­neas del SNES a las 192 de la DSi con filtrado bilineal. Nada se recorta. | Juegos de vista amplia, RPGs y plataformas generales. |
| **PÃ­xel Perfect 1:1 + HUD Squish** | `Scaled = 0`, `BG3Squish = 1` | Mantiene nitidez 100% pura y comprime Ãºnicamente la barra de vida/puntuaciÃ³n en pantalla. | *Super Mario World*, *Donkey Kong Country*. |
| **Semiescalado (Half Scaled)** | `Scaled = 1` | Punto medio con escalado sutil. | TÃ­tulos arcade y acciÃ³n rÃ¡pida. |

> Toca la **pantalla tÃ¡ctil inferior** en cualquier momento mientras juegas para cambiar el modo de escalado en vivo, gestionar *Save States* (guardar/cargar partida) o ajustar el audio.

Consulta todos los detalles tÃ©cnicos en [CONFIGURACION_PANTALLA.md](CONFIGURACION_PANTALLA.md).

---

## ðŸ† CrÃ©ditos y Agradecimientos

Este paquete recopila, repara e integra el esfuerzo de talentosos desarrolladores de la comunidad Homebrew de Nintendo DS/DSi:

* **[Archeide](https://www.gamebrew.org/wiki/SNEmulDS):** Creador original de **SNEmulDS** (1997-2007).
* **Bubble2k & Gladius:** Desarrolladores de los nÃºcleos de emulaciÃ³n de CPU 65C816 y sonido SPC700.
* **[Coto (cotodevel)](https://github.com/cotodevel/snemulds):** Creador del proyecto **SNEmulDS Revival**, portando el emulador a *ToolchainGenericDS (TGDS)* y habilitando el modo TWL a 133 MHz.
* **[Sanrax](https://github.com/Sanrax/snemulds-shim):** Creador de **`snemulds-shim`**, el chainloader que resuelve el paso de argumentos, corrige los bugs de pantalla tÃ¡ctil en DSi y automatiza el autoboot.
* **[RocketRobz](https://github.com/RocketRobz) y el equipo de [DS-Homebrew](https://github.com/DS-Homebrew/TWiLightMenu):** Creadores de **TWiLight Menu++** y **nds-bootstrap**, el entorno que hace posible la emulaciÃ³n retro moderna en Nintendo DSi y 3DS.

---

## ðŸ“„ Licencia

Este repositorio se distribuye bajo los tÃ©rminos de la licencia **GNU General Public License v2.0 (GPL-2.0)**, respetando las licencias originales de los componentes derivados. Consulta el archivo [LICENSE](LICENSE) para mÃ¡s detalles.

