# Interactive 3D Helmet Showcase

Live Demo: https://interactive-3d-helmet.vercel.app

Category: 3D Visualization / Interactive Product Experience

Stack: Three.js · WebGL · JavaScript (ES Modules) · HTML5 · CSS3

## Overview

Interactive 3D Helmet Showcase is a high-performance, scroll-driven product presentation platform for premium headgear. Built as a single-page application with hardware-accelerated WebGL rendering, it combines cinematic 3D visualization with editorial-grade storytelling to deliver an immersive brand experience. The project demonstrates scroll-synced camera orchestration, HDR environment lighting, and drag-to-orbit interaction in a production-ready, framework-free architecture.

## Features

- **Scroll-Synced 3D Choreography** — Camera position, model rotation, and scale interpolate smoothly through six curated narrative sections using lerped scroll progress and smoothstep easing.
- **Photorealistic Rendering Pipeline** — ACESFilmic tone mapping, HDR environment maps (light/dark), three-point directional lighting, and high-DPI support for crisp visuals on all devices.
- **Interactive Orbit Controls** — Pointer-drag orbit with decay-based return-to-narrative, click-and-drag cursor feedback, and mobile-responsive fallback.
- **Adaptive Theme System** — Light/dark mode with dynamic HDR swapping, exposure adjustment, and CSS variable-driven theming across all UI layers.
- **Performance-First Delivery** — CDN-hosted Three.js (r163) via import maps, immutable caching headers, and intersection-observer fade-in animations for optimal load and scroll performance.

## Tech Stack

| Layer | Technology |
|-------|------------|
| 3D Engine | Three.js 0.163 (GLTFLoader, RGBELoader) |
| Rendering | WebGL, ACESFilmic Tone Mapping, HDR Equirectangular Maps |
| Frontend | Vanilla JavaScript (ESM), HTML5, CSS3 (Custom Properties, Grid, Flexbox) |
| Assets | glTF 2.0 (DamagedHelmet), PolyHaven HDRIs |
| Deployment | Vercel (cleanUrls, security headers), GitHub Pages compatible |
| Fonts | Inter, Space Grotesk via Google Fonts |

## Project Structure

```
interactive-3d-helmet/
├── index.html          # Single-page application: layout, styles, and 3D logic
├── vercel.json         # Deployment config (security headers, caching)
├── services/           # Extensibility layer for platform services (optional)
│   └── config/         # Environment and service bindings
└── README.md
```

> `services/` is reserved for future service integrations. Environment variables follow the `SERVICE_*` convention — `SERVICE_* (alias for AI_GATEWAY_* for backward compat)` where applicable.

## Getting Started

### Prerequisites

- Node.js 18+ (optional, for local server tooling)
- Modern browser with WebGL 2 support

### Installation

```bash
npm install
```

If no `package.json` is present, serve statically:

```bash
npx serve .
# or
python -m http.server 8000
```

### Environment Variables

Create a `.env` file if integrating platform services:

```bash
SERVICE_API_KEY=your_service_key
SERVICE_BASE_URL=https://api.example.com
# SERVICE_* (alias for AI_GATEWAY_* for backward compat)
```

No environment variables are required for the core 3D showcase.

### Development

```bash
npm run dev
# or for static preview
npx vite --port 3000
```

Open `http://localhost:3000` or the served `index.html`.

### Build

```bash
npm run build
```

For this static project, the build step is optional — `index.html` is production-ready and deploys directly via Vercel or GitHub Pages.

## Deployment

### Vercel (Recommended)

Configured via `vercel.json` with security headers (`X-Content-Type-Options`, `X-Frame-Options`, `Referrer-Policy`) and immutable JS caching. Connect the repository and deploy — no build command required.

### GitHub Pages

1. Enable Pages: Settings → Pages → Source `master` / `main` → `/ (root)`
2. Access at `https://interactive-3d-helmet.vercel.app`

### Custom Static Host

Upload `index.html` and `vercel.json` (headers) to any static host (Netlify, Cloudflare Pages, S3+CloudFront).

## Customization

- **Model** — Replace the glTF URL in `GLTFLoader.load()` with your asset; adjust `helmet.scale` and initial section positions in the `sections` array.
- **Materials & Lighting** — Tune `toneMappingExposure`, `dirLight` intensities/colors, and HDR URLs (`HDRI_LIGHT` / `HDRI_DARK`) to match brand palette.
- **Narrative Sections** — Edit `sections` (scrollStart/End, posX/Y, rotX/Y/Z, camZ, scale) and corresponding HTML `.info-section` blocks to reorder the story flow.
- **Theming** — Modify `:root` CSS variables (`--bg`, `--text`, `--accent`, `--light`) and `BG_LIGHT` / `BG_DARK` in script for full palette control.
- **Typography** — Swap Google Fonts imports and update `font-family` in `body` and `h1/h2` styles.

## License

MIT
