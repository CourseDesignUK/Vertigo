# 🏗️ WAH-VAS // Work at Height Vertigo & Acrophobia Assessment Simulator

**WAH-VAS (Work at Height Vertigo & Acrophobia Simulator)** is a zero-dependency, WebXR and 3D WebGL occupational safety and vestibular assessment simulator. It is designed to evaluate postural stability, head-sway tremor, and visual target acquisition across progressive industrial elevations up to **60 meters**.

Built with **A-Frame (Three.js)**, **Tailwind CSS**, and a **Synthesized Web Audio API** engine, it runs out-of-the-box on both standard desktop browsers (Instructor/2D Mode) and standalone VR headsets such as Meta Quest 2/3/Pro (Immersive WebXR Mode).

---

## ✨ Key Features

* **Dual-Mode Interface (Desktop + VR):**
  * **2D Instructor HUD:** A dark glassmorphism overlay providing real-time biometric/vestibular telemetry, stage controls, environmental stressor toggles, and clinical report generation.
  * **3D In-World Spatial Console:** Mounted directly inside the ascending elevator cabin so VR headset users can operate lift stages, toggle stressors, and monitor telemetry using VR laser controllers or gaze interaction.
* **100% Procedural Textures & Geometry (Zero External Assets):**
  * Custom HTML5 `<canvas>` procedural textures generate transparent industrial open-steel floor grating, high-visibility hazard chevrons, ground tactical grids, and timber/grip-tape cantilever planks at runtime.
  * Includes a 65-meter steel lattice tower, intermediate outrigger gantries, shipping containers, a mid-rise warehouse, trees, and an emergency response ambulance with flashing lightbars at ground level to maximize vertical depth parallax.
* **60Hz Postural Sway & Head Stability Telemetry:**
  * Continuously tracks positional displacement ($\text{mm/s}$) and angular head rotation ($\text{deg/s}$) at $60\text{ Hz}$ to calculate an instantaneous and stage-averaged **Head Sway Index**, alongside downward head pitch angle ($\theta_{\text{pitch}}$).
* **Synthesized Web Audio Engine:**
  * Real-time procedural white-noise wind generator routed through a dynamically modulated bandpass filter whose frequency and gain scale with altitude, paired with synthesized UI lock and verification tones.
* **Clinical & Occupational Assessment Reporting:**
  * Generates an interactive end-of-session qualification summary table grading each tier (`PASS / STABLE`, `INCOMPLETE SCAN`, or `NOT EVALUATED`) with one-click **JSON Telemetry Export**.

---

## 📋 Progressive Assessment Protocol (5 Stages)

Candidates ascend an open-grating industrial lift and must look over the platform edge to lock their gaze or VR controller laser onto orange/cyan inspection beacons for **2.0 seconds** per marker:

| Stage | Altitude | Environment Tier | Visual Targets | Primary Assessment Objective |
| :--- | :--- | :--- | :---: | :--- |
| **Stage 0** | `0.0 m` | Ground Baseline Calibration | `0A`, `0B` | Establish baseline postural sway and calibrate gaze-lock mechanics at ground level. |
| **Stage 1** | `5.0 m` | Low-Level Scaffolding | `1A`, `1B` | Evaluate initial vestibular response during low-elevation perimeter look-down tasks. |
| **Stage 2** | `15.0 m` | Mid-Tower Open Grating | `2A`, `2B`, `2C` | Test visual focus through see-through steel grating and lateral drop zones. |
| **Stage 3** | `30.0 m` | High-Level Gantry | `3A`, `3B`, `3C` | Assess high-altitude target acquisition above adjacent warehouse rooflines. |
| **Stage 4** | `60.0 m` | Peak Cantilever Plank | `4A`, `4B`, `4C` | Peak acrophobia exposure: step out onto a narrow $0.48\text{ m}$ unguarded beam over a $60\text{ m}$ drop. |

---

## 🌪️ Environmental Stressors

