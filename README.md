# ArenaAuction: Zero-Backend Sports Auction System

A real-time, client-side player auction system engineered for live sports events. Originally built and deployed for the Narawala Super League (NSL), this system provides a broadcast-quality projector display controlled by a separate admin dashboard, all synchronized locally with zero network latency.

## Architecture & Technical Highlights

This project intentionally avoids a traditional client-server architecture to ensure reliability in physical venue settings with unpredictable Wi-Fi.

- **Zero-latency synchronization:** Uses the native HTML5 `BroadcastChannel` API to transmit bidding events from the controller window to the projector display window.
- **Fail-safe state management:** Uses `localStorage` to persist team wallets, squad counts, and player availability across browser refreshes.
- **Algorithm-driven bidding:** Enforces bidding slabs such as `+2k`, `+2.5k`, `+5k`, and `+10k` based on the current active bid.

## Tech Stack

- **Core:** HTML5 and Vanilla JavaScript (ES6+)
- **Styling:** Tailwind CSS via CDN
- **Fonts and UI:** Google Fonts, including Bebas Neue and Orbitron, with CSS glassmorphism
- **Animations:** `canvas-confetti` for live celebration overlays

## Features

- **Dual-view system:** `controller.html` provides the admin dashboard and `display.html` provides the public/projector view.
- **Live purse tracking:** Validates bids against each franchise's remaining purse and squad limit.
- **Smart filtering:** Sold players are removed from the active selection pool to prevent auction errors.
- **TV-broadcast aesthetic:** Dark mode UI with neon accents, pulsing bid updates, and an animated news ticker.
- **Multi-view projector:** The controller can switch the projector between the active player bid and a full-screen franchise leaderboard.

## How to Run Locally

This is a strictly client-side application with no build step, backend server, or database.

1. Clone the repository:

   ```bash
   git clone https://github.com/mkvmethsara/live-sports-auction-system.git
   cd live-sports-auction-system
   ```

2. Open `controller.html` in a modern browser.
3. Open `display.html` in another browser window or tab on the same origin.
4. Use the controller window to manage the auction and the display window for the projector/public view.

For the most reliable `BroadcastChannel` behavior, serve the folder through a simple local web server instead of opening the files directly:

```bash
python -m http.server 8000
```

Then open:

- `http://localhost:8000/controller.html`
- `http://localhost:8000/display.html`

## Repository Contents

- `controller.html` - Auction control dashboard
- `display.html` - Projector and public display
- `PLAYER LIST/` - Player profile images
- `TEAM LOGOS/` - Franchise/team logos
- `MAIN LOGO.png` - Application branding
