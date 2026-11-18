# Phase-beams-Extended-
Phase Beam Extended (Custom Mod Edition) - A modernized, standalone Android live wallpaper mod (org.aosp.phasebeamextended) bringing Google's classic KitKat Phase Beam graphics to SDK 33+ with refactored OpenGL ES shaders, custom RGB color themes, and high-refresh-rate optimizations. Co-developed with Claude and Gemini. # Phase Beam Extended (Custom Mod Edition)

**Phase Beam Extended** is a standalone, modernized custom mod of Google's classic **Phase Beam** live wallpaper, originally introduced in Android 4.4 (KitKat). Conceived as a direct architectural evolution from the abandoned `Holo Extended` (`.haloext`) container ecosystem and legacy RenderScript experiments (which became deprecated and removed in Android 12+), this project decouples and refactors the underlying graphics pipeline into a clean, independent, and highly customizable release optimized for modern Android environments (SDK 33+).

---

## Important Installation Note & Signature Collisions

Because this mod runs under an independent package namespace (`org.aosp.phasebeamextended`) with updated signing configurations to prevent system conflicts:
* **You must completely uninstall any original, stock, or legacy version of Phase Beam from your device before attempting to install this build.**
* Attempting to install this APK over an existing system package or legacy version will trigger a **signature collision**, resulting in an *"App not installed"* error from the package manager.

---

## Background, Evolution, and Architecture

### 1. The Pivot from Holo Extended (`.haloext`)
Early development aimed to bundle classic AOSP live wallpapers into a unified container format (`.haloext`). However, due to structural overhead, security container limitations on modern Android, and the complete deprecation of **RenderScript** in Android 12+, the project pivoted toward native, modular source-level refactoring.

### 2. OpenGL ES Shader Modernization
The core visual magic of Phase Beam relies on mathematical curves rendered directly via OpenGL ES. The original fragment and vertex shaders (`res/glsl/04.glsl`, `Tg.glsl`, `Zu.glsl`) were audited, rewritten, and adapted to compile cleanly under modern GLSL compilers, ensuring full compatibility with hardware acceleration flags on contemporary high-refresh-rate displays (90Hz, 120Hz, and up).

### 3. Clean Separation
Maintained as a standalone repository (`PhaseBeam-Extended`), this project allows for independent feature expansion, custom color palette injection, and asset modification without altering historical source archives or AOSP system trees.

---

## Key Features

* **Custom Color Themes & RGB Picker:** Expands far beyond the static stock blue palette, introducing dynamic RGB configuration options and user presets.
* **Optimized GLSL Pipeline:** Refactored OpenGL ES execution blocks for stutter-free frame rendering and lower battery overhead.
* **Standalone Namespace:** Built under `org.aosp.phasebeamextended` so it coexists cleanly alongside other user packages without system collision.
* **Modern Android Target:** Fully compatible with Android 13/14+ security standards, Edge-to-Edge display padding, and modern window manager parameters.

---

## Repository Directory Structure

```text
PhaseBeam-Extended/
├── app/
│   ├── build.gradle
│   └── src/
│       └── main/
│           ├── AndroidManifest.xml
│           ├── java/
│           │   └── org/aosp/phasebeamextended/
│           │       ├── PhaseBeamWallpaper.java
│           │       └── PhaseBeamRenderer.java
│           ├── res/
│           │   ├── glsl/                 # Refactored vertex & fragment shaders
│           │   │   ├── 04.glsl
│           │   │   ├── Tg.glsl
│           │   │   └── Zu.glsl
│           │   ├── drawable/             # Picker thumbnails, icons, and vector assets
│           │   └── values/               # Themes, colors, and configuration strings
│           └── assets/                   # Extension configuration and default palettes
├── .gitignore
├── LICENSE
└── README.md

