<p align="center"><img src="../assets/accent-picker.jpg" alt="Accent Picker: official Vetri Desktop plugin" width="100%"></p>

# Accent Picker — Vetri Desktop plugin

> Part of [Hermes Official Plugins](../README.md), Nous Research's official plugins for Hermes Agent. Formerly [`NousResearch/hermes-desktop-accent-picker`](https://github.com/NousResearch/hermes-desktop-accent-picker), which is archived; this directory carries its full history.

An OKLCH colour wheel in the Vetri Desktop status bar. Drag it and the whole
theme retints live; the palette re-derives from the one colour you pick. It is
an **authoring tool** for theme designers — the colour is scratch state and is
never persisted. Two palette commands come with it: *Accent: reset to the theme
default* and *Accent: copy the current color*.

It used to ship bundled with the app (off by default). It now lives here as a
desktop plugin so the app's plugin list only carries things most
users want.

## Install

From the Hermes plugin catalog: Vetri Desktop → **Capabilities → Plugins**, search **accent-picker**, install. Or from a terminal:

```bash
vetri plugins install accent-picker
```

The app copies `desktop/plugin.js` into `~/.vetri/desktop-plugins/` and loads it within a few seconds; flip the switch in Capabilities → Plugins to enable it.

## Layout

- `desktop/plugin.js` — the loadable artifact. Plain ESM, only imports
  `@vetri/plugin-sdk`, `react`, and `react/jsx-runtime` (the three specifiers
  the desktop plugin loader resolves).
- `src/plugin.tsx`, `src/picker.tsx` — the TSX source it is built from.
- `plugin.yaml` — the manifest the catalog and `vetri plugins` read.

## Build

```bash
npm install
npm run build   # esbuild src/plugin.tsx → desktop/plugin.js
```

Commit the rebuilt `desktop/plugin.js`; the desktop loads files uncompiled, so the
artifact is what ships.

## SDK

Everything the picker uses comes from `@vetri/plugin-sdk`: `$accentOverride`,
`setAccentOverride`, the OKLCH helpers (`hexToOklch`, `oklchToHex`,
`oklchToSrgb255`, `maxChroma`, `contrastRatio`), `Popover*`, `useTheme`,
`useValue`, `STATUSBAR_AREAS`, `PALETTE_AREA`. Reference:
https://pugazh342.github.io/Agent-Vetri/docs/developer-guide/desktop-plugin-sdk

MIT.
