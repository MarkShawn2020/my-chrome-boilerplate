<p align="center">
  <img src="docs/images/cover.png" alt="Chrome Extension Boilerplate Cover" width="100%">
</p>

<h1 align="center">
  <img src="assets/logo.svg" width="32" height="32" alt="Logo" align="top">
  Chrome Extension Boilerplate
</h1>

<p align="center">
  <strong>Modern browser extension development with React, TypeScript, and Vite</strong><br>
  <sub>Chrome &bull; Firefox &bull; Manifest V3</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black" alt="React">
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript">
  <img src="https://badges.aleen42.com/src/vitejs.svg" alt="Vite">
</p>

---

## Features

- **React 19** with TypeScript
- **Vite** + **Turborepo** for fast builds
- **Tailwind CSS** for styling
- **Hot Module Reload** during development
- **Manifest V3** support
- **Chrome & Firefox** compatible
- **Type-safe i18n** package
- **E2E testing** with WebdriverIO

## Quick Start

```bash
# Install dependencies
pnpm install

# Development (with HMR)
pnpm dev          # Chrome
pnpm dev:firefox  # Firefox

# Production build
pnpm build
pnpm build:firefox
```

### Load Extension

**Chrome:**
1. Open `chrome://extensions`
2. Enable **Developer mode**
3. Click **Load unpacked** → select `dist` folder

**Firefox:**
1. Open `about:debugging#/runtime/this-firefox`
2. Click **Load Temporary Add-on** → select `dist/manifest.json`

## Project Structure

```
├── chrome-extension/     # Manifest, background script, icons
├── pages/                # Extension UI pages
│   ├── popup/            # Toolbar popup
│   ├── options/          # Options page
│   ├── new-tab/          # New tab override
│   ├── side-panel/       # Side panel (Chrome 114+)
│   ├── content/          # Content scripts
│   ├── content-ui/       # Injected React components
│   ├── content-runtime/  # Runtime-injected scripts
│   └── devtools*/        # DevTools integration
└── packages/             # Shared code
    ├── ui/               # UI components
    ├── storage/          # Chrome storage helpers
    ├── i18n/             # Internationalization
    ├── env/              # Environment variables
    └── ...
```

## Commands

| Command | Description |
|---------|-------------|
| `pnpm dev` | Start dev server with HMR |
| `pnpm build` | Production build |
| `pnpm zip` | Build and create distribution zip |
| `pnpm lint` | Run ESLint |
| `pnpm type-check` | TypeScript check |
| `pnpm e2e` | Run E2E tests |
| `pnpm module-manager` | Enable/disable pages |

## Install Dependencies

```bash
# Root workspace
pnpm i <package> -w

# Specific module
pnpm i <package> -F <module>  # e.g., -F popup
```

## Environment Variables

All env vars must have `CEB_` prefix. See [packages/env/README.md](packages/env/README.md).

## Disable Unused Modules

Use `pnpm module-manager` to remove pages you don't need. See [module-manager docs](packages/module-manager/README.md).

## License

MIT

---

Based on [chrome-extension-boilerplate-react-vite](https://github.com/Jonghakseo/chrome-extension-boilerplate-react-vite)
