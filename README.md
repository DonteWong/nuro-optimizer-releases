# Nuro Optimizer

A free macOS optimizer from [Sentium Nuro Labs](https://getsentium.com). Sixteen analyzers find what's actually slowing your Mac down — caches, startup items, memory pressure, disk health — then fix it, reversibly, in one click.

🌐 **[optimizer.getsentium.com](https://optimizer.getsentium.com)**
⬇️  **[Download latest](https://github.com/DonteWong/nuro-optimizer-releases/releases/latest/download/Nuro-Optimizer.zip)** — universal (Apple Silicon + Intel), notarized

## What this repo is

This repository hosts:
- The marketing site (`index.html`, `icon.png`, `CNAME`) — deployed via Cloudflare Pages at `optimizer.getsentium.com`
- The notarized binary release artifacts (under [Releases](../../releases))

The Swift source for the app itself lives in a separate private working tree.

## Why Developer ID, not the App Store

Nuro Optimizer needs Full Disk Access, the ability to invoke `launchctl`, read SMART data, manage system caches, and control startup items. All of these are blocked by the App Sandbox required for Mac App Store apps. So we ship via Apple's notarized Developer ID program — same path as CleanMyMac, OnyX, BetterDisplay, and most macOS utilities of substance.

Every release on this page is:
- Built with `-O` optimizations, parsed as a library
- Universal binary (`arm64` + `x86_64`)
- Code-signed with `Developer ID Application: DONTE' MAURICE WONG (B9HPU9TVCR)`
- Hardened Runtime enabled
- Notarized + stapled by Apple
- Verified via `spctl --assess` before publishing

## Privacy

- **No telemetry.** No analytics SDKs, no event tracking, no usage reporting.
- **No accounts.** No sign-in, no email gate, no license keys.
- **No crash reporting.** No third-party crash collectors (Sentry, Crashlytics, Bugsnag, etc.).
- **No license server.** The app is free; there is nothing to check.
- **One outbound network call, and it's optional.** The app uses [Sparkle](https://sparkle-project.org/) to deliver updates. On launch and on a schedule, Sparkle fetches `https://optimizer.getsentium.com/appcast.xml` — a public, unauthenticated XML file that lists available versions. The request sends no information about you or your machine beyond the standard `User-Agent` Sparkle uses. Updates are EdDSA-signed; Sparkle refuses to install anything that doesn't verify against the bundled public key. You can disable automatic checks entirely in *Nuro Optimizer › Settings › Updates*.

Verifiable with `lsof -i -p $(pgrep "Nuro Optimizer")` or Little Snitch. The full privacy policy lives at [optimizer.getsentium.com/privacy.html](https://optimizer.getsentium.com/privacy.html).

## Contact

- 🐛 [Report an issue](../../issues)
- ✉️  [hello@getsentium.com](mailto:hello@getsentium.com)
