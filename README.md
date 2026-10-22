# ✦ I’M AFK — Web Studio & Project Ecosystem

> A client-side web development studio, interactive WebGL physics engine, and curated HTML5 application hub. Built with privacy-first sandboxing, continuous-curve continuous geometry, and the macOS Liquid Glass design system.

---

## 🌊 The Liquid Glass & Physics Engine

The interactive background combines an inline SVG displacement map filter with a Three.js WebGL fragment shader driven by a fixed-timestep 2D fluid simulation:

- **Refraction & Surface Tension**: Real-time potential field computation (`field += r * r / dSq`) combined with normal-gradient mapping (`nGrad = (grad / gradLen) * nScale`), dual specular rim reflections, and depth attenuation.
- **Chromatic Dispersion**: Multi-sampled color separation (`bgCA.r`, `bgCA.g`, `bgCA.b`) mapped across refracted UV coordinates.
- **SVG Displacement Filter**: Inline `<filter id="glass-distortion">` utilizing `<feTurbulence>` and `<feDisplacementMap>` to introduce organic micro-refraction across floating glass islands.
- **Verlet Integration Physics**: Fixed-timestep (`8ms`) simulation loop decoupled from display refresh rates, featuring:
  - Proximity cursor repulsion vector fields
  - Pairwise surface tension attraction and area-conserving mergers
  - Velocity-damped boundary restitution (`DAMP = 0.993`, `BOUNCE = 0.45`)
  - Soft-body trailing spring deformation for teardrop contouring
  - Interactive click-and-drag liquid droplet spawning

---

## 🎨 Visual System & Color Architecture

Built on the **macOS Liquid Glass** language—emphasizing optical depth, frosted blurs, specular rim lights, and elastic spring curves:

| Token | Dark Mode (`[data-theme="dark"]`) | Light Mode (`[data-theme="light"]`) | Usage |
| :--- | :--- | :--- | :--- |
| **Canvas Base** | `#070B0A` (Deep Obsidian Matte) | `#F2F6F4` (Paper Mist White) | Root viewport substrate |
| **Glass Surface** | `linear-gradient(145deg, rgba(255,255,255,0.08)...)` | `linear-gradient(145deg, rgba(255,255,255,0.85)...)` | Island surfaces & floating cards |
| **Specular Rim** | `inset 1.5px 1.5px 1px 0 rgba(255,255,255,0.22)` | `inset 1.5px 1.5px 1.5px 0 rgba(255,255,255,1.0)` | Dual-edge rim light |
| **Primary Accent**| `#38E1A6` (Luminous Mint) | `#176B52` (Alpine Forest Emerald) | Active links, primary actions, badges |
| **Accent Glow** | `rgba(56, 225, 166, 0.25)` | `rgba(23, 107, 82, 0.15)` | Dynamic focus rings & shadows |
| **Card Radii** | Continuous squircle `20px`–`28px` | Continuous squircle `20px`–`28px` | Apple continuous pebble curvature |
| **Spring Curves** | `cubic-bezier(0.175, 0.885, 0.32, 1.275)` | `cubic-bezier(0.175, 0.885, 0.32, 1.275)` | Tactile button & dock expansion |

---

## 🛠️ Platform Capabilities

### 1. Landing Hub & Comparison Lab (`index.html`)
- **macOS Floating Capsule Nav**: Streamlined pill-shaped dock housing brand triggers, routing, theme switcher, and mobile drawer toggle.
- **Conversational Tone**: Informal, punchy typography (*"Just play. Or make something cool."*) paired with live client telemetry status capsules.
- **Gateway Bento Grid**: Liquid Glass cards linking directly to the *Game Library*, *Code Studio*, and *Creator Submit Pipeline*.
- **Design Comparison Lab**: Integrated switcher supporting **Interactive Draggable Split Slider** and **Side-by-Side Dual Pane** modes to contrast macOS Liquid Glass against Samsung One UI 9 PC reachability paradigms.

### 2. Multi-File Web Coding Studio (`studio.html`)
- **Virtual File System**: Create, rename, switch, and delete HTML, CSS, and JavaScript files and directories in-browser.
- **Multi-Tab Workspace**: Tabbed file switching, active file persistence, synchronized line number gutter, and cursor metric tracking.
- **Integrated Live Sandbox**: Instant bundle compilation that inlines project styles and scripts into an isolated iframe preview with configurable auto-reload debounce.
- **Developer Debugging Console**: Real-time console log, warning, and runtime error mirror with an interactive JavaScript REPL prompt evaluated in the sandbox context.
- **Snapshot Time Machine**: Milestone bookmarking system with instant state restoration stored in browser `localStorage`.
- **Export & Import Suite**: Download standalone runnable `.html` files, project JSON bundles, or full multi-project workspace backups.

### 3. Curated Project Library (`library.html`)
- **Dual-Source Auto-Sync**: Connects to Supabase cloud records and automated GitHub repository directories (`/games`).
- **Real-Time Telemetry**: Live concurrent player presence tracking via Supabase Realtime WebSocket channels and persistent play-count analytics.
- **Built-in Fallbacks**: Embedded client-side classics (*Retro Snake*, *Minimalist Pong*) for offline availability.
- **Liquid Glass Player Overlay**: Isolated fullscreen sandbox with studio code handoff, standalone tab launching, reload, and fullscreen capabilities.
- **Command Dock**: Live debounced search, alphabetical/popularity sorting, and category filter pills (*All*, *Popular*, *Arcade*, *Classic*, *Community*).

### 4. Creator Submission Pipeline (`submit.html`)
- **Drag-and-Drop Ingestion**: Interactive file drop zone with automatic title generation, line counter, and character estimation.
- **Live Verification Sandbox**: Fullscreen Stage Manager-style modal preview executing code through an ephemeral `Blob` URL prior to deployment.
- **Direct Database Relay**: Publishes metadata and source code directly to the live Supabase catalog with non-blocking UI states.

### 5. Support & Inquiries Portal (`contact.html`)
- **Direct Category Dispatch**: Pre-configured support channels for General Inquiries, Game Reports, and DMCA/Takedowns.
- **Honeypot-Protected Formspree Relay**: Spam-filtered direct messaging system without third-party tracking scripts.
- **Ambient Topic Bento**: Quick visual overview of support response workflows and guidelines.

### 6. Root Operations Node (`admin.html`)
- **Cryptographic Gatekeeper**: SHA-256 verified passcode gateway with automated session timeout locks.
- **Catalog Database Inspector**: Live database patching, code editor, and batch status toggles (*Live* / *Takedown*).
- **Static Security Auditor**: Static analyzer detecting unauthorized frame escapes, malicious `eval()`, and crypto miners.
- **Snapshot Suite & Root CLI**: Full database JSON backup, snapshot restoration tools, and an integrated root terminal for maintenance.

---

## 📂 File Architecture

```text
├── index.html           # Landing page, Three.js liquid engine & design comparison lab
├── library.html         # Curated catalog with presence telemetry & player modal
├── studio.html          # Multi-file HTML/CSS/JS sandbox IDE & REPL console
├── submit.html          # Project publisher with drag-and-drop & sandbox verification
├── contact.html         # Support relay, glitch reporting & DMCA inquiry portal
├── tos.html             # Terms of service, offline sandboxing policy & licensing
├── admin.html           # Secure database inspector, code patcher & CLI terminal
├── icon.png             # Favicon & platform emblem
├── games/               # Static repository directory for standalone HTML5 games
│   ├── snake.html
│   └── pong.html
├── SECURITY.md          # Sandboxing security model & vulnerability disclosure
└── README.md            # Platform ecosystem documentation & specifications
