# 🤖 Laboratorio 2 — Robot Pepper

Este laboratorio documenta el proceso de creación de una **coreografía sencilla** para el robot **Pepper**, utilizando la herramienta **Choregraphe** y un **script en Python** ejecutado directamente en el robot mediante **SSH**. Incluye la explicación de las librerías utilizadas, los pasos de conexión y el despliegue en GitHub.

-----

## 📌 Objetivos
- Diseñar una coreografía básica en **Choregraphe**.  
- Conectarse a Pepper por **SSH** y crear un script en **Python** con `nano`.  
- Ejecutar la coreografía desde la terminal con los servicios de Pepper.  
- Documentar las librerías y servicios utilizados.  
- Subir el trabajo al repositorio de GitHub en la carpeta `Laboratorio 2`.

-----

## 🛠️ Requisitos previos
- Robot **Pepper** y computador en la **misma red Wi-Fi**.  
- Dirección IP del robot (ejemplo: `192.168.1.100`).  
- Usuario por defecto: `nao` ; contraseña: `nao`.  
- Instalación de **Choregraphe Suite** (versión `2.5.10.7`).  
- Acceso a la terminal con `ssh` y `scp`.  
- Python 2.7 en el robot.  

-----

## 🎭 Coreografía en Choregraphe
1. Abrir **Choregraphe** y crear un proyecto nuevo.  
2. Arrastrar las cajas necesarias:  
   - **Say** → Para mensajes hablados.  
   - **Animation Player** → Para movimientos predefinidos.  
   - **Python Script** → (opcional) para control avanzado.  
3. Conectar las cajas en secuencia (ejemplo: *Say* → *Animación* → *Say*).  
4. Probar en el simulador de Choregraphe y ajustar tiempos.  
5. Conectar a Pepper (`Connection → Connect to...`) e introducir su IP.  
6. Subir la coreografía al robot con **Upload and Run**.  

-----

## 💻 Trabajo en Python mediante SSH

Además de la herramienta gráfica, se trabajó directamente en la **terminal de Pepper** con **Python**, lo que permitió mayor control sobre sus acciones.

### 🔑 Acceso al robot
Se utilizó el comando `ssh` para conectarse a Pepper desde un computador en la misma red. Una vez autenticado, el usuario accede al sistema operativo interno del robot.  

### 📂 Creación del script
Dentro de la sesión, se creó un archivo Python con el editor `nano`. Este archivo contiene la lógica de la coreografía que el robot debe ejecutar. Guardar el archivo en la carpeta del usuario `nao` permite tener un acceso rápido y mantener la organización.

### ⚙️ Lógica general del script
El script Python se organizó en varias etapas:  
1. **Conexión al robot** → mediante la librería `qi`, que establece comunicación con los servicios internos de Pepper.  
2. **Acceso a servicios principales** → se invocaron servicios como `ALMotion` (para movimientos), `ALTextToSpeech` (para voz), `ALRobotPosture` (para posturas), `ALLeds` (para las luces), entre otros.  
3. **Activación de motores** → antes de ejecutar cualquier movimiento, es necesario activar la “rigidez” de las articulaciones, lo que despierta los motores para que puedan recibir órdenes.  
4. **Ejecución de acciones** → se programó una secuencia donde Pepper habla, se mueve, cambia de postura y enciende sus LEDs faciales en distintos colores.  
5. **Sincronización con pausas** → con la librería `time` se incluyeron pequeñas esperas para que los gestos, luces y voz se ejecuten de forma coordinada y natural.  
6. **Finalización y liberación de motores** → tras completar la coreografía, se redujo la rigidez de los motores, devolviendo al robot a un estado de reposo seguro.

### ▶️ Ejecución del script
Una vez guardado el archivo, se otorgaron permisos de ejecución y se lanzó el script desde la terminal.  
Durante la ejecución, el robot realizó en orden:  
- Una presentación hablada.  
- Un gesto animado de saludo.  
- Un cambio de postura utilizando el servicio de posturas predefinidas.  
- Una animación adicional de brazos.  
- Un cierre con mensaje de despedida y LEDs en blanco.  

De esta forma se comprobó el correcto funcionamiento del flujo completo.

-----

## 📚 Librerías y servicios utilizados
- **qi** → Conexión a servicios de Pepper (NAOqi).  
- **argparse** → Lectura de argumentos desde terminal.  
- **sys** → Manejo de errores y salida del programa.  
- **os** → Interacción con archivos y rutas.  
- **almath** → Cálculos geométricos en 3D (propia de SoftBank).  
- **math** → Funciones matemáticas estándar.  
- **motion (ALMotion)** → Control de motores y articulaciones.  
- **httplib** → Comunicación HTTP.  
- **json** → Lectura y escritura de datos en JSON.  
- **ALRobotPosture** → Posturas predefinidas.  
- **ALAnimatedSpeech** → Voz sincronizada con gestos.  
- **ALAnimationPlayer** → Animaciones preprogramadas.  
- **ALLeds** → Control de LEDs faciales.  
- **time** → Pausas y sincronización.  

-----

## ✅ Checklist para GitHub

- mkdir -p Laboratorio2/screenshots
- cp coreografia_pepper.py Laboratorio2/
- cd Laboratorio2
- git init
- git add .
- git commit -m "Laboratorio 2 - Coreografía con Pepper"
- git remote add origin https ://github.com/USUARIO/REPO.git
- git push -u origin main

-----

## 🎥 Link de YouTube de las Coreografias Hechas

https://youtu.be/zr-gXhziTD4
