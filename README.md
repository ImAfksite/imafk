✦ I’M AFK — 

> An enjoyable, interactive WebGL physics playground and standalone web game arcade. Play, test, and host client-side HTML5 simulations directly in the browser/ our systems.

---

## 🌊 The Bubbles Engine

The  layer is built upon a custom WebGL shader pipeline paired with a discrete 2D physics simulation:

- **Refraction & Surface Tension**: Real-time metaball field computation (`field += r * r / dSq`) with normal-gradient mapping (`nGrad = (grad / gradLen) * nScale`), Schlick Fresnel reflection, and depth attenuation.
- **Chromatic Aberration**: Multi-sampled color dispersion (`bgCA.r`, `bgCA.g`, `bgCA.b`) across the refracted UV coordinates.
- **Physics Simulation**: Fixed-timestep (`8ms`) Verlet integration supporting:
  - Cursor repulsion forces
  - Pairwise surface tension pull
  - Area-conserving droplet merging
  - Momentum-driven droplet splitting at high velocities
  - Soft-body trailing teardrop deformation
  - Drag-and-spawn particle generation

---

## 🚀 Our Capabilities

1. **Pure Client-Side Focus Mode**
   - Instantly loads games into a sandbox iframe with zero downloads fr chat.
   - Includes live restart, dedicated new-tab opener, and native fullscreen trigger.

2. **Dual-Source Game Synchronization**
   - **Database Integration**: Live catalog updates for newly published community submissions. Yes dawg you publish a game and it's then on the page instantly.
   - **GitHub Repository Indexer**: Automatically parses `.html` builds stored in the `/games` directory.

3. **Creator Submission Studio (`studio.html`)**
   - Drag-and-drop `.html` game files with instant code metrics (character, line count, and byte estimates).
   - In-page isolated sandbox preview modal.
   - This is one of the coolest thing I have every added to this.

4. **Bilingual Localization (EN / AR)**
   - Complete toggle for English and Arabic with bidirectional RTL layout transformation.
   - This might get removed because We will be adding an instant localization to all language.

5. **Moderation Suite (`admin.html`)**
   - Secure authorization gate, live submission inspection, sandbox testing, takedown toggles, and record deletion.
   - Yeah we have the admin section.

---

## 📂 File Architecture

```text
├── index.html       # Home page
├── submit.html      # Pulbish games page.
├── studio.html      # Bored Game devs studio.
├── contact.html     # Support Relay & DMCA Dispatch Portal
├── tos.html         # Interactive Protocol & License Agreement
├── admin.html       # Moderation & Database Controller
├── games/           # Games I found !The Games were not made by me(imafksite)
└── README.md        # Documentation

📜 License

Distributed under the MIT License. Built with ❤️ for web physics & arcade
lovers.
