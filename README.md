# CleanTheOcean 🌊

Proyecto de realidad virtual desarrollado en Unity para concientizar sobre la contaminación oceánica. El jugador puede limpiar el océano usando gestos de manos detectados por visión por computadora.

## Requisitos previos

Antes de compilar el proyecto, asegurate de tener instalado:

- **Unity Hub** (descargalo de https://unity.com/download)
- **Unity 2022.3.x LTS** (o la versión que uses, se instala desde Unity Hub)
- **Python 3.10 o superior** (para el sistema de detección de gestos)
- **Visual Studio 2022** con el workload de desarrollo de juegos con Unity (opcional, pero recomendado)

## Cómo abrir el proyecto en Unity

1. Abrí **Unity Hub**
2. Hacé clic en **"Open"** o **"Add"**
3. Navegá hasta la carpeta `Proyecto` dentro de este repositorio
4. Seleccioná esa carpeta y esperá a que Unity importe todos los assets (puede tardar unos minutos la primera vez)

## Estructura del proyecto

```
CleanTheOcean/
├── Proyecto/                 # Proyecto de Unity
│   ├── Assets/              # Assets del juego (escenas, scripts, modelos, etc.)
│   ├── Packages/            # Paquetes de Unity
│   └── ProjectSettings/     # Configuración del proyecto
├── hand_tracker.py          # Sistema de detección de gestos con la cámara
├── phone_server.py          # Servidor para control desde el celular
├── config.py                # Configuración general
└── requirements.txt         # Dependencias de Python
```

## Cómo compilar el juego

1. Abrí el proyecto en Unity (como se explicó arriba)
2. Andá a **File → Build Settings**
3. Asegurate de que la plataforma sea **PC, Mac & Linux Standalone**
4. Hacé clic en **"Add Open Scenes"** si no hay escenas en la lista
5. Hacé clic en **"Build"** o **"Build and Run"**
6. Elegí una carpeta donde guardar el ejecutable

## Sistema de control por gestos (opcional)

El proyecto incluye un sistema de detección de gestos con la cámara web. Para usarlo:

1. Abrí una terminal en la carpeta del proyecto
2. Instalá las dependencias de Python:
   ```
   pip install -r requirements.txt
   ```
3. Ejecutá el detector de gestos:
   ```
   python hand_tracker.py
   ```
   O simplemente hacé doble clic en `run_gesture_detection.bat`

## Escenas principales

- **CleanOceanVR.unity** - Escena principal del juego VR
- **Demo.unity** - Escena de demostración

Las escenas están en: `Proyecto/Assets/Ventuar/UnderwaterPack/Scenes/`

## Notas

- La primera vez que abrís el proyecto, Unity tiene que importar todos los assets, así que puede tardar un rato
- Si te aparece algún error de paquetes, andá a **Window → Package Manager** y dejá que se actualicen
- El proyecto usa **Photon** para funcionalidades de red (ya está configurado)

## Problemas comunes

**Unity no encuentra los scripts:**
Cerrá Unity, borrá la carpeta `Library` dentro de `Proyecto/` y volvé a abrir. Unity va a reimportar todo.

**Error de versión de Unity:**
Instalá la versión exacta que pide o una compatible desde Unity Hub.

---

Desarrollado para el curso de Interacción Humano-Computador
