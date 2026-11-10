# 🖥️ Guía de Escalado de Pantalla y Menú Táctil

Esta guía explica en detalle cómo funciona el renderizado gráfico de Super Nintendo en las pantallas de la Nintendo DSi y DSi XL, y cómo personalizar la experiencia visual a tu gusto.

---

## 📐 La Diferencia de Resoluciones

| Consola | Resolución Nativa | Relación de Aspecto |
| :--- | :--- | :--- |
| **Super Nintendo (SNES)** | $256 \times 224$ (NTSC) / $256 \times 239$ (PAL) | 4:3 en televisores CRT (8:7 interno) |
| **Nintendo DSi / DSi XL** | $256 \times 192$ | 4:3 nativo en cada pantalla |

Observa un dato fundamental: **El ancho es idéntico (256 píxeles)**. Por lo tanto, en horizontal no se pierde ni un solo píxel de nitidez. La única diferencia radica en la altura: la pantalla de la DSi tiene **32 líneas verticales menos** que el SNES ($224 - 192 = 32$).

---

## 🎨 Los Modos de Escalado Disponibles

En [snemul.cfg](file:///E:/snemul.cfg) o desde el menú táctil dentro del juego puedes elegir entre tres modos:

### 1. Modo Pantalla Completa (`Scaled = 2`) — *Modo Recomendado por Defecto*
* **Cómo funciona:** El emulador comprime las 224 líneas a 192 usando un filtro bilineal por hardware.
* **Ventajas:**
  * Ves el 100% de la pantalla del juego.
  * No se corta ningún marcador, vida, texto ni barra superior/inferior.
  * Llena por completo la pantalla de la DSi XL.
* **Ideal para:** RPGs con mucho texto (*Chrono Trigger*, *Final Fantasy*), juegos de carreras (*Top Gear*) o títulos con interfaces complejas.

### 2. Modo Píxel Perfect 1:1 con Compresión Inteligente de HUD (`Scaled = 0`)
* **Cómo funciona:** La imagen del juego se dibuja sin ningún tipo de compresión ni escalado (1 píxel de SNES = 1 píxel de DSi). Es la máxima nitidez posible.
* **El truco de `BG3Squish`:** Para evitar que la barra de vida o el marcador de monedas quede fuera de la pantalla:
  * `BG3Squish = 1`: Comprime la capa de texto y marcadores (Capa 3) en 16 píxeles hacia abajo.
  * `BG3Squish = 2`: La comprime 32 píxeles.
  * `YScroll = 16`: Centra la vista del juego verticalmente recortando 16 píxeles en el cielo y 16 en el suelo (zonas que en las televisiones de tubo antiguas solían quedar tapadas por el borde plástico de la TV).
* **Ideal para:** Plataformas de acción pura como *Super Mario World*, *Donkey Kong Country*, *Castlevania IV* y *Super Metroid*.

### 3. Modo Semiescalado (`Scaled = 1`)
* **Cómo funciona:** Aplica una compresión vertical muy suave, recortando solo una pequeña franja de 8 píxeles en los extremos.

---

## 📱 Cómo Personalizar el Escalado en Vivo (Menú Táctil)

No necesitas editar archivos para cambiar de modo:
1. Durante una partida, **toca la pantalla inferior (táctil)** con el stylus o el dedo.
2. Aparecerá el menú de control táctil de SNEmulDS.
3. Presiona el botón de **Escalado (Scaling)** para alternar entre `Scaled 0`, `Scaled 1` y `Scaled 2`.
4. Observa el cambio al instante en la pantalla superior y déjalo en el que te resulte más cómodo para ese juego en particular.

---

## 🎯 Perfiles Recomendados por Juego

En este paquete ya dejamos configurados en `snemul.cfg` los siguientes perfiles óptimos para los juegos más populares:

* **Super Mario World:**
  `SpeedHacks = 1 | Transparency = 0 | Scaled = 2 | BG3Squish = 1 | YScroll = 24`
* **Donkey Kong Country 1, 2 y 3:**
  `SpeedHacks = 0 | BGPriorities = 3 | Scaled = 2 | Vblank = 1`
* **Chrono Trigger:**
  `Scaled = 2 | Vblank = 1 | Sound = 1`
* **The Legend of Zelda: A Link to the Past:**
  `Scaled = 2 | Transparency = 0 | YScroll = 16`
* **Super Metroid:**
  `Scaled = 2 | SpeedHacks = 1 | Vblank = 1`
