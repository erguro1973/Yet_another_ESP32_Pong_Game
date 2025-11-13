# ESP32 FabGL Pong

Este es un proyecto clásico de Pong para el ESP32, utilizando la increíble librería FabGL para generar video VGA y sonido. El juego está controlado por dos potenciómetros (uno para cada jugador) y un botón para el saque.

El código está configurado para una resolución de 320x240 @ 60Hz.

![¡Añade aquí una foto o un GIF de tu juego funcionando!]

## Créditos y Agradecimientos

Este proyecto no sería posible sin el increíble trabajo de **Fabrizio Di Vittorio**. Todo el mérito de la generación de vídeo VGA, el sonido y la gestión de periféricos es de su librería [**FabGL**](http://www.fabglib.org/).

Este repositorio simplemente implementa la lógica del juego Pong sobre esa potente librería.

## Requisitos de Compilación (¡Importante!)

Este código ha sido depurado para funcionar con una combinación muy específica de librerías y versiones del core de ESP32, como se detalla en [este aviso](http://www.fabglib.org/):

* **Placa:** ESP32 (Cualquier modelo, ej: ESP32 DEVKIT V1).
* **Librería FabGL:** Versión `v1.0.9` (la última "release" oficial).
* **Paquete de Placas ESP32:** Versión `2.0.14` o `2.0.17`. **No uses v3.x.x**, ya que no es compatible con FabGL v1.0.9 y causará errores de compilación en los archivos internos de la librería (`ps2controller.cpp`, etc.).

## Conexiones (Pinout)

Este proyecto utiliza el modo VGA de 8 colores (5 pines) para simplificar el montaje.

| Componente | Pin ESP32 | Conexión |
| :--- | :--- | :--- |
| **SEÑAL VGA** | | |
| HSync | `GPIO 18` | VGA Pin 13 |
| VSync | `GPIO 5` | VGA Pin 14 |
| Rojo | `GPIO 22` | Resistencia (330Ω-470Ω) -> VGA Pin 1 |
| Verde | `GPIO 21` | Resistencia (330Ω-470Ω) -> VGA Pin 2 |
| Azul | `GPIO 19` | Resistencia (330Ω-470Ω) -> VGA Pin 3 |
| Tierra | `GND` | VGA Pines 5, 6, 7, 8, 10 |
| | | |
| **CONTROLES** | | |
| J1 (Poti) | `GPIO 34` | Pin central (Wiper). El otro a 3.3V y GND. |
| J2 (Poti) | `GPIO 35` | Pin central (Wiper). El otro a 3.3V y GND. |
| Botón Saque | `GPIO 12` | Un lado del botón. El otro a `GND`. |
| | | |
| **SONIDO** | | |
| Altavoz | `GPIO 25` | Pin positivo (+) del buzzer/altavoz. |
| Tierra | `GND` | Pin negativo (-) del buzzer/altavoz. |

## Cómo Empezar

1.  **Instala el Entorno Correcto:**
    * Abre el Arduino IDE.
    * Ve a `Herramientas > Placa > Gestor de Placas...` e instala el paquete `esp32` versión **2.0.14** (o 2.0.17).
    * Ve a `Herramientas > Gestor de Librerías...` e instala `FabGL` versión **1.0.9**.
    * Reinicia el Arduino IDE.
2.  **Conecta el Hardware:** Monta el circuito siguiendo la tabla de `Pinout` de arriba.
3.  **Compila y Sube:** Abre el archivo `ESP32_Pong.ino`, selecciona tu placa ESP32 (ej: "ESP32 Dev Module") y el puerto COM correcto.
4.  **¡A Jugar!**
