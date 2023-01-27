# Project "Foxhound" patched for Playwright
This repository contains a patched version of Project Foxhound, which enables the engine to be used in combination with Playwright. We applied the open-source firefox patch from Playwright, located in the Playwright project repository. Accesible under: [GitHub Playwright Repository](https://github.com/microsoft/playwright/tree/release-1.21/browser_patches/firefox)

The patch adds Juggler and other changes to support interaction via Playwright with the taint-aware firefox browser. We simply apply the bootstrapped diff file located at [/browser_patches/firefox/patches/bootstrap.diff](https://github.com/microsoft/playwright/blob/11f51455f212c4452ff8b0722f72f473053a868a/browser_patches/firefox/patches/bootstrap.diff). Furthermore, we moved the Juggler files in the foxhound source folder & copyied additional configuration options into the `taintfox_mozconfig_ubuntu` config (the concrete options could be extracted from `BUILD.sh` from the playwright repository).

## Build instructions
The build process is equal to the process for Foxhound, except after compiling we need to use the `install-preferences.js` script to tweak the browser preferences for usage with playwright.
- Make sure to install all build tools using `./mach bootstrap`
- Compile the browser with `./mach build`
- After compiling, run `node install-preferences.js DIST_PATH` to apply playwright specific configuration options, where `DIST_PATH` is the output folder containing the compiled foxhound browser

### Packaging
Just as with foxhound, use `./mach package` to obtain an archive containing the compiled browser for use on other systems.

## Using with Playwright
After installing `playwright@1.21.1` via `npm install`, one can instrument playwright to use the browser in the setup function, when launching a firefox context, e.g. as shown in the following:

```typescript
firefox.launch({ executablePath: "/path/to/bin/foxhound" });
```

## Current Status
- ✅ Currently tested with: Playwright v1.21 (Javascript) on Ubuntu

## More
- The Foxhound README file provides additional details about the patched firefox and build instructions: [Foxhound README](README_OLD.md)
