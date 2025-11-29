# CleanTheOcean 🌊🐟

Juego multijugador cooperativo/competitivo desarrollado en Unity donde dos jugadores compiten en tiempo real: uno limpia el océano mientras el otro lo contamina.

## Sobre el juego

CleanTheOcean es un juego **multijugador para 2 jugadores** que usa **Photon PUN** para la conexión en red:

- **Jugador 1 - Limpiador:** Controla un personaje en 3D usando gestos de manos (detectados con cámara web) o desde el celular. Su objetivo es limpiar la basura del océano.
- **Jugador 2 - Contaminador:** Tiene una vista estratégica 2D desde arriba y puede tirar basura al océano para dificultar la tarea del limpiador.

Las partidas duran 2 minutos y medio. Gana el jugador que cumpla mejor su objetivo.

## Ejecutar el juego (forma rápida)

Si solo querés probar el juego sin compilar nada, descargá el ejecutable ya compilado:

**[Descargar Build (Windows)](https://drive.google.com/drive/folders/1zdD15tEtEQ0hM9qYYMpAW-BjHxWqsFDG?usp=sharing)**

Solo descomprime el `.zip` y ejecutá `Proyecto.exe`. Necesitás dos computadoras o ejecutá dos veces el `Proyecto.exe` para probar el juego.

## Requisitos previos para compilar

Si quieres abrir el proyecto en Unity y compilarlo ttu mismo:

- **Unity Hub** - descargalo de https://unity.com/download
- **Unity 2021.3.45f1** - instalalo desde Unity Hub, es importante usar esta versión exacta
- **Python 3.10 o superior** - solo si vas a usar el control por gestos
- **Conexión a internet** - para el multijugador con Photon

## Cómo abrir el proyecto en Unity

1. Abrí **Unity Hub**
2. Hacé clic en **"Open"** o **"Add"**
3. Navegá hasta la carpeta `Proyecto` dentro de este repositorio
4. Si te pide instalar la versión **2021.3.45f1**, instalala desde Unity Hub
5. Esperá a que Unity importe todos los assets 

## Estructura del proyecto

```
CleanTheOcean/
├── Build/                                 # Ejecutable compilado (Windows)
│   └── Proyecto.exe                       # Ejecutar este archivo para jugar
├── Proyecto/                              # Proyecto de Unity
│   ├── Assets/
│   │   ├── ScriptsConexion/              # Scripts principales del juego
│   │   │   ├── Launcher.cs               # Conexión a Photon y asignación de roles
│   │   │   ├── GameMatchManager.cs       # Lógica de partida, timer y puntuación
│   │   │   ├── Movement.cs               # Control del jugador
│   │   │   ├── TrashSpawner.cs           # Sistema de basura
│   │   │   ├── PhoneButtonReceiver.cs    # Recibe comandos del celular
│   │   │   └── UDPMultiplayerAdapter.cs  # Comunicación UDP con Python
│   │   ├── Ventuar/UnderwaterPack/Scenes/
│   │   │   ├── Demo.unity                # ESCENA PRINCIPAL DEL JUEGO
│   │   │   └── MainMenu.unity            # Menú inicial
│   │   └── Photon/                       # Plugin de red (Photon PUN 2)
│   ├── Packages/
│   └── ProjectSettings/
├── movimiento.py                          # Detección de gestos con la cámara
├── phone_server.py                        # Servidor para control desde celular
├── phone_controller.html                  # Interfaz del celular (con giroscopio)
├── phone_buttons_controller.html          # Interfaz del celular (solo botones)
├── config.py                              # Configuración de la cámara y gestos
├── requirements.txt                       # Dependencias de Python
└── run_gesture_detection.bat              
```

## Cómo compilar el juego

1. Abrí el proyecto en Unity
2. Abrí la escena: **Assets → Ventuar → UnderwaterPack → Scenes → Demo.unity**
3. Andá a **File → Build Settings**
4. Asegurate de que **Demo** esté en la lista de escenas
5. Plataforma: **PC, Mac & Linux Standalone**
6. Hacé clic en **Build** y elige donde guardar

## Cómo jugar

### Inicio de partida

1. Ejecutá el juego en dos computadoras (o dos instancias en la misma PC)
2. El primero que entre será el **Limpiador**
3. El segundo será el **Contaminador**
4. Cuando los dos estén conectados, presioná **2** para iniciar

### Controles del Limpiador (Jugador 1)

Podés usar gestos con la cámara o el celular:

**Gestos con cámara:**
- Mano derecha arriba → Rotar derecha
- Mano izquierda arriba → Rotar izquierda
- Ambas manos arriba → Avanzar
- Manos juntas → Retroceder
- Puño cerrado → Agarrar basura
- Pulgar arriba → Iluminar basura cercana

**Con celular:**
- Botones en pantalla para iluminar la basura y comer la basura.

### Controles del Contaminador (Jugador 2)

- Vista desde arriba del océano
- Click en el agua para tirar basura

## Sistema de control por gestos

Para usar los gestos con la cámara web:

1. Abrí una terminal en la carpeta del proyecto
2. Instalá las dependencias:
   ```
   pip install -r requirements.txt
   ```
3. Ejecutá el detector:
   ```
   python movimiento.py
   ```
El juego tiene que estar corriendo antes de iniciar el detector.

## Control desde el celular

1. Ejecutá el servidor:
   ```
   python phone_server.py
   ```
2. Te va a mostrar una URL tipo `http://192.168.x.x:8080`
3. Abrí esa URL en el navegador del celular (tiene que estar en la misma red WiFi)
4. Opciones:
   - `/` → Control con giroscopio + botones


## Tecnologías usadas

- **Unity 2021.3.45f1** - Motor del juego
- **Photon PUN 2** - Multijugador en tiempo real
- **Python + MediaPipe** - Detección de gestos con visión por computadora
- **OpenCV** - Captura de video
- **WebSockets/UDP** - Comunicación entre Python y Unity


