✦ I’M AFK — Liquid Glass Web Arcade

> An ethereal, interactive WebGL physics playground and standalone web game arcade. Play, test, and host client-side HTML5 simulations directly in the browser.

---

## 🌊 Liquid Glass Refraction Engine

The visual layer is built upon a custom WebGL shader pipeline paired with a discrete 2D physics simulation:

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

## 🚀 Platform Capabilities

1. **Pure Client-Side Focus Mode**
   - Instantly loads games into an isolated sandbox iframe with zero downloads or trackers.
   - Includes live restart, dedicated new-tab launcher, and native fullscreen triggers.

2. **Dual-Source Game Synchronization**
   - **Supabase Integration**: Live catalog updates for newly published community submissions.
   - **GitHub Repository Indexer**: Automatically parses `.html` builds stored in the `/games` directory.
   - **Fallback Built-ins**: Built-in games (`Retro Snake`, `Neon Pong`) ready offline.

3. **Creator Submission Studio (`submit.html`)**
   - Drag-and-drop `.html` game files with instant code metrics (character, line count, and byte estimates).
   - In-page isolated sandbox preview modal.

4. **Bilingual Localization (EN / AR)**
   - Complete toggle for English and Arabic with bidirectional RTL layout transformation.

5. **Moderation Suite (`admin.html`)**
   - Secure authorization gate, live submission inspection, sandbox testing, takedown toggles, and record deletion.

---

## 📂 File Architecture

```text
├── index.html       # WebGL Liquid Refraction Engine & Arcade Hub
├── submit.html      # Creator Studio & Live Sandbox Runner
├── contact.html     # Support Relay & DMCA Dispatch Portal
├── tos.html         # Interactive Protocol & License Agreement
├── admin.html       # Encrypted Moderation & Database Controller
├── games/           # Standalone HTML5 builds (auto-indexed)
└── README.md        # Technical Documentation

🛠️ Supabase Setup

Run this SQL snippet in your Supabase SQL Editor:

create table public.games (
  id uuid primary key default gen_random_uuid(),
  created_at timestamp with time zone default timezone('utc'::text, now()) not null,
  title text not null,
  author text not null,
  source_url text,
  html_code text not null,
  email text not null,
  status text default 'live'::text,
  takedown_reason text
);

alter table public.games enable row level security;

create policy "Allow public read access"
on public.games for select
using (status = 'live');

create policy "Allow public game submission"
on public.games for insert
with check (true);

📜 License

Distributed under the MIT License. Built with ❤️ for web physics & arcade
lovers.
