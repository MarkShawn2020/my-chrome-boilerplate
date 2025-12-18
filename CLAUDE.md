# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
# Development (HMR enabled)
pnpm dev              # Chrome
pnpm dev:firefox      # Firefox

# Build
pnpm build            # Chrome
pnpm build:firefox    # Firefox

# Lint & Format
pnpm lint             # Run ESLint
pnpm lint:fix         # Fix ESLint issues
pnpm format           # Run Prettier
pnpm type-check       # TypeScript check

# E2E Tests (WebdriverIO)
pnpm e2e              # Run e2e tests (builds & zips first)

# Package for distribution
pnpm zip              # Build and create zip

# Module management
pnpm module-manager   # Interactive CLI to enable/disable pages

# Install dependencies
pnpm i <pkg> -w       # Root workspace
pnpm i <pkg> -F <mod> # Specific module (e.g., -F popup)

# Version update
pnpm update-version <version>
```

## Architecture

Turborepo monorepo for Chrome/Firefox extension development using React + TypeScript + Vite.

### Directory Structure

- **chrome-extension/** - Core extension: `manifest.ts`, background service worker, icons
- **pages/** - Extension UI pages (each builds independently):
  - `popup`, `options`, `new-tab`, `side-panel` - Standard extension pages
  - `content`, `content-ui`, `content-runtime` - Content scripts injected into web pages
  - `devtools`, `devtools-panel` - DevTools integration
- **packages/** - Shared code:
  - `@extension/shared` - Types, constants, hooks, components
  - `@extension/storage` - Chrome storage helpers
  - `@extension/ui` - Shared UI components with Tailwind
  - `@extension/i18n` - Type-safe internationalization
  - `@extension/env` - Environment variables
  - `@extension/hmr` - Hot module reload plugin
  - `@extension/vite-config` - Shared Vite configuration
  - `@extension/tailwindcss-config` - Shared Tailwind config

### Key Patterns

- All env vars must have `CEB_` prefix (or `CLI_CEB_` for CLI args)
- Each page has its own `tailwind.config.ts` extending the shared config
- Content scripts output as IIFE bundles (`*.iife.js`)
- Manifest is generated from `chrome-extension/manifest.ts`
- Use `pnpm module-manager` to delete/recover pages you don't need
