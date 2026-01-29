# $ISRAELSCAN — Implementation Plan

## Tech Approach
Single HTML file with embedded CSS and JS. This is a crypto token landing page / dashboard — single-file deployment is ideal for simplicity, hosting on any static server or IPFS, and zero build tooling. All styles and scripts inline.

## File Structure
```
israelscan/
└── index.html    (single file — all HTML, CSS, JS embedded)
```

## Implementation Steps

### Step 1: HTML Skeleton + CSS Foundation
- Full viewport layout using CSS Grid (header / sidebar / main / footer)
- CSS custom properties for the color palette
- Import Google Fonts: JetBrains Mono, Share Tech Mono, Orbitron
- Base dark theme (#0a0f0d background)
- CRT scanline overlay via CSS pseudo-element with repeating-linear-gradient
- Subtle noise texture via CSS (SVG filter or repeating pattern)

### Step 2: Header Bar
- Logo mark (CSS-drawn radar/hexagon icon)
- Title: "Israel Scan" + subtitle "Real-Time Logistics & Node Monitoring"
- Nav tabs: Transportation | Israel Map | Live Feed (styled as terminal tabs)
- Action buttons: Reset View, Zoom, Export (outlined neon cyan buttons)
- Bottom border with animated gradient line

### Step 3: Left Sidebar — Control Panel
- Contract address display with copy-to-clipboard button
- Search input with monospace styling and cyan focus glow
- Dropdown selector for data indicators
- Animation speed slider (custom styled range input)
- "Refresh Data" button with pulsing glow animation
- Section dividers with dashed lines

### Step 4: Left Sidebar — Data Readout
- Terminal-style data panel showing: Profile, Indicator, Latest Value, Year, Capital, Selected
- Typing animation effect on values (JS typewriter)
- Trend Analysis section with mini ASCII-style chart or "NO DATA AVAILABLE" state
- Green/cyan monospace text on dark panels

### Step 5: Left Sidebar — Assets & Routes (Detected Nodes)
- Scrollable list of infrastructure nodes
- Each item: icon + name + type badge + status indicator (pulsing dot)
- Hover glow effect on each list item
- Grouped by category (airports, seaports, rail, borders)

### Step 6: Main Area — SVG Map of Israel
- Hand-coded SVG outline of Israel (approximate polygon path)
- Glowing border effect (CSS filter: drop-shadow with cyan glow)
- Grid overlay lines across the map area
- Positioned node markers at real geographic locations:
  - Airports: Ben Gurion (TLV), Ramon (ETM), Haifa, Sde Dov area
  - Seaports: Haifa, Ashdod, Eilat
  - Rail hubs: Tel Aviv, Haifa, Beer Sheva, Jerusalem
  - Border crossings: Taba, Allenby, Erez, Rosh HaNikra, Quneitra
- Route lines connecting nodes (SVG path with dash animation)
- Each marker: SVG icon + pulsing ring animation
- Compass indicator (N/S/E/W) in corner
- System status bar at bottom of map: "RES: 1920x1080 | STATUS: LOADED | SIGNAL: ACTIVE"

### Step 7: Radar Sweep Animation
- CSS-animated radar sweep overlay on the map (conic-gradient rotating)
- Semi-transparent cyan sweep arc
- Positioned in map center or corner

### Step 8: Filter Bar (Below Map)
- Toggle buttons: Airports / Seaports / Rail / Borders / Routes
- Active state with filled background, inactive with outline
- JS toggles visibility of corresponding SVG node groups

### Step 9: Stats Bar
- Horizontal bar with 4 stat cards
- "Total Nodes Tracked: 47" — counter ticker animation
- "Active Routes: 12" — counter ticker
- "Data Points: 24,891" — counter ticker
- "Last Updated: [live timestamp]" — real-time clock
- Numbers animate counting up on page load

### Step 10: Token Info Panel
- $ISCAN contract address with copy button
- "BUY ON PUMP.FUN" button (large, gold/yellow, glowing)
- Holder count display
- Styled as a highlighted panel with border glow

### Step 11: Footer
- Social links: Twitter/X, Telegram, pump.fun (icon + text)
- Disclaimer: "For educational and analytical purposes only..."
- Version: "v1.0.0 | BUILD 2025.01"
- Muted styling, subtle top border

### Step 12: Animations & Effects
- Glitch effect on headers: CSS clip-path animation with color channel offset
- Typing effect on data values: JS interval-based character reveal
- Counter tickers: JS animated number counting
- Node pulse: CSS keyframe scale + opacity animation
- Route travel: SVG stroke-dashoffset animation
- CRT flicker: occasional subtle opacity flash
- Hover glow: CSS transition on box-shadow

### Step 13: Fake Live Data System
- JS module that generates periodic data updates
- Random node status changes (active/inactive)
- Timestamp updates every second
- Occasional "alert" events in data feed
- Data counter increments periodically

### Step 14: Interactivity
- Map node click: highlights node, shows info in sidebar
- Filter toggles: show/hide node categories on map
- Search input: filters node list in sidebar
- Copy buttons: clipboard API for contract address
- Nav tabs: switch between view modes (visual state changes)
- Hover tooltips on map nodes

## Key Technical Decisions

1. **SVG Map**: Hand-drawn SVG path for Israel outline. Node positions calculated as percentage-based coordinates within the SVG viewBox. No external map library needed.

2. **Animations**: Pure CSS animations where possible (pulse, glow, sweep, scanlines). JS only for data-driven animations (counters, typing, route travel).

3. **Layout**: CSS Grid for main layout. Flexbox for component internals. Fixed viewport (100vh/100vw), overflow hidden.

4. **Fake Data**: Hardcoded arrays of real Israeli infrastructure data (names, types, coordinates). Periodic JS intervals simulate live updates.

5. **No Dependencies**: Zero external JS libraries. Pure vanilla HTML/CSS/JS. Only external resources are Google Fonts.

6. **Icons**: SVG inline icons for node types (plane, anchor, train, flag). Simple geometric shapes, not icon libraries.
