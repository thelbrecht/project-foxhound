# Project "Foxhound" patched for Playwright
[Old README](README_OLD.md)

Applied open-source firefox patch adding Juggler and other changes to support interaction via Playwright with the taint-aware firefox browser. Patch diff is accesible under: [GitHub Playwright Repository](https://github.com/microsoft/playwright/tree/release-1.21/browser_patches/firefox)

## Build instructions
After compiling, run `install-preferences.js` to apply playwright specific configuration options.

## Current Status
- ✅ Currently working with: Playwright v1.21 (JS) on Ubuntu