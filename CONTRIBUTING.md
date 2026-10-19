# Contributing

Thanks for helping improve Codebase X-Ray. Keep changes focused, transparent, and dependency-light.

## Before proposing a change

- Open an issue describing the use case, expected behavior, and a small reproducible example.
- For security-sensitive reports, follow `SECURITY.md` rather than posting exploit details publicly.
- Check existing issues to avoid duplicate work.

## Development

1. Clone the repository and run `python3 -m http.server 8000`.
2. Open `http://localhost:8000` and test both the demo and a small local fixture.
3. Run automated checks with `node --test tests/scanner.test.mjs` (Node.js 18+ recommended).
4. Test exports by opening the downloaded JSON, SVG, and HTML report.
5. Check keyboard access, narrow viewport behavior, and reduced-motion settings.

No package install is required. Keep modules readable and avoid external dependencies, network calls, analytics, or executing scanned code. Include the problem solved, approach, manual test steps, and limitations in pull requests. Update docs when behavior changes. Do not claim language support beyond what is actually implemented.
