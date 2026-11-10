# SNEmulDS DSi TWL Bundle para TWiLight Menu++

[![Plataforma](https://img.shields.io/badge/Plataforma-Nintendo%20DSi%20%7C%20DSi%20XL-e60012.svg)](https://es.wikipedia.org/wiki/Nintendo_DSi)
[![Compatibilidad](https://img.shields.io/badge/TWiLight%20Menu%2B%2B-v27.25.1%2B-blue.svg)](https://github.com/DS-Homebrew/TWiLightMenu)
[![Licencia](https://img.shields.io/badge/Licencia-GPL--2.0-green.svg)](LICENSE)
[![Release](https://img.shields.io/badge/Release-v1.0.0-orange.svg)](https://github.com/Luisigle97/snes-dsi-twilightmenu/releases/tag/v1.0.0)

Paquete optimizado y actualizado de **SNEmulDS (Modo TWL DSi a 133 MHz)** con integracion nativa directa para **TWiLight Menu++**.

Este proyecto soluciona todos los problemas historicos de arranque, congelamiento de pantalla tactil, listas de ROMs vacias y errores de escalado visual al emular Super Nintendo en consolas Nintendo DSi y DSi XL.

---

## Caracteristicas y Mejoras Aplicadas

1. **Rendimiento Nativo DSi (TWL Mode a 133 MHz):**
   * Emplea el binario legitimo `SNEmulDS.srl` con identificador DSi (`UnitCode = 0x02`), duplicando la velocidad del procesador de 67 MHz a 133 MHz y accediendo a los 16 MB de memoria RAM completa de la consola (evitando el modo legado de DS Lite de 4 MB).
2. **Arranque Directo sin Menus Intermedios (`autoboot = true`):**
   * Integracion mediante el puente `snemulds-shim` (desarrollado por Sanrax). Al seleccionar cualquier juego `.sfc` o `.smc` en TWiLight Menu++, arranca directamente la partida sin quedarse trabado en la pantalla de *"Seleccionar ROM"*.
3. **Parcheo Dinamico en Memoria RAM:**
   * Corrige el fallo critico del ejecutable DSi oficial donde la pantalla tactil dejaba de responder.
   * Restaura y desmutea los canales de audio por hardware de la DSi en la transicion de arranque.
4. **Escalado de Pantalla Optimizado:**
   * Configurado globalmente en `Scaled = 2` (pantalla completa adaptada a los 192 pixeles verticales de la DSi) con filtrado bilineal para evitar deformaciones bruscas.
   * Compatibilidad con recorte 1:1 pixel-perfect y compresion de HUD (`BG3Squish`) para juegos como *Super Mario World*, *Donkey Kong Country*, *Chrono Trigger* y *The Legend of Zelda*.
5. **Menu Tactil en Espanol:**
   * Menu inferior configurado en Espanol (`Language = 5`), con diseno centrado y accesible al tocar la pantalla tactil.

---

## Estructura del Repositorio

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
â”‚   â”‚       â”‚   â”œâ”€â”€ SNEmulDS_0.6a.nds  (Clasico 2007)
â”‚   â”‚       â”‚   â””â”€â”€ snemul.cfg
â”‚   â”‚       â””â”€â”€ extras/
â”‚   â”‚           â”œâ”€â”€ config.sfc.ini     (Lanzador directo)
â”‚   â”‚           â””â”€â”€ config.smc.ini     (Lanzador directo)
â”‚   â”œâ”€â”€ snes/                          <-- Carpeta donde van tus juegos .smc / .sfc
â”‚   â”‚   â””â”€â”€ snemul.cfg
â”‚   â””â”€â”€ snemul.cfg                     <-- Configuracion global con perfiles optimizados
â”œâ”€â”€ release/
â”‚   â””â”€â”€ SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip  <-- Paquete comprimido listo para descargar
â”œâ”€â”€ GUIA_INSTALACION.md          <-- Guia paso a paso para usuarios
â”œâ”€â”€ CONFIGURACION_PANTALLA.md    <-- Manual tecnico de escalado y pantalla tactil
â”œâ”€â”€ CREDITS.md                   <-- Atribuciones y licencias originales
â””â”€â”€ README.md
```

---

## Instalacion Rapida

1. Descarga el paquete oficial: [SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip](https://github.com/Luisigle97/snes-dsi-twilightmenu/releases/download/v1.0.0/SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip)
2. Descomprime su contenido en la raiz de la tarjeta SD de tu Nintendo DSi / DSi XL (combinando las carpetas `_nds` y `snes`).
3. Coloca tus juegos de Super Nintendo (`.sfc` o `.smc`) dentro de la carpeta `sd:/snes/`.
4. Enciende tu Nintendo DSi XL, entra a **TWiLight Menu++**, selecciona tu juego y presiona **(A)**.

Para instrucciones detalladas paso a paso, consulta la [Guia de Instalacion](GUIA_INSTALACION.md).

---

## Modos de Pantalla y Escalado

| Modo | Ajuste en `snemul.cfg` | Comportamiento | Recomendado para |
| :--- | :--- | :--- | :--- |
| **Pantalla Completa (Full Scaled)** | `Scaled = 2` *(Por defecto)* | Ajusta las 224 lineas de SNES a las 192 de DSi con filtrado bilineal. Nada se recorta. | Vista completa, RPGs y plataformas generales. |
| **Pixel Perfect 1:1 + HUD Squish** | `Scaled = 0`, `BG3Squish = 1` | Mantiene nitidez 100% pura y comprime unicamente la barra de vida/puntuacion en pantalla. | *Super Mario World*, *Donkey Kong Country*. |
| **Semiescalado (Half Scaled)** | `Scaled = 1` | Punto medio con escalado vertical sutil. | Titulos arcade y accion rapida. |

> Toca la **pantalla tactil inferior** en cualquier momento mientras juegas para cambiar el modo de escalado en vivo, gestionar *Save States* (guardar/cargar partida) o ajustar el audio.

Consulta los detalles tecnicos en [CONFIGURACION_PANTALLA.md](CONFIGURACION_PANTALLA.md).

---

## Creditos y Agradecimientos

Este paquete recopila, repara e integra el esfuerzo de talentosos desarrolladores de la comunidad Homebrew de Nintendo DS/DSi:

* **[Archeide](https://www.gamebrew.org/wiki/SNEmulDS):** Creador original de **SNEmulDS** (1997-2007).
* **Bubble2k & Gladius:** Desarrolladores de los nucleos de emulacion de CPU 65C816 y sonido SPC700.
* **[Coto (cotodevel)](https://github.com/cotodevel/snemulds):** Creador del proyecto **SNEmulDS Revival**, portando el emulador a *ToolchainGenericDS (TGDS)* y habilitando el modo TWL a 133 MHz.
* **[Sanrax](https://github.com/Sanrax/snemulds-shim):** Creador de **`snemulds-shim`**, el chainloader que resuelve el paso de argumentos, corrige los bugs de pantalla tactil en DSi y automatiza el autoboot.
* **[RocketRobz](https://github.com/RocketRobz) y el equipo de [DS-Homebrew](https://github.com/DS-Homebrew/TWiLightMenu):** Creadores de **TWiLight Menu++** y **nds-bootstrap**, el entorno que hace posible la emulacion retro moderna en Nintendo DSi y 3DS.

---

## Licencia

Este repositorio se distribuye bajo los terminos de la licencia **GNU General Public License v2.0 (GPL-2.0)**, respetando las licencias originales de los componentes derivados. Consulta el archivo [LICENSE](LICENSE) para mas detalles.

