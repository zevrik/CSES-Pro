# Contributing to CSES Pro

Thank you for considering contributing to **CSES Pro**! Contributions of all kinds—bug fixes, new features, UI improvements, documentation updates, and problem list updates—are welcome.

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v18 or later recommended) and npm
- Google Chrome (or another Chromium-based browser supporting Manifest V3 extensions)

### Local Development Setup

1. **Fork and clone the repository:**

   ```bash
   git clone https://github.com/<your-github-username>/CSES-Pro.git
   cd CSES-Pro
   ```

2. **Install dependencies:**

   ```bash
   npm install
   ```

3. **Build or run in development mode:**

   - Production build (runs TypeScript type-checking and bundles via Vite into `dist/`):
     ```bash
     npm run build
     ```
   - Watch/dev mode with `@crxjs/vite-plugin`:
     ```bash
     npm run dev
     ```

4. **Load the extension in Chrome:**
   - Open `chrome://extensions/`
   - Enable **Developer mode** (top-right toggle)
   - Click **Load unpacked** and select the `dist` directory
   - After rebuilding, click the reload icon on the extension card and refresh your open `cses.fi` tab

## Making Changes

1. Create a descriptive branch from `main`:
   ```bash
   git checkout -b feat/your-feature-name
   ```
   (Use prefixes like `feat/`, `fix/`, `docs/`, or `refactor/`.)
2. Follow the existing TypeScript conventions (`strict` mode in `tsconfig.json`).
3. Ensure every content script continues to export `onExecute()` as required by `@crxjs/vite-plugin`.
4. Keep styling adaptive to both CSES **light** and **dark** themes using relative colors/opacity and `inherit` where appropriate.
5. Do not introduce external network requests, tracking, or telemetry—all user data must remain local in `chrome.storage.local`.

## Testing Your Changes

Before opening a Pull Request, please verify:

- `npm run build` completes with zero TypeScript or Vite errors.
- Test manually on `https://cses.fi/` in both **Light** and **Dark** themes across:
  - Logged-out state (dashboard does not mount; user data stays isolated)
  - `/problemset/` and `/problemset/list/` (dashboard, bookmarks filter, popularity sort, random button)
  - `/problemset/task/<id>` (bookmark toggle, copy buttons on input/output/code blocks, solve detection)
  - `/submit` (paste code mode, upload file mode, language auto-extension)
  - `/user/<username>` (profile progress dashboard injection)

## Submitting a Pull Request

1. Push your branch to your fork.
2. Open a Pull Request against `main` on [zevrik/CSES-Pro](https://github.com/zevrik/CSES-Pro/pulls).
3. Clearly describe:
   - What problem your PR solves or what feature it adds
   - How you tested it (including screenshots/recordings for UI changes)
   - Any related issue numbers (e.g., `Fixes #12`)

## Reporting Issues

Found a bug or have a feature idea? Open an issue at [github.com/zevrik/CSES-Pro/issues](https://github.com/zevrik/CSES-Pro/issues) with clear reproduction steps, browser/OS details, and screenshots if relevant.

## Code of Conduct

Please note that this project follows our [Code of Conduct](CODE_OF_CONDUCT.md). By participating, you agree to uphold it.

