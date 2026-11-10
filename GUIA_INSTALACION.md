# ðŸ“– GuÃ­a Paso a Paso de InstalaciÃ³n

Esta guÃ­a te mostrarÃ¡ cÃ³mo instalar y dejar listo el emulador de Super Nintendo (SNES) en tu **Nintendo DSi o Nintendo DSi XL** ejecutando **TWiLight Menu++ (versiÃ³n v27.25.1 o superior)**.

---

## ðŸ“‹ Requisitos Previos

1. Una consola **Nintendo DSi o DSi XL** con tarjeta SD (formateada en FAT32).
2. **TWiLight Menu++** instalado y funcionando en tu consola.
3. El archivo descargable [[SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip](https://github.com/Luisigle97/snes-dsi-twilightmenu/releases/download/v1.0.0/SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip)](release/SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip).

---

## ðŸ› ï¸ Proceso de InstalaciÃ³n

### Paso 1: Conectar la Tarjeta SD a la PC
* Apaga la consola, extrae la tarjeta SD e insÃ©rtala en el lector de tarjetas de tu ordenador.

### Paso 2: Copiar los Archivos
* Abre el archivo ZIP descargado: `SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip`.
* Arrastra o copia todo el contenido directamente a la **raÃ­z** de tu tarjeta SD (por ejemplo `E:\`).
* Si Windows te pregunta si deseas combinar carpetas o reemplazar archivos existentes, selecciona **SÃ­ a todo / Reemplazar**.

La estructura resultante en tu SD debe verse asÃ­:
```text
sd:/
â”œâ”€â”€ _nds/
â”‚   â””â”€â”€ TWiLightMenu/
â”‚       â”œâ”€â”€ addons/Virtual Console
â”‚       â”œâ”€â”€ emulators/
â”‚       â”‚   â”œâ”€â”€ snemulds-shim.nds
â”‚       â”‚   â”œâ”€â”€ snemulds-shim.ini
â”‚       â”‚   â”œâ”€â”€ SNEmulDS.srl
â”‚       â”‚   â”œâ”€â”€ SNEmulDS.nds
â”‚       â”‚   â”œâ”€â”€ SNEmulDS_0.6a.nds
â”‚       â”‚   â”œâ”€â”€ SNEmulDS-legacy.nds
â”‚       â”‚   â”œâ”€â”€ SNEmulDS-legacy-twlm-path.nds
â”‚       â”‚   â””â”€â”€ snemul.cfg
â”‚       â””â”€â”€ extras/
â”‚           â”œâ”€â”€ config.sfc.ini
â”‚           â””â”€â”€ config.smc.ini
â”œâ”€â”€ snes/
â”‚   â””â”€â”€ snemul.cfg
â””â”€â”€ snemul.cfg
```

### Paso 3: Agregar tus Juegos (ROMs)
* Copia tus juegos de Super Nintendo con extensiÃ³n `.sfc` o `.smc` dentro de la carpeta:
  ```text
  sd:/snes/
  ```
  *(Nota: TambiÃ©n puedes usar `sd:/ROMS/SNES/`, pero `sd:/snes/` es la ruta estÃ¡ndar con compatibilidad total en todos los modos).*

> [!TIP]
> AsegÃºrate de que los nombres de los juegos no terminen con espacios raros antes del punto (por ejemplo, usa `Super Mario World.sfc` en lugar de `Super Mario World .sfc`).

### Paso 4: Ajustar la Velocidad de Reloj en TWiLight Menu++ (Opcional pero Recomendado)
1. Coloca la tarjeta SD en tu Nintendo DSi XL y enciÃ©ndela.
2. Abre **TWiLight Menu++**.
3. Presiona `SELECT` para entrar a la **ConfiguraciÃ³n de TWiLight Menu++**.
4. Ve a la pestaÃ±a **ConfiguraciÃ³n de Juegos/Homebrew**:
   * **Velocidad de Reloj ARM9:** ConfigÃºrala en `133 MHz (TWL)`.
   * **VRAM Boost:** ConfigÃºralo en `Activado`.
5. Presiona `(B)` para guardar y salir de la configuraciÃ³n.

---

## ðŸŽ® CÃ³mo Jugar

1. En el explorador de archivos de TWiLight Menu++, entra en la carpeta `snes/`.
2. VerÃ¡s la lista de tus juegos con su icono de cartucho de SNES.
3. Pulsa **(A)** sobre el juego que desees jugar.
4. El emulador arrancarÃ¡ de inmediato en modo DSi a 133 MHz, adaptando la pantalla a los 192 pÃ­xeles verticales de la consola.

---

## â“ Preguntas Frecuentes y SoluciÃ³n de Problemas

#### 1. Â¿CÃ³mo guardo mi partida en cualquier momento?
* Toca la **pantalla tÃ¡ctil inferior** durante el juego.
* Pulsa en **Guardar Juego** (Save State). Para reanudarla despuÃ©s, entra a **Cargar Juego** (Load State).

#### 2. En los juegos con guardado nativo en baterÃ­a (ej. Zelda o Super Mario World), Â¿cÃ³mo se guarda?
* Tras guardar partida en el menÃº del propio juego, toca la pantalla inferior, entra en **Opciones** y verifica que la opciÃ³n de escribir la SRAM estÃ© activa antes de apagar la consola.

#### 3. Â¿CÃ³mo cambio el modo de pantalla si quiero ver los grÃ¡ficos con pÃ­xel 1:1?
* Durante la partida, toca la pantalla tÃ¡ctil inferior y pulsa en la opciÃ³n de escalado para alternar entre:
  * `Scaled 2`: Pantalla completa sin bordes cortados.
  * `Scaled 0`: PÃ­xeles 1:1 perfectos con compresiÃ³n de la barra de vida/HUD.
  * `Scaled 1`: Modo semiescalado intermedio.

