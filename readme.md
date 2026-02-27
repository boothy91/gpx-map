# 🗺️ Trail Planner

A lightweight, browser-based trail planning tool for mapping hiking routes, estimating distances, and exporting tracks.

**Live app:** [https://boothy91.github.io/gpx-map/](https://boothy91.github.io/gpx-map/)

---

## Features

- **Click-to-add waypoints** — tap anywhere on the map to build a route
- **Routed paths** — uses the OpenRouteService API to follow real trails and roads rather than straight lines
- **Elevation profile** — visualises ascent and descent across your route
- **Stats panel** — live distance, estimated hiking time, total ascent and descent
- **GPX & GeoJSON export** — download your route for use in other apps (Garmin, Komoot, etc.)
- **Satellite view** — toggle between standard and satellite basemaps
- **Undo / Redo / Clear** — full waypoint history management
- **Locate me** — centres the map on your current position
- **Responsive** — works on desktop and mobile (slide-in panel on small screens)

---

## Usage

1. Open the app at the link above
2. Click or tap on the map to place waypoints — the route will be drawn automatically between them
3. View distance, time, and elevation stats in the side panel
4. Export your route as **GPX** or **GeoJSON** using the export buttons

> If the OpenRouteService API is unavailable, the app falls back to straight-line segments and shows a warning.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Map rendering | [MapLibre GL JS](https://maplibre.org/) v3.6.2 |
| Basemap | OpenStreetMap / Esri World Imagery (satellite) |
| Routing & elevation | [OpenRouteService API](https://openrouteservice.org/) (foot-hiking profile) |
| Fonts | DM Mono, Fraunces (Google Fonts) |
| Hosting | GitHub Pages |

No build step, no framework — plain HTML, CSS, and vanilla JavaScript in a single file.

---

## Known Issues & Limitations

- Routing requires a valid OpenRouteService API key — without one (or if the key is inactive), routes fall back to straight lines
- The `Authorization` header must use the `Bearer <key>` format required by the ORS API
- Elevation data is only available when the ORS API returns a successful response; straight-line fallback shows no elevation profile
- No persistent storage — waypoints are lost on page refresh

---

## Local Development

No build tools required. Just clone and open:

```bash
git clone https://github.com/boothy91/gpx-map.git
cd gpx-map
open index.html
```

To enable routing, add your [OpenRouteService API key](https://openrouteservice.org/) on line 256 of `index.html`:

```js
const ORS_KEY = "Bearer your-api-key-here";
```

---

## License

MIT
