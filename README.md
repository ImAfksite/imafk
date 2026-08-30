# ✦ I’M AFK — Curated Web Games Platform

> A bright, tranquil, and frictionless web arcade and experiment sandbox. Play, test, and host standalone HTML5 games without installs, paywalls, or intrusive trackers.

---

## 🎨 Visual Identity & Design Philosophy

I'm Afk is built around the **Aurora & Ethereal Liquid Glass** aesthetic:
- **Warm & Calm Palette**: Rich champagne backgrounds (`#f8f4ee` to `#f2dfcc`), soft warm peach hazes, and deep espresso typography (`#211914`).
- **Sculpted Interfaces**: Frosted milky glass cards (`backdrop-filter: blur(25px)`), subtle 1px inner sheen strokes, and organic morphing SVG blobs with dynamic parallax.
- **Editorial Typography**: Pairing of `Space Grotesk` (headings), `Plus Jakarta Sans` (interface), and `Tajawal` (full Arabic RTL typography).

---

## 🚀 Key Features

1. **Pure Web Play (Dual Engine)**
   - **Supabase Integration**: Automatically fetches community-submitted games in real time.
   - **GitHub Repository Indexer**: Automatically scans and indexes games placed in the `/games` folder of `imafksite/imafk`.
   - **Fallback Built-ins**: Includes curated games (Snake Protocol & Pong Dynamics) even without internet connectivity.

2. **Dedicated Fullscreen Focus Player**
   - Seamlessly transitions from the game grid into an uninterrupted fullscreen sandbox frame.
   - Includes instant restart, open in new tab, and native browser fullscreen triggers.

3. **Creator Submission Studio (`submit.html`)**
   - Drag-and-drop `.html` game files with real-time character, line, and file size counters.
   - Built-in live sandbox preview modal to test games before submitting.
   - Direct publication into the database.

4. **Bilingual Localization (EN / AR)**
   - Native toggle between English and Arabic with bidirectional layout adaptation (`dir="ltr"` / `dir="rtl"`).

5. **Legal & Security Suite**
   - **Terms of Service (`tos.html`)**: Interactive certified protocol agreement with reading progress bar and local storage seal.
   - **Support Desk (`contact.html`)**: Integrated Formspree ticketing system with honeypot spam protection for bugs and 24-hour DMCA requests.
   - **Moderation Node (`admin.html`)**: Encrypted access room with instant sandbox testing, live status toggling, takedowns, and record deletion.

---

## 📂 Repository Structure

```text
├── index.html       # Main Hub & Dedicated Focus Game Player
├── submit.html      # Creator Studio & Sandbox Test Runner
├── contact.html     # Support Relay & DMCA Dispatch Portal
├── tos.html         # Interactive Protocol & License Agreement
├── admin.html       # Encrypted Moderation & DB Management Node
├── games/           # Standalone HTML5 game files (auto-indexed)
└── README.md        # Documentation & Developer Guide

🛠️ Database Schema (Supabase)

To support community submissions, create a table named games in Supabase with
the following schema:

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

-- Enable public read access for live games
alter table public.games enable row level security;

create policy "Allow public read access"
on public.games for select
using (status = 'live');

create policy "Allow public game submission"
on public.games for insert
with check (true);

💻 Running Locally

No build tools, Node.js, or package managers required. Simply serve the
directory with any static server:

# Using Python 3
python -m http.server 8000

# Using Node.js npx serve
npx serve .

Open http://localhost:8000 in any modern web browser.

📜 License

Distributed under the MIT License. Created with ❤️ for gamers and developers
everywhere.
