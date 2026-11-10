# Guia de Escalado de Pantalla y Menu Tactil

[Español](CONFIGURACION_PANTALLA.md) | [English](SCREEN_CONFIG.md)

Esta guia explica en detalle como funciona el renderizado grafico de Super Nintendo en las pantallas de la Nintendo DSi y DSi XL, y como personalizar la experiencia visual a tu gusto.

---

## La Diferencia de Resoluciones

| Consola | Resolucion Nativa | Relacion de Aspecto |
| :--- | :--- | :--- |
| **Super Nintendo (SNES)** | 256 x 224 (NTSC) / 256 x 239 (PAL) | 4:3 en televisores CRT (8:7 interno) |
| **Nintendo DSi / DSi XL** | 256 x 192 | 4:3 nativo en cada pantalla |

Observa un dato fundamental: **El ancho es identico (256 pixeles)**. Por lo tanto, en horizontal no se pierde ni un solo pixel de nitidez. La unica diferencia radica en la altura: la pantalla de la DSi tiene **32 lineas verticales menos** que el SNES (224 - 192 = 32).

---

## Los Modos de Escalado Disponibles

En `snemul.cfg` o desde el menu tactil dentro del juego puedes elegir entre tres modos:

### 1. Modo Pantalla Completa (`Scaled = 2`) - *Modo Recomendado por Defecto*
* **Como funciona:** El emulador comprime las 224 lineas a 192 usando un filtro bilineal por hardware.
* **Ventajas:**
  * Ves el 100% de la pantalla del juego.
  * No se corta ningun marcador, vida, texto ni barra superior/inferior.
  * Llena por completo la pantalla de la DSi XL.
* **Ideal para:** RPGs con mucho texto (*Chrono Trigger*, *Final Fantasy*), juegos de carreras (*Top Gear*) o titulos con interfaces complejas.

### 2. Modo Pixel Perfect 1:1 con Compresion Inteligente de HUD (`Scaled = 0`)
* **Como funciona:** La imagen del juego se dibuja sin ningun tipo de compresion ni escalado (1 pixel de SNES = 1 pixel de DSi). Es la maxima nitidez posible.
* **El truco de `BG3Squish` y `YScroll = 16`:**
  * `BG3Squish = 1`: Comprime la capa de texto y marcadores (Capa 3) en 16 pixeles hacia abajo.
  * `BG3Squish = 2`: La comprime 32 pixeles.
  * `YScroll = 16`: Centra la vista del juego verticalmente recortando 16 pixeles exactos en el cielo y 16 en el suelo (eliminando temblores, jitter o artefactos de entrelazado).
* **Ideal para:** Plataformas de accion pura como *Super Mario World*, *Donkey Kong Country*, *Castlevania IV* y *Super Metroid*.

### 3. Modo Semiescalado (`Scaled = 1`)
* **Como funciona:** Aplica una compresion vertical muy suave, recortando solo una pequena franja de 8 pixeles en los extremos.

---

## Como Personalizar el Escalado en Vivo (Menu Tactil)

No necesitas editar archivos para cambiar de modo:
1. Durante una partida, **toca la pantalla inferior (tactil)** con el stylus o el dedo.
2. Aparecera el menu de control tactil modernizado de SNEmulDS.
3. Presiona el boton de **Escalado (Scaling)** para alternar entre `Scaled 0`, `Scaled 1` y `Scaled 2`.
4. Observa el cambio al instante en la pantalla superior y dejalo en el que te resulte mas comodo para ese juego en particular.

---

## Perfiles Recomendados por Juego

En este paquete ya dejamos configurados en `snemul.cfg` los siguientes perfiles optimos para los juegos mas populares:

* **Super Mario World:**
  `SpeedHacks = 1 | Transparency = 0 | Scaled = 2 | BG3Squish = 0 | YScroll = 16`
* **Donkey Kong Country 1, 2 y 3:**
  `SpeedHacks = 0 | BGPriorities = 3 | Scaled = 2 | Vblank = 1 | YScroll = 16`
* **Chrono Trigger:**
  `Scaled = 2 | Vblank = 1 | Sound = 1 | YScroll = 16`
* **The Legend of Zelda: A Link to the Past:**
  `Scaled = 2 | Transparency = 0 | YScroll = 16`
* **Super Metroid:**
  `Scaled = 2 | SpeedHacks = 1 | Vblank = 1 | YScroll = 16`
* **Top Gear 1 y 2 / Top Racer:**
  `BGLayers = 10101 | Transparency = 0 | Vblank = 1 | SpeedHacks = 0 | Scaled = 2 | YScroll = 16`
  *(Nota: Desactivar la capa BG2 elimina la corrupcion de la pista y division de pantalla).*
* **The Mask (La Mascara):**
  `Transparency = 0 | BGPriorities = 1 | Vblank = 1 | SpeedHacks = 1 | Scaled = 2 | YScroll = 16`
  *(Nota: Desactivar transparencias evita la desaparicion de sprites y personajes).*
