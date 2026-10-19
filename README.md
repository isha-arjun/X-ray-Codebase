# Codebase X-Ray

**Understand any project. See how everything connects.**

Codebase X-Ray is a local-first, static web app for exploring project structure, inspecting source as text, and visualizing dependency references its conservative scanner can recognize. It uses vanilla HTML, CSS, and JavaScript modules; there is no build step, backend, API key, account, or runtime dependency.

## Features

- Load a built-in sample or select a local folder / multiple files.
- Search and filter the file tree; switch between tree and flat-list views.
- Explore an interactive SVG dependency graph with selection, panning, zoom, fit, and connected-file isolation.
- Inspect file type, size, incoming references, local references, external imports, unresolved paths, and a text-only source preview.
- Export a JSON analysis report, standalone SVG graph, or offline HTML report.
- See skipped files and scanner limitations; reset to clear project data held by the app.
- Responsive layout, keyboard focus states, reduced-motion support, and no external scripts or analytics.

## Screenshots

No screenshots are bundled. To capture genuine screenshots, run the app, load the demo, and capture the welcome screen and explorer with a selected file. Save them in a `screenshots/` directory and update this section with relative image paths if you choose to include them.

## Run locally

Because the app uses ES modules, serve the folder over HTTP rather than opening `index.html` directly.

```sh
python3 -m http.server 8000
```

Then visit `http://localhost:8000`. Any simple static server works; no install step is required.

## Supported analysis and limits

- **JavaScript-like files** (`.js`, `.mjs`, `.cjs`, `.jsx`, `.ts`, `.tsx`): conservative pattern matching for static `import`, `export … from`, literal dynamic `import()`, and literal `require()`. This is not a full JavaScript parser; comments, aliases, template strings, and complex syntax can cause misses or false positives.
- **HTML** (`.html`, `.htm`, `.svg`): recognizes selected `script`, `link`, image/media and related `src` / `href` attributes.
- **CSS** (`.css`): recognizes `url()` and `@import`.
- **JSON** (`.json`): validates syntax and reports parse errors; it does not infer arbitrary relationships from JSON.
- **Local resolution** follows relative paths and tries exact paths, a limited list of common extensions, and common `index.*` candidates. Bare imports are reported as external; aliases, package metadata, framework conventions, and runtime-generated paths are not resolved.
- Common generated/dependency directories (`.git`, `node_modules`, `dist`, `build`, `coverage`, `.next`) are skipped by default. Limits are 2,000 files, 1 MiB per file, and 20 MiB total readable content. Large and known binary files are listed as skipped/unsupported rather than previewed.
- The UI and exports label output as recognized references, not a complete dependency graph.

## Privacy and security

Selected files are processed in the browser and are not uploaded by this app. No analytics, telemetry, tracking pixels, remote scripts, or external fonts are used. Source content is kept in memory while the page is open and is not saved to `localStorage`. Imported project code is never executed. File contents and names are treated as untrusted text, including in reports and SVG export.

This is not a security sandbox. Browser extensions, the browser itself, the operating system, and user-selected files are outside the app's control. See [SECURITY.md](./SECURITY.md).

## Keyboard and navigation

- `/` focuses file search when focus is not already in a text field.
- `Tab` / `Shift+Tab` moves through controls.
- `Enter` or `Space` selects a focused graph node.
- Click or tap a graph node to select it; drag the graph background to pan; use `+`, `−`, and `Fit` controls or the wheel to zoom.
- Use the file list as an accessible alternative to the graph.

## Roadmap

Implemented now: local scan, tree/list browsing, supported reference detection, SVG graph, inspector, filters/search, exports, demo, and static checks.

Possible future work: parser-backed language analysis, configurable ignore rules, improved graph layout for very large projects, keyboard graph traversal, drag-and-drop, and richer configuration-specific diagnostics. These are ideas, not current features.

## Contributing

Read [CONTRIBUTING.md](./CONTRIBUTING.md) before opening a pull request. Community expectations are in [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md). This repository includes an MIT license in [LICENSE](./LICENSE).
