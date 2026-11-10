# 📖 Guía Paso a Paso de Instalación

Esta guía te mostrará cómo instalar y dejar listo el emulador de Super Nintendo (SNES) en tu **Nintendo DSi o Nintendo DSi XL** ejecutando **TWiLight Menu++ (versión v27.25.1 o superior)**.

---

## 📋 Requisitos Previos

1. Una consola **Nintendo DSi o DSi XL** con tarjeta SD (formateada en FAT32).
2. **TWiLight Menu++** instalado y funcionando en tu consola.
3. El archivo descargable [`release/SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip`](release/SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip).

---

## 🛠️ Proceso de Instalación

### Paso 1: Conectar la Tarjeta SD a la PC
* Apaga la consola, extrae la tarjeta SD e insértala en el lector de tarjetas de tu ordenador.

### Paso 2: Copiar los Archivos
* Abre el archivo ZIP descargado: `SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip`.
* Arrastra o copia todo el contenido directamente a la **raíz** de tu tarjeta SD (por ejemplo `E:\`).
* Si Windows te pregunta si deseas combinar carpetas o reemplazar archivos existentes, selecciona **Sí a todo / Reemplazar**.

La estructura resultante en tu SD debe verse así:
```text
sd:/
├── _nds/
│   └── TWiLightMenu/
│       ├── addons/Virtual Console
│       ├── emulators/
│       │   ├── snemulds-shim.nds
│       │   ├── snemulds-shim.ini
│       │   ├── SNEmulDS.srl
│       │   ├── SNEmulDS.nds
│       │   ├── SNEmulDS_0.6a.nds
│       │   ├── SNEmulDS-legacy.nds
│       │   ├── SNEmulDS-legacy-twlm-path.nds
│       │   └── snemul.cfg
│       └── extras/
│           ├── config.sfc.ini
│           └── config.smc.ini
├── snes/
│   └── snemul.cfg
└── snemul.cfg
```

### Paso 3: Agregar tus Juegos (ROMs)
* Copia tus juegos de Super Nintendo con extensión `.sfc` o `.smc` dentro de la carpeta:
  ```text
  sd:/snes/
  ```
  *(Nota: También puedes usar `sd:/ROMS/SNES/`, pero `sd:/snes/` es la ruta estándar con compatibilidad total en todos los modos).*

> [!TIP]
> Asegúrate de que los nombres de los juegos no terminen con espacios raros antes del punto (por ejemplo, usa `Super Mario World.sfc` en lugar de `Super Mario World .sfc`).

### Paso 4: Ajustar la Velocidad de Reloj en TWiLight Menu++ (Opcional pero Recomendado)
1. Coloca la tarjeta SD en tu Nintendo DSi XL y enciéndela.
2. Abre **TWiLight Menu++**.
3. Presiona `SELECT` para entrar a la **Configuración de TWiLight Menu++**.
4. Ve a la pestaña **Configuración de Juegos/Homebrew**:
   * **Velocidad de Reloj ARM9:** Configúrala en `133 MHz (TWL)`.
   * **VRAM Boost:** Configúralo en `Activado`.
5. Presiona `(B)` para guardar y salir de la configuración.

---

## 🎮 Cómo Jugar

1. En el explorador de archivos de TWiLight Menu++, entra en la carpeta `snes/`.
2. Verás la lista de tus juegos con su icono de cartucho de SNES.
3. Pulsa **(A)** sobre el juego que desees jugar.
4. El emulador arrancará de inmediato en modo DSi a 133 MHz, adaptando la pantalla a los 192 píxeles verticales de la consola.

---

## ❓ Preguntas Frecuentes y Solución de Problemas

#### 1. ¿Cómo guardo mi partida en cualquier momento?
* Toca la **pantalla táctil inferior** durante el juego.
* Pulsa en **Guardar Juego** (Save State). Para reanudarla después, entra a **Cargar Juego** (Load State).

#### 2. En los juegos con guardado nativo en batería (ej. Zelda o Super Mario World), ¿cómo se guarda?
* Tras guardar partida en el menú del propio juego, toca la pantalla inferior, entra en **Opciones** y verifica que la opción de escribir la SRAM esté activa antes de apagar la consola.

#### 3. ¿Cómo cambio el modo de pantalla si quiero ver los gráficos con píxel 1:1?
* Durante la partida, toca la pantalla táctil inferior y pulsa en la opción de escalado para alternar entre:
  * `Scaled 2`: Pantalla completa sin bordes cortados.
  * `Scaled 0`: Píxeles 1:1 perfectos con compresión de la barra de vida/HUD.
  * `Scaled 1`: Modo semiescalado intermedio.
