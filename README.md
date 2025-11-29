# CleanTheOcean 🌊🐟

Juego multijugador cooperativo/competitivo desarrollado en Unity donde dos jugadores compiten en tiempo real: uno limpia el océano mientras el otro lo contamina.

## Sobre el juego

CleanTheOcean es un juego **multijugador para 2 jugadores** que usa **Photon PUN** para la conexión en red:

- **Jugador 1 - Limpiador:** Controla un personaje en 3D usando gestos de manos (detectados con cámara web) o desde el celular. Su objetivo es limpiar la basura del océano.
- **Jugador 2 - Contaminador:** Tiene una vista estratégica 2D desde arriba y puede tirar basura al océano para dificultar la tarea del limpiador.

Las partidas duran 2 minutos y medio. Gana el jugador que cumpla mejor su objetivo.

## Requisitos previos

Para abrir y compilar el proyecto necesitás:

- **Unity Hub** (descargalo de https://unity.com/download)
- **Unity 2021.3.45f1** (instalalo desde Unity Hub, es importante usar esta versión exacta)
- **Python 3.10 o superior** (solo si vas a usar el control por gestos)
- **Conexión a internet** (para el multijugador con Photon)

## Cómo abrir el proyecto

1. Abrí **Unity Hub**
2. Hacé clic en **"Open"** o **"Add"**
3. Navegá hasta la carpeta `Proyecto` dentro de este repositorio
4. Si te pide instalar la versión **2021.3.45f1**, instalala desde Unity Hub
5. Esperá a que Unity importe todos los assets (la primera vez tarda unos minutos)

## Estructura del proyecto

```
CleanTheOcean/
├── Proyecto/                              # Proyecto de Unity
│   ├── Assets/
│   │   ├── ScriptsConexion/              # Scripts del juego (networking, movimiento, etc.)
│   │   │   ├── Launcher.cs               # Conexión a Photon y asignación de roles
│   │   │   ├── GameMatchManager.cs       # Lógica de la partida, timer, puntuación
│   │   │   ├── Movement.cs               # Control del jugador
│   │   │   ├── TrashSpawner.cs           # Sistema de spawn de basura
│   │   │   └── HandReceiver.cs           # Recibe datos de gestos desde Python
│   │   ├── Ventuar/UnderwaterPack/
│   │   │   └── Scenes/
│   │   │       ├── Demo.unity            # ⭐ ESCENA PRINCIPAL DEL JUEGO
│   │   │       └── MainMenu.unity        # Menú inicial
│   │   ├── Photon/                       # Plugin de Photon PUN (networking)
│   │   └── Audio/                        # Efectos de sonido y música
│   ├── Packages/
│   └── ProjectSettings/
├── hand_tracker.py                        # Detección de gestos con MediaPipe
├── phone_server.py                        # Servidor para control desde celular
├── phone_controller.html                  # Interfaz web para el celular
├── config.py                              # Configuración del sistema de gestos
├── requirements.txt                       # Dependencias de Python
└── run_gesture_detection.bat              # Script para iniciar detección de gestos
```

## Cómo compilar y ejecutar

1. Abrí el proyecto en Unity (como se explicó arriba)
2. Abrí la escena principal: **Assets → Ventuar → UnderwaterPack → Scenes → Demo.unity**
3. Para probar, dale **Play** en el editor (necesitás 2 instancias para el multijugador)
4. Para compilar:
   - Andá a **File → Build Settings**
   - Asegurate de que **Demo** esté en la lista de escenas (si no está, hacé clic en "Add Open Scenes")
   - Plataforma: **PC, Mac & Linux Standalone**
   - Hacé clic en **Build** y elegí donde guardar el ejecutable

## Cómo jugar

### Inicio de partida
1. Ejecutá el juego en dos computadoras (o dos instancias)
2. El primer jugador que entre será el **Limpiador**
3. El segundo jugador será el **Contaminador**
4. Cuando los dos estén conectados, presioná **2** para iniciar la partida

### Controles del Limpiador (Jugador 1)
- Usa los gestos de la mano frente a la cámara para mover el personaje
- También podés usar el celular como control (abrí `phone_controller.html` en el navegador del celular)

### Controles del Contaminador (Jugador 2)
- Vista desde arriba del océano
- Click para tirar basura y contaminar

## Sistema de control por gestos

El Jugador 1 puede usar gestos de manos detectados con la cámara web:

1. Abrí una terminal en la carpeta del proyecto
2. Instalá las dependencias:
   ```
   pip install -r requirements.txt
   ```
3. Ejecutá el detector:
   ```
   python hand_tracker.py
   ```
   O hacé doble clic en `run_gesture_detection.bat`

4. Asegurate de que el juego esté corriendo antes de iniciar el detector

## Tecnologías usadas

- **Unity 2021.3.45f1** - Motor del juego
- **Photon PUN 2** - Multijugador en tiempo real
- **Python + MediaPipe** - Detección de gestos con visión por computadora
- **OpenCV** - Captura y procesamiento de video

## Notas importantes

- La primera vez que abrís el proyecto, Unity importa todo y puede tardar varios minutos
- Si aparecen errores de paquetes, andá a **Window → Package Manager** y actualizalos
- Para probar el multijugador en una sola PC, podés compilar el juego y correr una instancia compilada + otra en el editor

## Problemas comunes

**"Script not found" o errores de compilación:**
Cerrá Unity, borrá la carpeta `Library` dentro de `Proyecto/` y volvé a abrir.

**No conecta al multijugador:**
Verificá tu conexión a internet. Photon necesita conectarse a sus servidores.

**Los gestos no funcionan:**
Asegurate de que la cámara esté funcionando y que Python tenga las librerías instaladas.

---

Desarrollado para el curso de Interacción Humano-Computador
