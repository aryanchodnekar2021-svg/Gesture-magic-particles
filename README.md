# Gesture-magic-particles
Construction and Deconstruction of 3D heart using Three.js and HTML,CSS and JS
# 🪄 Gesture Magic Particles

An interactive generative art experiment that turns your webcam into a motion controller for a 3D particle system. Built with **Three.js** for WebGL rendering and **MediaPipe** for real-time hand tracking.

## 🌟 Features

* **Real-time Hand Tracking:** Uses MediaPipe Hands to detect palm position and finger distance with low latency.
* **Custom GLSL Shaders:** 8,000 particles are animated directly on the GPU using custom vertex and fragment shaders for high performance.
* **Shape Morphing:** Smoothly transitions between a **3D Heart** and a **Galaxy/Saturn Ring** based on hand shape.
* **Physics Interactions:**
    * **Expand/Shrink:** Particles scale based on how wide your hand is open.
    * **Fireworks:** Detects rapid hand-opening velocity to trigger a particle explosion effect.
* **Glassmorphism UI:** Modern, translucent UI overlay for instructions.

## 🎮 How to Play

1.  **Allow Camera Access** when prompted (all processing is done locally on your device; no video is sent to the cloud).
2.  Stand back slightly so your hand is clearly visible.
3.  **Perform the gestures:**

| Gesture | Action | Effect |
| :--- | :--- | :--- |
| **Open Hand** ✋ | **Expand & Morph** | Particles transform into a Galaxy/Ring shape and spread out. |
| **Closed Fist** ✊ | **Shrink & Morph** | Particles condense into a pulsing Heart shape. |
| **Hand Flick** 💥 | **Explosion** | Quickly flick your hand from closed to open to trigger a firework burst. |
| **Move Hand** 👋 | **Position** | The particle cloud follows your hand across the screen. |

## 🛠️ Tech Stack

* **[Three.js](https://threejs.org/):** 3D Rendering engine.
* **[MediaPipe Hands](https://developers.google.com/mediapipe):** Machine Learning for computer vision.
* **GLSL (OpenGL Shading Language):** For raw GPU particle calculations.
* **HTML5/CSS3:** For the glassmorphism overlay and structure.

## 🚀 Getting Started

Since this project is contained within a single file for portability, setup is instant.

### Option 1: Direct Run
1.  Download the `index.html` file.
2.  Open it in any modern web browser (Chrome, Edge, Firefox).
3.  *Note:* Some browsers block webcam access for local files (`file://`). If the camera doesn't start, use Option 2.

### Option 2: Local Server (Recommended)
To avoid browser security restrictions on the webcam:

1.  Clone the repo:
    ```bash
    git clone [https://github.com/your-username/gesture-magic-particles.git](https://github.com/your-username/gesture-magic-particles.git)
    cd gesture-magic-particles
    ```
2.  Install a simple http server (if you have Node.js):
    ```bash
    npx http-server
    ```
3.  Open the localhost URL provided in your terminal (usually `http://127.0.0.1:8080`).

## 🧠 Code Highlights

The core magic happens in the **Vertex Shader**. Instead of updating 8,000 particle positions in JavaScript (CPU), we use math to calculate the shapes directly on the Graphics Card (GPU).

```glsl
// Example from the code: Morphing logic
vec3 finalPos = mix(posHeart, posSaturn, uMorph);
