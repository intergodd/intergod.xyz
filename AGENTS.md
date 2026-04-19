# Repository Guidelines

## Project Structure & Module Organization

This is a Svelte 4 application built with Vite. Application code lives in `src/`: `main.js` mounts the app, `App.svelte` contains the main page, and `LoadingScreen.svelte` handles the entry overlay. Static assets are served from `static/` and include SVG icons, cursor images, audio, and background video. Build output goes to `dist/` and should not be edited manually. GitHub Pages deployment is configured in `.github/workflows/deploy.yml`; the custom domain is in `CNAME`.

## Build, Test, and Development Commands

- `npm ci`: install dependencies from `package-lock.json`; use this for clean local or CI installs.
- `npm run dev`: start the Vite development server.
- `npm run build`: create a production build in `dist/`.
- `npm run preview`: serve the production build locally for final checks.

The GitHub Pages workflow runs on pushes to `main`, builds the app, adds `dist/.nojekyll`, and deploys `dist/`.

## Coding Style & Naming Conventions

Use Svelte single-file components with `<script>`, markup, and `<style>` sections. Follow the existing JavaScript style: two-space indentation, semicolons, single quotes, and descriptive camelCase names (`showNotification`, `audioProgress`, `contextMenuOpen`). Name Svelte components in PascalCase, such as `LoadingScreen.svelte`. Keep assets lowercase and descriptive in `static/`.

Prefer small, direct functions. Keep UI text and links near related state arrays, as shown by `links`, `contextMenuItems`, and `spotlightItems`.

## Testing Guidelines

No automated test framework is currently configured. Before submitting changes, run `npm run build` and manually verify with `npm run dev` or `npm run preview`. For UI changes, check desktop and mobile widths, loading behavior, audio controls, custom cursor, context menu, Spotlight search, and external links.

If tests are added later, place them near the related source files or in a clear `tests/` directory, and add an `npm test` script to `package.json`.

## Commit & Pull Request Guidelines

The existing history uses short, informal commit messages. Prefer concise imperative messages going forward, for example `Add audio progress controls` or `Fix mobile loading overlay`.

Pull requests should include a short description, user-visible impact, verification steps, and screenshots or recordings for visual changes. Link related issues when available. Do not commit `node_modules/`, `dist/`, local environment files, or generated cache files.

## Security & Configuration Tips

Keep secrets out of the repository. Public links and static assets are client-visible, so do not place tokens or API keys in Svelte components, `static/`, or Vite config. Validate changes to `CNAME`, workflow permissions, and external URLs before merging.