Instructors or candidates can dynamically increase task difficulty using three real-time environmental stressors:
1. **🌬️ Wind Audio (`OFF` / `ACTIVE`):** Activates procedural high-altitude wind gusts that increase in pitch and volume as the lift ascends.
2. **📳 Platform Sway (`OFF` / `ACTIVE`):** Introduces multi-axis sinusoidal mechanical resonance and structural sway to the elevator cabin proportional to altitude.
3. **🚧 Guardrails (`GUARDED` / `UNGUARDED`):** Toggles the $1.1\text{ m}$ OSHA-standard perimeter safety rails around the elevator deck for unguarded edge exposure.

---

## 🎮 Controls & Interaction

### 🖥️ Desktop Browser (Instructor / 2D Mode)
* **Look Around:** Click and drag with the **Mouse**.
* **Move on Platform:** **W, A, S, D** or **Arrow Keys**.
* **Verify Targets:** Center the blue/amber screen reticle over any active stage marker (`0A`–`4C`) and hold for **2.0 seconds**.
* **Quick Positioning:** Use the **"Step Out to Edge / Plank"** and **"Center Rig"** buttons on the bottom console to quickly move between the cabin center and the cantilevered plank.

### 🥽 VR Headset (Meta Quest / WebXR Mode)
1. Click the **"VR"** button in the bottom-right corner of the viewport to enter immersive WebXR mode.
2. **Physical Locomotion:** Walk naturally within your physical guardian boundary to step toward the grating edge or out onto the cantilever plank.
3. **Target Scanning:** Gaze directly at markers using the head-tracked reticle or point with Left/Right VR controller laser pointers.
4. **In-World Console:** Point and click on the 3D Spatial Telemetry Panel inside the cabin to switch altitudes or toggle guardrails without removing your headset.

---

## 🚀 Quick Start & Deployment

Because the simulator is self-contained inside a single `index.html` file with zero external 3D models or audio files required, deployment is instantaneous.

### 1. Run Locally
Clone the repository and serve the folder over any local HTTP server:

```bash
git clone https://github.com/your-username/wah-vas-vr-simulator.git
cd wah-vas-vr-simulator

# Using Python 3
python -m http.server 8000

# Or using Node.js serve
npx serve .
```
Open `http://localhost:8000` in your browser.

> **⚠️ Note for VR Headsets (WebXR):** Browsers require a secure **HTTPS** context (or `localhost` via USB port forwarding) to enable WebXR sessions on standalone headsets. Deploy via **GitHub Pages**, **Vercel**, or **Netlify** for instant HTTPS access on Meta Quest Browser.

---

## 📊 Telemetry JSON Export Schema

Clicking **Assessment Report → Copy JSON Telemetry** exports a structured payload for occupational health records or research analysis:

```json
{
  "timestamp": "2026-10-27T20:19:00.000Z",
  "simulator": "WAH-VAS v5.0 WebXR",
  "stressorsActive": {
    "wind": true,
    "sway": true,
    "rails": false
  },
  "stages": [
    {
      "stage": "Stage 0: Ground Baseline Calibration",
      "altitudeMeters": 0,
      "targetsVerified": "2/2",
      "exposureSeconds": 14.52,
      "meanSwayMM": 1.18,
      "peakTremorMM": 2.04
    }
  ]
}
```

---

## ⚠️ Safety & Clinical Disclaimer

This software is an educational, training, and research simulation tool. When operating in immersive VR headset mode:
* Always ensure a clear physical floor space free of trip hazards.
* Have a spotter or instructor present during high-elevation unguarded plank stages (`Stage 3` & `Stage 4`), as strong visual-vestibular conflict at simulated heights can induce sudden balance corrections.
* Immediately discontinue use if the participant experiences severe motion sickness, dizziness, or acute panic.

---

## 📄 License

Distributed under the **MIT License**. Free for commercial, educational, and occupational safety training use.
