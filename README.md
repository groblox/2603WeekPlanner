# 2603 Week Planner

A premium, distraction-free, paper-themed weekly planner and outliner designed for fast keyboard-driven workflows. The entire application is contained within a single, highly-optimized `index.html` file—no build tools, no framework dependencies, and no server configuration required.

---

## 🌟 Key Features

### ⌨️ Outliner & Keyboard Workflow
* **Seamless Text Editing** — Direct in-place editing using HTML5 `contenteditable`. Tasks behave like a natural document outline.
* **Automatic Line Management** — A trailing blank task is automatically appended at the bottom, keeping the interface ready for new entries. Empty unused trailing rows are automatically cleaned up.
* **Keyboard-Driven Shortcuts**
  * `Enter` — Splits the current line at the cursor, creating a new task directly below.
  * `Backspace` (at the start of a line) — Merges the current task's text with the line above or deletes it if already empty.
  * `Arrow Up` / `Arrow Down` — Moves focus sequentially up and down the list.
* **Inline Deletion** — Hover over any row on desktop to reveal a quick `×` delete button.

### 🏷️ Rich Metadata & Context Tags
* **Time Estimates** — Allocate effort to tasks with three distinct presets:
  * **15 min** (● small dot)
  * **30 min** (● medium dot)
  * **1 hr** (◯ hollow circle)
  * *Note: Only one time estimate can be active per task. Clicking an active estimate clears it.*
* **Contextual Tags**
  * 💻 **Computer** — Visual tag for desk, screen, or focused digital work.
  * ☀️ **Daytime / Outdoors** — Visual tag for physical errands, outdoor tasks, or daylight-restricted work.
* **Intelligent Behavior** — Context tags and time estimates are automatically cleared when a task's text is emptied, ensuring storage and layout sanity.

### 📊 Sorting & Filtering
* **Four Dedicated Sort Modes** — Sort the list by clicking headers:
  * ↕️ **Manual Order (`::`)** — Represented by a 2x2 dot grid in the top header (to the right of the stats), allowing custom drag-and-drop reordering.
  * ⏱️ **By Time Estimate** — Groups and sorts tasks from shortest to longest duration.
  * 💻 **By Computer Work** — Prioritizes tasks requiring screen time.
  * ☀️ **By Daytime / Outdoors** — Prioritizes physical and outdoor tasks.
  * *Adaptive Sorting: State changes (like toggling checkbox, time tags, computer, or sun tags) do NOT instantly re-sort tasks. Items preserve their vertical position on edit to prevent accidental "snapping" away. Tasks only sort when a sort/filter button is explicitly clicked.*
* **Status Filtering** — Filter your view between **All**, **Active**, or **Done** using the header-integrated toolbar icons.
* **Real-time Metrics** — Real-time stats header displaying the cumulative estimated time for remaining active tasks (e.g. `~1h 30m`), shifted slightly left for optimal alignment.

### 💾 Persistence & Dropbox Cloud Sync
* **Zero-Latency Auto-Save** — Changes auto-save to browser `localStorage` dynamically as you type (with a lightweight 250ms debounce). Blank trailing rows are excluded from persistence to keep the save data clean.
* **Dropbox Cloud Sync** — Replaces manual file imports/exports with seamless cloud synchronization. Click the cloud icon in the top toolbar to link your own Dropbox App Key. It connects directly via standard scoped OAuth2 to back up and sync tasks across desktop and mobile devices.

### 📱 Adaptive Mobile Experience
The planner features a fully responsive design tailored for mobile screens (under `640px` width):
* **Simplified Row Layout** — Hides desktop-only visual clutter like drag handles and delete buttons to maximize horizontal text space.
* **Mobile-Visible Controls** — The Manual Order (`::`) button is fully visible and usable on mobile.
* **Tap-to-Cycle Time Estimates** — Replaces the three desktop estimate buttons with a single tap-to-cycle glyph. Tap once to assign 15 min (small blue circle), twice for 30 min (medium blue circle), three times for 1 hr (large blue outline circle), and four times to return to the greyed-out square (none).
* **Keyboard Merging** — Delete tasks easily on mobile by backspacing them to empty.

---

## 🎨 Design & Aesthetics

* **Warm Paper Aesthetic** — Built with a muted sand-and-beige color palette (`#f0e8d8` / `#faf6ee`) and high-contrast, elegant Georgia serif typography that mimics the feel of a physical notebook or high-quality paper planner.
* **Premium Dark Mode** — Supports a beautifully designed, high-contrast warm charcoal/dark-sepia theme (`#181510` / `#241f18`) with tailored custom variables that preserve the physical planner aesthetic. It can be toggled using the custom slider switch inside the info popup panel.
* **Functional Color Hints** — Highlights active metadata with harmonized, natural accents:
  * Time estimates glow in muted blue (`#4a7cc7` / `#6c9ce6` in dark mode).
  * Computer contexts illuminate in dark sage green (`#4a8a4a` / `#63b363` in dark mode).
  * Daytime/outdoor contexts glow in warm amber (`#c8840a` / `#e8a72b` in dark mode).
  * Deletions flash in soft terracotta red (`#c05040` / `#e06c5c` in dark mode).
* **Micro-interactions** — Smooth CSS transitions for state toggles, hover effects, theme toggles, and drag-and-drop overlays.
* **Context-Sensitive Info Panel** — Hovering or focusing the information `i` icon in the header reveals an elegant popover containing the estimate legend and the **Dark Mode** toggle switch.

---

## 🛠️ Technical Implementation

* **Single-File Architecture** — HTML, CSS variables, responsive styles, and vanilla JavaScript reside together in `index.html` for instant load times and extreme portability.
* **Vanilla JS Execution** — Enclosed within an Immediately Invoked Function Expression (IIFE) using `'use strict'` to protect scope and prevent global variable pollution.
* **Modern Web APIs & Integrations** — Leverages:
  * `localStorage` API under the key `week-planner-v1` for local offline persistence, and `week-planner-theme` for theme preference persistence.
  * **Dropbox Scoped Access Client** — Utilizes Dropbox REST APIs (`/files/upload` and `/files/download`) using direct client-side OAuth2 token authentication to sync state. Synchronization uses an conflict-free timestamp resolution algorithm comparing last saved tags.
  * HTML5 Drag & Drop API (`dragstart`, `dragend`, `dragover`, `dragleave`, `drop`) for reordering.
  * `crypto.randomUUID` with a fallback mechanism for robust task ID generation.
  * Native CSS Grid (`.row-grid`) for precise alignment across all screen sizes.
* **Accessibility Features** — Outfitted with semantic markup (`header`, `section`, `dl`, `dt`, `dd`) and standard ARIA attributes (`role="checkbox"`, `aria-checked`, `role="tooltip"`, `aria-describedby`, and `aria-label`).

---

## 🚀 Quick Start

### Option 1: Direct Open
Simply double-click the `index.html` file to open it directly in any modern web browser. No server is required.

### Option 2: Local Server (Recommended for persistence across some environments)
If you prefer running a local server, navigate to the folder in your terminal and run:

**Python 3:**
```bash
python3 -m http.server 3000
```
Then visit [http://localhost:3000](http://localhost:3000).

**Node.js / npx:**
```bash
npx serve -l 3001 .
```
Then visit [http://localhost:3001](http://localhost:3001).

---

## 📂 Project Structure

```text
2603WeekPlanner/
├── index.html    # Core Application (Markup, Layout, Typography, & Logic)
└── README.md     # Documentation
```
