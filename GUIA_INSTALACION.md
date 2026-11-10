# Guia Paso a Paso de Instalacion

Esta guia te mostrara como instalar y dejar listo el emulador de Super Nintendo (SNES) en tu **Nintendo DSi o Nintendo DSi XL** ejecutando **TWiLight Menu++ (version v27.25.1 o superior)**.

---

## Requisitos Previos

1. Una consola **Nintendo DSi o DSi XL** con tarjeta SD (formateada en FAT32).
2. **TWiLight Menu++** instalado y funcionando en tu consola.
3. El paquete oficial descargable: [SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip](https://github.com/Luisigle97/snes-dsi-twilightmenu/releases/download/v1.0.0/SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip)

---

## Proceso de Instalacion

### Paso 1: Conectar la Tarjeta SD a la PC
* Apaga la consola, extrae la tarjeta SD e insertala en el lector de tarjetas de tu ordenador.

### Paso 2: Copiar los Archivos
* Abre el archivo ZIP descargado: `SNEmulDS-DSi-TWiLightMenu-v1.0.0.zip`.
* Arrastra o copia todo el contenido directamente a la **raiz** de tu tarjeta SD (por ejemplo `E:\`).
* Si el sistema te pregunta si deseas combinar carpetas o reemplazar archivos existentes, selecciona **Si a todo / Reemplazar**.

La estructura resultante en tu tarjeta SD debe quedar asi:
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
* Copia tus juegos de Super Nintendo con extension `.sfc` o `.smc` dentro de la carpeta:
  ```text
  sd:/snes/
  ```
  *(Nota: Tambien puedes usar `sd:/ROMS/SNES/`, pero `sd:/snes/` es la ruta estandar con compatibilidad total en todos los modos).*

> **Consejo:** Asegurate de que los nombres de los juegos no terminen con espacios raros antes del punto (por ejemplo, usa `Super Mario World.sfc` en lugar de `Super Mario World .sfc`).

### Paso 4: Ajustar la Velocidad de Reloj en TWiLight Menu++ (Recomendado)
1. Coloca la tarjeta SD en tu Nintendo DSi XL y enciendela.
2. Abre **TWiLight Menu++**.
3. Presiona `SELECT` para entrar a la **Configuracion de TWiLight Menu++**.
4. Ve a la pestana **Configuracion de Juegos/Homebrew**:
   * **Velocidad de Reloj ARM9:** Configurala en `133 MHz (TWL)`.
   * **VRAM Boost:** Configuralo en `Activado`.
5. Presiona `(B)` para guardar y salir de la configuracion.

---

## Como Jugar

1. En el explorador de archivos de TWiLight Menu++, entra en la carpeta `snes/`.
2. Veras la lista de tus juegos con su icono de cartucho de SNES.
3. Pulsa **(A)** sobre el juego que desees jugar.
4. El emulador arrancara de inmediato en modo DSi a 133 MHz, adaptando la pantalla a los 192 pixeles verticales de la consola.

---

## Preguntas Frecuentes y Atajos

* **Guardar partida en cualquier momento:** Toca la pantalla tactil inferior durante el juego y pulsa **Guardar Juego** (Save State). Para reanudarla despues, pulsa **Cargar Juego** (Load State).
* **Partidas guardadas en bateria (SRAM):** Tras guardar partida dentro del propio juego (por ejemplo en el mapa de Super Mario World o un santuario de Zelda), toca la pantalla inferior, entra en **Opciones** y confirma la escritura de SRAM antes de apagar la consola.
* **Alternar el modo de escalado:** Durante la partida, toca la pantalla inferior y pulsa en la opcion de escalado para probar entre `Scaled 2` (pantalla completa) o `Scaled 0` (pixel perfect con recorte).
