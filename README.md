# 🎮 SNEmulDS DSi TWL Bundle para TWiLight Menu++

[![Plataforma](https://img.shields.io/badge/Plataforma-Nintendo%20DSi%20%7C%20DSi%20XL-e60012.svg)](https://es.wikipedia.org/wiki/Nintendo_DSi)
[![Compatibilidad](https://img.shields.io/badge/TWiLight%20Menu%2B%2B-v27.25.1%2B-blue.svg)](https://github.com/DS-Homebrew/TWiLightMenu)
[![Licencia](https://img.shields.io/badge/Licencia-GPL--2.0-green.svg)](LICENSE)
[![Release](https://img.shields.io/badge/Release-v1.0.0-orange.svg)](release/SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip)

Paquete optimizado y actualizado de **SNEmulDS (Modo TWL DSi a 133 MHz)** con integración nativa directa para **TWiLight Menu++**.

Este proyecto soluciona todos los problemas históricos de arranque, congelamiento de pantalla táctil, listas de ROMs vacías y errores de escalado visual al emular Super Nintendo en consolas Nintendo DSi y DSi XL.

---

## 🌟 Características y Mejoras Aplicadas

1. **Rendimiento Nativo DSi (TWL Mode a 133 MHz):**
   * Emplea el binario legítimo `SNEmulDS.srl` con identificador DSi (`UnitCode = 0x02`), duplicando la velocidad del procesador de 67 MHz a 133 MHz y accediendo a los 16 MB de memoria RAM completa de la consola (evitando el modo legado de DS Lite de 4 MB).
2. **Arranque Directo sin Menús Intermedios (`autoboot = true`):**
   * Integración mediante el puente `snemulds-shim` (por Sanrax). Al seleccionar cualquier juego `.sfc` o `.smc` en TWiLight Menu++, arranca directamente la partida sin quedarse trabado en la pantalla de *"Seleccionar ROM"*.
3. **Parcheo en Memoria RAM Dinámico:**
   * Corrige el fallo crítico del ejecutable DSi oficial donde la pantalla táctil dejaba de responder.
   * Restaura y desmutea los canales de audio por hardware de la DSi en la transición de arranque.
4. **Escalado de Pantalla Optimizado:**
   * Configurado globalmente en `Scaled = 2` (pantalla completa adaptada a los 192 píxeles verticales de la DSi) con filtrado bilineal para evitar deformaciones bruscas.
   * Compatibilidad con recorte 1:1 pixel-perfect y compresión de HUD (`BG3Squish`) para juegos como *Super Mario World*, *Donkey Kong Country*, *Chrono Trigger* y *The Legend of Zelda*.
5. **Menú Táctil Modernizado en Español:**
   * Menú inferior configurado en Español (`Language = 5`), con diseño centrado y accesible al tocar la pantalla táctil.

---

## 📦 Estructura del Repositorio

```text
snes-dsi-twilightmenu/
├── sd_card_package/             <-- Archivos listos para copiar a tu tarjeta SD
│   ├── _nds/
│   │   └── TWiLightMenu/
│   │       ├── addons/Virtual Console
│   │       ├── emulators/
│   │       │   ├── snemulds-shim.nds
│   │       │   ├── snemulds-shim.ini
│   │       │   ├── SNEmulDS.srl       (TWL 133 MHz)
│   │       │   ├── SNEmulDS.nds       (NTR Fallback)
│   │       │   ├── SNEmulDS_0.6a.nds  (Clásico 2007)
│   │       │   └── snemul.cfg
│   │       └── extras/
│   │           ├── config.sfc.ini     (Lanzador directo)
│   │           └── config.smc.ini     (Lanzador directo)
│   ├── snes/                          <-- Carpeta donde van tus juegos .smc / .sfc
│   │   └── snemul.cfg
│   └── snemul.cfg                     <-- Configuración global con perfiles optimizados
├── release/
│   └── SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip  <-- Paquete comprimido listo para descargar
├── GUIA_INSTALACION.md          <-- Guía paso a paso para usuarios
├── CONFIGURACION_PANTALLA.md    <-- Manual técnico de escalado y pantalla táctil
├── CREDITS.md                   <-- Atribuciones y licencias originales
└── README.md
```

---

## 🚀 Instalación Rápida

1. Descarga el archivo comprimido desde la carpeta [`release/SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip`](release/SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip).
2. Descomprime su contenido en la raíz de la tarjeta SD de tu Nintendo DSi / DSi XL (combinando las carpetas `_nds` y `snes`).
3. Coloca tus juegos de Super Nintendo (`.sfc` o `.smc`) dentro de la carpeta `sd:/snes/`.
4. Enciende tu Nintendo DSi XL, entra a **TWiLight Menu++**, selecciona tu juego y ¡listo!

Para una guía más detallada con resolución de dudas, consulta la [Guía de Instalación Completa](GUIA_INSTALACION.md).

---

## 🎮 Opciones de Escalado y Menú Táctil

| Modo | Ajuste en `snemul.cfg` | Comportamiento | Recomendado para |
| :--- | :--- | :--- | :--- |
| **Pantalla Completa (Full Scaled)** | `Scaled = 2` *(Por defecto)* | Ajusta las 224 líneas del SNES a las 192 de la DSi con filtrado bilineal. Nada se recorta. | Juegos de vista amplia, RPGs y plataformas generales. |
| **Píxel Perfect 1:1 + HUD Squish** | `Scaled = 0`, `BG3Squish = 1` | Mantiene nitidez 100% pura y comprime únicamente la barra de vida/puntuación en pantalla. | *Super Mario World*, *Donkey Kong Country*. |
| **Semiescalado (Half Scaled)** | `Scaled = 1` | Punto medio con escalado sutil. | Títulos arcade y acción rápida. |

> Toca la **pantalla táctil inferior** en cualquier momento mientras juegas para cambiar el modo de escalado en vivo, gestionar *Save States* (guardar/cargar partida) o ajustar el audio.

Consulta todos los detalles técnicos en [CONFIGURACION_PANTALLA.md](CONFIGURACION_PANTALLA.md).

---

## 🏆 Créditos y Agradecimientos

Este paquete recopila, repara e integra el esfuerzo de talentosos desarrolladores de la comunidad Homebrew de Nintendo DS/DSi:

* **[Archeide](https://www.gamebrew.org/wiki/SNEmulDS):** Creador original de **SNEmulDS** (1997-2007).
* **Bubble2k & Gladius:** Desarrolladores de los núcleos de emulación de CPU 65C816 y sonido SPC700.
* **[Coto (cotodevel)](https://github.com/cotodevel/snemulds):** Creador del proyecto **SNEmulDS Revival**, portando el emulador a *ToolchainGenericDS (TGDS)* y habilitando el modo TWL a 133 MHz.
* **[Sanrax](https://github.com/Sanrax/snemulds-shim):** Creador de **`snemulds-shim`**, el chainloader que resuelve el paso de argumentos, corrige los bugs de pantalla táctil en DSi y automatiza el autoboot.
* **[RocketRobz](https://github.com/RocketRobz) y el equipo de [DS-Homebrew](https://github.com/DS-Homebrew/TWiLightMenu):** Creadores de **TWiLight Menu++** y **nds-bootstrap**, el entorno que hace posible la emulación retro moderna en Nintendo DSi y 3DS.

---

## 📄 Licencia

Este repositorio se distribuye bajo los términos de la licencia **GNU General Public License v2.0 (GPL-2.0)**, respetando las licencias originales de los componentes derivados. Consulta el archivo [LICENSE](LICENSE) para más detalles.
