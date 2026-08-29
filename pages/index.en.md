---
title: Home
---

# ![Obtainium Icon](https://raw.githubusercontent.com/ImranR98/Obtainium/main/assets/graphics/icon_small.png) Obtainium Wiki

---

[![Ceasefire Now](https://badge.techforpalestine.org/default)](https://techforpalestine.org/learn-more)

Get Android app updates straight from the source.

Obtainium's core goal is to automate the process of downloading and installing Android app updates directly from their "source" websites (sites where app files are available for direct download). This process needs automation since users may not be willing or able to rely on an app store to update a given app, but Android apps (unlike PC apps) usually assume they will be updated externally by an app store and therefore don't include a built-in self-update function.

While this concept is simple, the wide variety of supported sources, user preferences, and APK naming, versioning, and distribution methods make things more complicated. This Wiki explains the various app sources and settings available in Obtainium.


## Finding App Configurations

You can find crowdsourced app configurations at [apps.obtainium.imranr.dev](https://apps.obtainium.imranr.dev).

If you can't find the configuration for an app you want, feel free to leave a request on the [discussions page](https://github.com/ImranR98/apps.obtainium.imranr.dev/issues).

Or, contribute some configurations to the website by creating a PR at [this repo](https://github.com/ImranR98/apps.obtainium.imranr.dev).

## Installation

<div style="text-align: center;">
  <a href="https://github.com/ImranR98/Obtainium/releases">
    <img src="https://github.com/machiav3lli/oandbackupx/raw/034b226cea5c1b30eb4f6a6f313e4dadcbb0ece4/badge_github.png" alt="Get it on GitHub">
  </a>
  <a href="https://apt.izzysoft.de/fdroid/index/apk/dev.imranr.obtainium">
    <img src="https://gitlab.com/IzzyOnDroid/repo/-/raw/master/assets/IzzyOnDroid.png" alt="Get it on IzzyOnDroid">
  </a>
  <a href="https://f-droid.org/packages/dev.imranr.obtainium.fdroid/">
    <img src="https://fdroid.gitlab.io/artwork/badge/get-it-on.png" alt="Get it on F-Droid">
  </a>
</div>
     
!!! info "Verification Info"
    - Package ID: `dev.imranr.obtainium`
    - SHA-256 Hash of Signing Certificate: `B3:53:60:1F:6A:1D:5F:D6:60:3A:E2:F5:0B:E8:0C:F3:01:36:7B:86:B6:AB:8B:1F:66:24:3D:A9:6C:D5:73:62`
        - Note: The above signature is also valid for the F-Droid flavour of Obtainium, thanks to [reproducible builds](https://f-droid.org/docs/Reproducible_Builds/). This means the F-Droid APK is bit-for-bit identical to the one built from the same source code, allowing independent verification by a third party you may trust more than the developer.
    - [PGP Public Key](https://keyserver.ubuntu.com/pks/lookup?search=contact%40imranr.dev&fingerprint=on&op=index) (to verify APK hashes)

## In-App Links

You can find a link to this wiki, along with links to the source code and crowdsourced app configurations, in the footer of the Settings page within Obtainium.

## Limitations
- For some sources, data is gathered using Web scraping and can easily break due to changes in website design. In such cases, more reliable methods may be unavailable.
