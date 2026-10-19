# Security Policy

## Scope and boundaries

Codebase X-Ray is designed to analyze selected files locally in a browser. It does not upload source files, execute imported code, use analytics, or intentionally make network requests. It is not a hardened security sandbox. The browser, browser extensions, operating system, and user-selected files are outside the application's control.

## Reporting a vulnerability

Please report suspected vulnerabilities privately to the repository owner using GitHub's private vulnerability reporting feature, if enabled. If it is not enabled, contact a repository maintainer through a private channel listed on the repository profile. No contact address is invented or assumed here.

Please include affected version/commit, browser and operating system, impact, reproduction steps, and a minimal proof of concept that does not include secrets or third-party data. Avoid publishing exploitable details before maintainers have had a reasonable chance to investigate.

## Handling source files

Generated reports can contain project paths, filenames, and import specifiers; store and share them accordingly. The app avoids saving source code in localStorage, but browser environment and downloaded exports are outside its control.
