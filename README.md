# Borneo-IoT Web Flasher

Web-based firmware flasher for ESP devices, built with React + TypeScript + Vite and powered by [`esp-web-tools`](https://github.com/esphome/esp-web-tools).

This project lets users connect supported devices over Web Serial, choose a firmware manifest, and flash directly from the browser.

## Features

- Device firmware selection from a manifest list (`/public/firmware/manifests.json`)
- Browser-based flashing through `esp-web-install-button`
- Clear unsupported-browser and permission warnings
- Material UI based interface
- Auto-injected app version from `package.json`

## Tech Stack

- React 19
- TypeScript
- Vite
- Material UI
- TSyringe + reflect-metadata

## Requirements

- Node.js (current LTS recommended)
- npm
- A Web Serial compatible browser (Chrome/Edge)

## Local Development

Install dependencies:

```bash
npm install
```

Start development server:

```bash
npm run dev
```

## Build & Quality Checks

Lint:

```bash
npm run lint
```

Production build:

```bash
npm run build
```

Preview build:

```bash
npm run preview
```

## Firmware Assets

- Firmware files and manifest files are served from `/public/firmware/`.
- In CI/CD, release assets are downloaded from `borneo-iot/borneo` tag `release-fw-latest`.
- Supported downloaded assets include:
  - `manifests.json`
  - `*.bin`
  - `*.bin.gz`
  - `*.manifest.json`

## Deployment Workflows

- `deploy.yml`: builds the site and deploys to GitHub Pages on `master` push or manual dispatch.
- `check-manifests.yml`: daily check that compares remote and release manifests, then triggers deployment if content changed.

## Project Structure

```text
src/
  App.tsx          Main UI and flashing flow
  main.tsx         Application bootstrap and theme setup
  types.d.ts       Custom JSX and global version typing
public/
  firmware/        Firmware binaries and manifests
.github/workflows/
  deploy.yml
  check-manifests.yml
```
