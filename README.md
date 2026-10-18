# Toll-Booth Operations & Traffic Simulation System

[![Deployment: Netlify](https://img.shields.io/badge/Deployment-Netlify_Ready-00C7B7?logo=netlify&logoColor=white)](https://your-toll-plaza-simulation.netlify.app)
[![Tech: HTML5 / CSS3 / ES6](https://img.shields.io/badge/Stack-Vanilla_HTML5_%2F_CSS3_%2F_ES6-E34F26?logo=html5&logoColor=white)](#technologies)
[![Map: Leaflet / OpenStreetMap](https://img.shields.io/badge/GIS-Leaflet_%2B_OpenStreetMap-199900?logo=leaflet&logoColor=white)](https://leafletjs.com/)
[![Academic: B.Sc. CS Practical](https://img.shields.io/badge/Academic-B.Sc._CS_Semester_V-4F46E5)](#academic-origin--enhancement-history)

An interactive, multi-lane highway toll plaza simulation and intelligent traffic management operations dashboard. Originally developed as part of a **B.Sc. Computer Science Semester V practical examination**, this project has been upgraded into an operations-grade simulation featuring six independent lanes (dual carriageway), realistic lane-queuing physics, live booth monitoring, and comprehensive audit reporting.

---


## 🎓 Academic Origin & Enhancement History

To provide complete academic transparency, this repository clearly distinguishes the original practical exam implementation from the modern enhancements:

### 1. Original Practical Exam Features (B.Sc. CS Semester V)
- **Vehicle Classification & Tariffs:** Implemented 10 distinct vehicle categories with individual toll rates, service times, and queue waiting limits.
- **Toll Calculation Engine:** Fee computation with single, double, and triple trip multipliers.
- **Waiting-Time Waiver Rule:** Exemption logic waiving tolls if waiting time exceeds category-specific limits (e.g. 5 minutes for two-wheelers, 10 minutes for four-wheelers).
- **Penalties & Violations:** Fixed penalties for excessive honking (&gt; 5 honks, +₹200) and pollution emissions (+₹500).
- **Basic Exemptions:** Toll exemption for emergency services (ambulances, fire brigades) and category-based local exemptions.
- **Initial Single-Lane Prototype:** The foundational single-booth prototype remains preserved in [`index1.html`](file:///Users/minalmaurya/TollBoothSimulator/index1.html) as an archival record.

### 2. Modern Professional Enhancements
- **Six-Lane Dual-Carriageway Plaza:** Models 3 inbound and 3 outbound lanes separated by a central highway median strip.
- **Realistic Kinematic Queuing:** Vehicles approach along lane centerlines, hold steady queue spacings, smoothly ripple forward as front vehicles depart, stop at booth windows during service, and drive down the exit corridor before despawning.
- **Live 6-Lane Operations Monitor:** Real-time dashboard visualizer displaying current booth activity (STANDBY / PROCESSING / CLEARING) and live queue visualizer strips.
- **Comprehensive Results & Audit Hub:** Real-time search, category/outcome filtering (All, Paid, Toll-Free, Exempt, Fined), and one-click **CSV Audit Log Export**.
- **Interactive Map Geodesics:** Seamless toll plaza relocation anywhere on Earth via Leaflet map clicks, plus quick-selection presets for major Indian expressway plazas (Mumbai, Delhi-Gurugram, Bengaluru, Pune).
- **Responsive Highway Operations UI:** Adaptive layout supporting desktop split-screen resizer (mouse & keyboard accessible) as well as mobile/tablet segmented views.

---

## 📜 Toll Rules, Tariffs & Enforcement Model

| Category | Key | Base Toll (₹) | Max Wait Limit | Service Time | Toll Exempt? | Fine Waived? |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| 🛵 Two-wheeler | `TWO` | ₹30 | 5 min | 2 min | No | No |
| 🛺 Three-wheeler | `THREE` | ₹50 | 7 min | 3 min | No | No |
| 🚗 Four-wheeler (Car) | `FOUR` | ₹100 | 10 min | 4 min | No | No |
| 🚚 Six-wheeler (Truck) | `SIX` | ₹180 | 12 min | 6 min | No | No |
| 🚛 Container Truck | `CONT` | ₹250 | 15 min | 8 min | No | No |
| 🚑 Ambulance | `AMB` | ₹0 | 0 min | 0 min | **Yes** | **Yes** |
| 🚒 Fire Brigade | `FIRE` | ₹0 | 0 min | 0 min | **Yes** | **Yes** |
| 🚘 Government Vehicle | `GOV` | ₹0 | 0 min | 2 min | **Yes** | No |
| 🚌 Government Bus | `GBUS` | ₹0 | 0 min | 4 min | **Yes** | No |
| 🎫 Exempted (Locals) | `EXEM` | ₹0 | 0 min | 1 min | **Yes** | No |

### Business Rules Summary
1. **Trip Multipliers:** Single Journey ($1\times$), Return/Double ($2\times$), Multi-trip/Triple ($3\times$).
2. **Waiting-Time Waiver:** Non-exempt vehicles pay `Base Toll × Multiplier` only if `waited ≤ waitLimit`. If queue delay exceeds limit, toll is completely waived (₹0).
3. **Violations & Penalties:** Horn violations (&gt; 5 honks) incur ₹200. Pollution non-compliance incurs ₹500.
4. **Emergency Vehicles:** Ambulances and fire brigades receive 0-wait clearance, ₹0 toll, and full waiver of violation fines.
5. **Local Vehicles:** Local exemption is applied based on vehicle classification tags (illustrative academic rule).

---

## 🛠️ Technologies & Architecture

- **Markup & Styling:** Semantic HTML5, CSS3 Custom Properties (Dark traffic-management theme), Flexbox & CSS Grid.
- **Interactive Mapping:** [Leaflet.js 1.9.4](https://leafletjs.com/) with [OpenStreetMap](https://www.openstreetmap.org/) cartography.
- **Simulation Engine:** Asynchronous event timeline with continuous multi-server queuing logic ($M/G/k$).
- **Zero Build Dependencies:** Pure client-side vanilla JavaScript (ES6+). Zero Node modules or webpack/vite compilation required.

---

## 🚀 Running Locally

No installation or build steps are required. Clone the repository and serve it using any static HTTP server:

```bash
# Clone the repository
git clone https://github.com/your-username/TollBoothSimulator.git
cd TollBoothSimulator

# Option 1: Python 3 HTTP Server
python3 -m http.server 8000

# Option 2: Node.js npx serve
npx serve .
```

Open [http://localhost:8000](http://localhost:8000) in any modern web browser (Google Chrome, Firefox, Safari, Microsoft Edge). An active internet connection is required to load OpenStreetMap tiles.

---

## ☁️ Deploying to Netlify

This project is 100% static and pre-configured for instant zero-configuration deployment on Netlify:


## ⚠️ Simulation Assumptions & Academic Limitations

- **Educational Simulation:** Toll tariffs, penalty amounts, and vehicle behaviors are designed for educational modeling and do not represent official government highway regulations.
- **Simulated Highway Corridor:** Vehicles follow mathematically calculated approach lanes and departure vectors on the map; live GPS routing and road network turn-by-turn navigation are not used.
- **Local Resident Exemption:** Local exemptions are assigned via vehicle category attributes (`EXEM`) rather than live geographical boundary detection.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE) — free for educational, academic, and portfolio demonstration use.
