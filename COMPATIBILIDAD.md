# Guia de Compatibilidad y Solucion de Juegos en SNEmulDS

[Español](COMPATIBILIDAD.md) | [English](COMPATIBILITY.md)

Esta guia detalla el nivel de compatibilidad de los juegos de Super Nintendo (SNES) ejecutados mediante **SNEmulDS** en consolas **Nintendo DSi y DSi XL** bajo **TWiLight Menu++**, junto con las configuraciones exactas para resolver fallos en juegos populares.

---

## Indice
1. [Como Solucionar Juegos Problematicos (Top Gear y La Mascara)](#como-solucionar-juegos-problematicos)
   - [Top Gear 1 y 2 (y Top Racer)](#1-top-gear-1-y-2--top-racer)
   - [La Mascara (The Mask)](#2-la-mascara-the-mask)
2. [Lista Maestra de Compatibilidad](#lista-maestra-de-compatibilidad)
   - [Tier 1: Compatibles al 100% (60 FPS / Perfectos)](#tier-1-compatibles-al-100-60-fps--perfectos)
   - [Tier 2: Jugables con Ajustes Menores](#tier-2-jugables-con-ajustes-menores)
   - [Tier 3: Juegos No Compatibles (Chips Especiales)](#tier-3-juegos-no-compatibles-chips-especiales)
3. [Base de Datos Oficial de la Comunidad](#base-de-datos-oficial-de-la-comunidad)

---

## Como Solucionar Juegos Problematicos

### 1. Top Gear 1 y 2 / Top Racer

#### El Problema
Al arrancar una carrera, la pista de asfalto aparece partida por la mitad, parpadea con artefactos grises o negros, o la pantalla dividida tapa la visualizacion del horizonte.

#### La Causa Tecnica
*Top Gear* utiliza interrupciones por linea de barrido (*raster line interrupts* o HDMA) en la **Capa 2 (BG2)** de la SNES para simular la perspectiva en curva de la carretera. La Nintendo DS posee un motor 2D con un numero finito de capas que no puede procesar dicha rasterizacion simultanea en hardware, generando basura visual sobre la pista.

#### La Solucion
Desactivar la capa **BG2** y sincronizar por hardware **VBlank**:
* **Ajuste automatico:** Ya esta pre-configurado en nuestro archivo `snemul.cfg`:
  ```ini
  [TOP GEAR]
  BGLayers = 10101
  Transparency = 0
  Vblank = 1
  SpeedHacks = 0
  Scaled = 2
  YScroll = 16
  Sound = 1
  ```
  *(El valor `BGLayers = 10101` mantiene activas BG1, BG3, BG4 y Sprites, apagando unicamente BG2).*
* **Como configurarlo en vivo desde la consola:**
  1. Abre el juego y toca la pantalla tactil para abrir el menu de SNEmulDS.
  2. Pulsa en **Avanzado** (o **Opciones** -> **Capas**).
  3. Desmarca la casilla **BG2** (Capa 2).
  4. Desactiva **Transparencias** (`Transparency: OFF`).
  5. Asegurate de tener **Vblank** activado (`Vblank: 1`).
  6. ¡La carretera se vera perfectamente limpia y el juego correra a 60 FPS estables!

> [!NOTE]
> **¿Que ocurre con Top Gear 3000?**
> *Top Gear 3000* no funciona en SNEmulDS porque no es un juego estandar: contiene en su cartucho el chip matematico coprocesador **DSP-4**. SNEmulDS no tiene soporte para la serie de chips DSP-4 (ver seccion de chips especiales).

---

### 2. La Mascara (The Mask)

#### El Problema
Durante el juego, el personaje de La Mascara (Jim Carrey) y varios enemigos parpadean, se vuelven invisibles o se dibujan por detras de los escenarios, haciendolo injugable.

#### La Causa Tecnica
*The Mask* utiliza un sistema avanzado de mezcla de transparencias y prioridades por celda (*tile priorities*) para crear efectos de sombras y dibujos animados. En el hardware de la DS, el motor de mezcla interpreta incorrectamente el canal alfa del sprite del protagonista y lo descarta o lo envia al fondo de la pila de capas.

#### La Solucion
Desactivar el canal de transparencias conflictivo y forzar las prioridades de fondo:
* **Ajuste automatico:** Pre-configurado en nuestro archivo `snemul.cfg`:
  ```ini
  [THE MASK]
  Transparency = 0
  BGPriorities = 1
  Vblank = 1
  SpeedHacks = 1
  Scaled = 2
  YScroll = 16
  Sound = 1
  ```
* **Como configurarlo en vivo desde la consola:**
  1. Durante la partida, toca la pantalla inferior para invocar el menu de SNEmulDS.
  2. Dirigete a **Opciones** -> **Graficos / Configuracion**.
  3. Cambia **Transparencias** a **OFF** (`Transparency = 0`).
  4. Activa **Prioridades BG** (`BGPriorities = 1`).
  5. Guarda los ajustes para este juego. El personaje y los enemigos se mantendran solidos y siempre al frente.

---

## Lista Maestra de Compatibilidad

### Tier 1: Compatibles al 100% (60 FPS / Perfectos)

Estos juegos funcionan a velocidad real completa (60 fotogramas por segundo), con sonido impecable a 32 kHz y sin fallos criticos de emulacion:

| Titulo | Genero | Configuracion Recomendada |
| :--- | :--- | :--- |
| **Super Mario World** | Plataformas | `SpeedHacks = 1`, `Scaled = 2`, `YScroll = 16` |
| **Donkey Kong Country 1, 2 y 3** | Plataformas | `BGPriorities = 3`, `Vblank = 1`, `Scaled = 2` |
| **The Legend of Zelda: A Link to the Past** | Accion / RPG | `Transparency = 0`, `Scaled = 2`, `YScroll = 16` |
| **Chrono Trigger** | JRPG | `Vblank = 1`, `Sound = 1`, `Scaled = 2` |
| **Final Fantasy IV, V y VI** | JRPG | `Scaled = 2`, `Vblank = 1`, `Sound = 1` |
| **Super Metroid** | Aventura | `SpeedHacks = 1`, `Vblank = 1`, `Scaled = 2` |
| **Super Castlevania IV** | Accion | `Vblank = 1`, `Scaled = 2`, `YScroll = 16` |
| **TMNT IV: Turtles in Time** | Beat 'em up | `SpeedHacks = 1`, `Scaled = 2` |
| **F-Zero** | Carreras Modo 7 | `Scaled = 2`, `Vblank = 1` |
| **Secret of Mana** | Accion / RPG | `Vblank = 1`, `Scaled = 2` |
| **Aladdin (Capcom)** | Plataformas | `Vblank = 1`, `Scaled = 2` |
| **The Lion King** | Plataformas | `Vblank = 1`, `Scaled = 2` |
| **Goof Troop** | Puzzle / Aventura | `Vblank = 1`, `Scaled = 2` |
| **Mega Man X (X1)** | Accion | `SpeedHacks = 1`, `Vblank = 1`, `Scaled = 2` |
| **Zombies Ate My Neighbors** | Accion | `Vblank = 1`, `Scaled = 2` |
| **Sunset Riders** | Run & Gun | `Vblank = 1`, `Scaled = 2` |
| **Super Bomberman 1 al 5** | Arcade / Fiesta | `Vblank = 1`, `Scaled = 2` |
| **Contra III: The Alien Wars** | Accion / Shooter | `Transparency = 0`, `Vblank = 1`, `Scaled = 2` |
| **Top Gear 1 y 2 / Top Racer** | Carreras | `BGLayers = 10101`, `Transparency = 0`, `Vblank = 1` |
| **The Mask (La Mascara)** | Accion / Plataformas | `Transparency = 0`, `BGPriorities = 1`, `Vblank = 1` |
| **Super Mario All-Stars** | Plataformas | `Scaled = 2`, `Vblank = 1` |
| **Super Punch-Out!!** | Deportes / Boxeo | `SpeedHacks = 1`, `Scaled = 2` |
| **Demon's Crest** | Accion | `Vblank = 1`, `Scaled = 2` |
| **Wild Guns** | Shooter Arcade | `Vblank = 1`, `Scaled = 2` |
| **NBA Jam / Tournament Edition** | Deportes | `Vblank = 1`, `Scaled = 2` |
| **Earthworm Jim 1 y 2** | Accion | `Vblank = 1`, `Scaled = 2` |

---

### Tier 2: Jugables con Ajustes Menores

Juegos que se pueden completar de principio a fin, pero que presentan pequenas inconsistencias visuales en fondos o transparencias secundarias:

* **Super Mario Kart:** El efecto de pista Modo 7 funciona y es perfectamente jugable; algunas texturas lejanas presentan un ligero temblor. Requiere `Vblank = 1` y `Scaled = 2`.
* **EarthBound:** Totalmente jugable y disfrutable; los efectos de distorsion psicodelica de fondo en las batallas se renderizan de forma simplificada por limitaciones de las matrices de la DS.
* **Killer Instinct:** Jugable a buen ritmo activando `SpeedHacks = 1`.
* **Mortal Kombat II y 3:** Muy fluidos; en ciertos escenarios se recomienda `Transparency = 0` para una representacion perfecta de los luchadores.
* **Super Street Fighter II:** Buena tasa de cuadros por segundo; algunos escenarios muestran pequenas lineas en las sombras de los personajes.
* **Breath of Fire I y II:** Jugable al 100% de inicio a fin.
* **ActRaiser 1 y 2:** Jugables con rendimiento notable.

---

### Tier 3: Juegos No Compatibles (Chips Especiales)

A diferencia de consolas como la Game Boy Advance o la Nintendo 3DS, la Nintendo DS (y DSi) ejecuta SNEmulDS mediante un emulador hiper-optimizado en ensamblador ARM para la CPU central de SNES (65816) y el procesador de sonido (SPC700).

En la epoca de los 16 bits, muchos cartuchos integraban **chips coprocesadores de silicio adicionales dentro del propio cartucho**. SNEmulDS **no emula dichos microprocesadores secundarios**, por lo que los siguientes titulos no arrancan o muestran pantalla en negro:

| Chip Especial | Titulos Afectados | Explicacion Tecnica |
| :--- | :--- | :--- |
| **SuperFX / SuperFX 2** | *Star Fox*, *Super Mario World 2: Yoshi's Island*, *Doom*, *Stunt Race FX*, *Vortex*, *Dirt Trax FX* | Procesador matematico RISC secundario a 21 MHz para calculo 3D y escalado poligonal de poligonos planos. |
| **SA-1 (Super Accelerator)** | *Super Mario RPG*, *Kirby Super Star*, *Kirby's Dream Land 3*, *Dragon Ball Z: Hyper Dimension* | CPU secundaria 65C816 a 10.74 MHz con mapeador de memoria DMA rapido. |
| **DSP-3 / DSP-4** | ***Top Gear 3000***, *SD Gundam GX* | Coprocesador matematico para el trazado de trayectorias y calculos vectoriales en pista. *(Por esta razon Top Gear 1 y 2 funcionan perfecto pero Top Gear 3000 no).* |
| **S-DD1** | *Street Fighter Alpha 2*, *Star Ocean* | Chip de descompresion grafica de datos comprimidos en memoria ROM al vuelo. |
| **Cx4** | *Mega Man X2*, *Mega Man X3* | Chip matematico de rotacion y renderizado de wireframe vectorial (animaciones de jefes). |
| **OBC1** | *Metal Combat: Falcon's Revenge* | Procesador de sprites para la pistola Super Scope. |

---

## Base de Datos Oficial de la Comunidad

La comunidad de homebrew ha mantenido durante mas de una decada la lista oficial y detallada de compatibilidad de cada juego probado en hardware real de Nintendo DS y DSi:

* **[Wiki Oficial de Compatibilidad de SNEmulDS en GBAtemp](https://wiki.gbatemp.net/wiki/SNEmulDS_Compatibility_List)**

En esa wiki puedes buscar cualquier titulo por su nombre en orden alfabetico para verificar de antemano que combinacion exacta de capas o hacks requiere si llegara a presentar algun detalle grafico.
