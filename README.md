# GeoGuesser VR 🌍

An immersive, hands-first 360° street view and world landmark geographic exploration game built for WebXR and Meta Quest devices using Meta's **Immersive Web SDK (IWSDK)**.

## 🌐 Live Demo

Play the app here: [GeoGuesser VR](https://geoguesser-lemon.vercel.app/)

---

## 🏆 Project Highlights

* **Track:** Gaming (*Hands-first, seated-optimized, no controllers required*)
* **Design Philosophy:** Airplane Seat Test compliant (*All interactions function smoothly within a 2-foot seated radius*)
* **Target Devices:** Meta Quest 2 / 3 / 3S / Pro (via Meta Quest Browser), Meta VR Glasses, and desktop browsers with WebXR simulation.
* **Core Technology:** Built on IWSDK, Three.js, Horizon UIKitML, WebXR Hand Tracking, and the Web Audio API.

---

## ✨ Features

### 1. High-Resolution 360° Photospheres & Panoramic Environments
* Stand directly inside iconic world locations across **France (Paris)**, **Russia (Moscow & Saint Petersburg)**, **India (Agra & Mumbai)**, **United States of America**, and famous world heritage locations across **South America**, **Africa**, **Oceania**, and **Europe**.
* Dual-layer rendering: Instant procedural equirectangular projection with road markings and landmark silhouettes, overlaid with high-resolution photographic 360° panoramas.
* Authentic street view visual cues: Nadir camera blur, ground-projected compass ring, road navigation directional chevrons, and localized street signs in Cyrillic, Devanagari, French, and English.

### 2. 3D Holographic Interactive Globe
* Drop pins directly onto a floating 3D holographic Earth globe with your hand ray or touch pointer.
* Live geodetic math: Computes great-circle distance (Haversine formula), nearest sovereign country, and displays an animated geodesic arc connecting your guess to the actual monument coordinates.

### 3. Hands-First & Seated Comfort
* **Zero Controllers Needed:** Complete end-to-end hand tracking (`XRHand`) pinch, point, and tap support.
* **Comfort Snap-Turn:** Rotate your viewpoint 45° left or right with a single tap to inspect surroundings without physical neck strain.
* **Binoculars Zoom:** Toggle 2× optical magnification to examine distant architecture, license plates, and environmental hints.
* **Minimizeable Floating HUD:** Click the **Minimize** button to collapse bulky controls into a slim lap-level dashboard, giving you an unobstructed 360° panoramic view while keeping country choices and scoring accessible.

### 4. High-Contrast Accessible Spatial UI
* Solid white cards with bold black text (`#000000`) for maximum legibility in virtual reality.
* Two-step selection safety: Mark and inspect your selection before pressing **Confirm & Submit**.
* Filter countries easily by continent pills (Europe, Asia, Americas, Africa, Oceania).

### 5. Zero-Latency Procedural Audio
* Custom Web Audio synthesizer producing responsive clicks, correct arpeggios, error buzzers, and victory fanfares without external audio files.

---

## 🚀 Getting Started

### Prerequisites
* [Node.js](https://nodejs.org/) (version `20.19.0` or higher, or `22.12.0+`)
* `npm` (comes with Node.js)

### Installation
```bash
git clone https://github.com/<YOUR-USERNAME>/<YOUR-REPO-NAME>.git
cd <YOUR-REPO-NAME>
npm install
```

### Running Locally
```bash
# Start the local development server with WebXR support
npm run dev

# Or run Vite directly
npm run dev:runtime
```

* Open your browser at `http://localhost:8081` (or `https://localhost:8081`).
* Click **Start World Expedition** to begin playing.

### Testing on Meta Quest
1. Connect your Meta Quest headset and computer to the **same Wi-Fi network**.
2. Find your computer's local IP address (e.g. `192.168.1.50`).
3. Inside your headset, open the **Meta Quest Browser** and navigate to:
   ```
   https://<YOUR-PC-IP>:8081
   ```
   *(Accept the local development certificate warning if prompted).*
4. Tap **"Enter VR Headset"** to enter the immersive hands-first session.

---

## 🛠️ Build & Deployment

### Production Build
```bash
npm run build
```
Generates a production-ready, minified build in the `dist/` directory.

### GitHub Pages (Automated Deployment)
A pre-configured GitHub Actions workflow is included at [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml).

To enable automated deployment:
1. Push this repository to GitHub.
2. In your GitHub repository, navigate to **Settings** → **Pages**.
3. Under **Build and deployment** → **Source**, select **GitHub Actions**.
4. Every push to `main` or `master` will automatically build and deploy your WebXR application to your free GitHub Pages URL.

---

## 📁 Project Structure

```
├── .github/
│   └── workflows/
│       └── deploy.yml          # Automated GitHub Pages CI/CD workflow
├── public/
│   ├── panoramas/              # High-resolution 360° equirectangular panoramas
│   ├── scenes/
│   │   └── main.iwsdk.scene.json # Spatial composition, lighting & panel placement
│   └── ui/
│       └── geoguessr.uikitml   # Horizon OS spatial UI panel layout
├── src/
│   ├── data/
│   │   ├── countries.ts        # Global country coordinates, continents & flags
│   │   └── locations.ts        # Curated world monuments & street view coordinates
│   ├── systems/
│   │   ├── audio.ts            # Web Audio procedural sound synthesizer
│   │   ├── game.ts             # Game state machine & distance scoring
│   │   ├── globe.ts            # 3D Holographic Globe & raycast pin placement
│   │   ├── panorama.ts         # Inverted 360° photosphere sphere & comfort zoom
│   │   └── procedural-pano.ts  # Procedural canvas generator with street view cues
│   ├── index.ts                # Application entry point & ECS systems registration
│   └── panel.ts                # Spatial UI controller & minimize HUD handler
├── iwsdk.config.json           # Immersive Web SDK project authority & XR settings
├── vite.config.ts              # Vite bundler configuration
└── package.json                # Project scripts & dependencies
```

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
