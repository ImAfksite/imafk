# ✦ I’M AFK — Web Studio & Project Ecosystem

> A modern, client-side web development studio, interactive WebGL physics engine, and curated HTML5 application hub. Built with clean architecture, zero-dependency sandboxing, and precision editorial design inspired by Addition7.

---

## 🌊 The Liquid Glass Engine

The interactive background operates on a custom WebGL shader pipeline paired with a discrete 2D physics simulation running in Three.js:

- **Refraction & Surface Tension**: Real-time metaball field computation (`field += r * r / dSq`) combined with normal-gradient mapping (`nGrad = (grad / gradLen) * nScale`), Schlick Fresnel reflection, and depth attenuation.
- **Chromatic Dispersion**: Multi-sampled color separation (`bgCA.r`, `bgCA.g`, `bgCA.b`) mapped across refracted UV coordinates.
- **Verlet Integration Physics**: Fixed-timestep (`8ms`) simulation loop featuring:
  - Cursor repulsion vector fields
  - Pairwise surface tension attraction
  - Area-conserving droplet merging
  - Momentum-driven droplet splitting at high velocity thresholds
  - Soft-body trailing spring deformation for organic teardrop contouring
  - Interactive click-and-drag node spawning

---

## 🛠️ Platform Capabilities

### 1. Multi-File Web Coding Studio (`studio.html`)
- **Virtual File System**: Create, rename, switch, and delete HTML, CSS, and JavaScript files and directories directly in the browser.
- **Multi-Tab Workspace**: Tabbed file switching, active file persistence, synchronized line number gutter, and cursor metric tracking.
- **Integrated Live Sandbox**: Instant bundle compilation that inlines project styles and scripts into an isolated iframe preview with configurable auto-reload debounce.
- **Developer Debugging Console**: Real-time console log, warning, and runtime error mirror with an interactive JavaScript REPL prompt evaluated in the sandbox context.
- **Snapshot Time Machine**: Milestone bookmarking system with instant state restoration stored in browser LocalStorage.
- **Export & Import Suite**: Download standalone runnable `.html` files, project JSON bundles, or full multi-project workspace backups.

### 2. Curated Project Library (`library.html`)
- **Dual-Source Sync**: Connects to Supabase cloud records and automated GitHub Pages repository directories (`/games`).
- **Real-Time Telemetry**: Live concurrent player presence tracking via Supabase Realtime channels and persistent play-count analytics.
- **Focused Execution Mode**: Launches standalone creations inside an isolated, distraction-free sandbox with fullscreen, reload, and new-tab support.
- **Dynamic Search & Filtering**: Instant filter by category (*Interactive*, *Classic*, *Community*), title search, and multi-tier sorting (*Most Played*, *Newest*, *A-Z*).

### 3. Creator Submission Pipeline (`submit.html`)
- Direct project publishing to the global catalog with automated metadata parsing.
- Drag-and-drop `.html` file reader with real-time character, line, and byte estimation.
- Pre-submission live sandbox preview modal to verify code execution prior to deployment.

### 4. Root Operations Node (`admin.html`)
- Cryptographically verified passcode gateway with automated session timeout locks.
- Complete catalog database inspector with code editing, live database patching, and batch status toggles (*Live* / *Takedown*).
- Static script security analyzer detecting malicious `eval()`, crypto miners, and unauthorized frame escapes.
- Full database JSON backup and snapshot restoration tools.
- Integrated root CLI terminal for rapid node maintenance.

### 5. Internationalization & Theme System
- Complete bilingual localization (**English** and **Arabic RTL**) with native typography rendering.
- Shared Light and Dark theme engine persisted across all pages via unified `localStorage` preferences.

---

## 📂 File Architecture

```text
├── index.html       # Landing page & WebGL liquid glass physics engine
├── studio.html      # Multi-file HTML/CSS/JS code editor & sandbox studio
├── library.html     # Curated web applications & games catalog with telemetry
├── submit.html      # Creator submission portal with sandbox verification
├── contact.html     # Direct support relay & DMCA inquiry portal
├── tos.html         # Legal protocol, sandboxing terms & licensing
├── admin.html       # Administrative moderation & database operations node
├── games/           # Static standalone HTML5 project directory
├── SECURITY.md      # Security policy, sandboxing model & vulnerability reporting
└── README.md        # Ecosystem documentation
