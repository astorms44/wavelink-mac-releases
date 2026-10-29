# Wavelink Intercom — Mac App Releases

Signed, notarized builds of **Wavelink Mac**, the Wavelink Intercom app for macOS.

**[Download the latest release →](https://github.com/astorms44/wavelink-mac-releases/releases/latest)**

This repository distributes build artifacts only. The Wavelink Intercom source is not public.
Looking for the server? It lives at
[astorms44/wavelink-releases](https://github.com/astorms44/wavelink-releases).

## Requirements

- macOS 26 or later, Apple Silicon or Intel
- A Wavelink Intercom server to sign in to, and a login from its administrator

## Installing

Download the `.dmg`, open it and drag **Wavelink Mac** to Applications. On first launch macOS asks
for microphone access — allow it, or you'll listen but not talk.

Each release also carries a `.pkg`. That's the file the app's own updater installs; you can also
open it by hand or push it with MDM. If the app is running, the installer quits it first and
reopens it afterwards.

## Updates

The app updates itself from this channel. It checks every six hours and tells you when a new
version is out — in the menu-bar dropdown, with a download arrow in the toolbar, and in
**Settings → Updates**, where the release notes sit next to the Update button.

It never installs on its own. **Update** downloads the package, verifies it three ways — SHA-256
against the manifest, the Developer ID Installer signature, and Gatekeeper's notarization verdict —
then asks once for an administrator password. You drop off the intercom for the length of the
install, so update between shows.

## Verifying a download yourself

```
shasum -a 256 WavelinkMac-*.pkg      # compare against mac-manifest.json
pkgutil --check-signature WavelinkMac-*.pkg
spctl -a -t install -vv WavelinkMac-*.pkg
```

Expect `Developer ID Installer: Austin Storms (A8UR75UJ6Q)` and `accepted`. Each release's
`mac-manifest.json` holds the hash.

---

© Austin Storms / Storms Audio. All rights reserved.
