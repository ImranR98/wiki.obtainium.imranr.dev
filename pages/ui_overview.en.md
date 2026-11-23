---
title: UI Overview
description: Overview of the Obtainium UI
---

# UI Overview

The Apps page is the main screen. Add App and Settings are opened from it using the add button and the gear icon in the top bar. On tablets and Android TV, the app list and app details can appear side by side.

## Apps Page

This is the main screen; it contains a list of apps being tracked by Obtainium, and provides the basic info for each app.

On this page, you can use the buttons at the bottom of the screen to perform various operations on multiple apps at once. You can do this after selecting one or more apps, either using a long-press to enter multi-select mode or using the "select all" button. Available batch operations include updating, installing, deleting, categorising, pinning/unpinning, sharing app URLs or export links, and marking selected apps as updated.

Apps can be assigned to categories, which are shown as coloured bars on the left edge of each app entry. When "Group by" is enabled in Settings → Appearance, the app list is divided into expandable sections by category or source.

In the detail view for an individual app, you can view the app's version info, release date, changelog, and APK signing certificate hashes (long-press to copy). If a repository rename is detected, a prominent notice will appear with the option to update the app's URL automatically.

You can also filter for specific apps by pressing the filter button. This lets you view only the apps that fulfill specific criteria (like installed/not-installed, latest/outdated, source site, category, etc.).

## Add App Page

This page lets you add an app by its source URL.

As you enter the source URL, Obtainium will automatically detect what [source logic](app_tracking.md/#basics) it should use, and will present the relevant options. If a URL does not correspond to any supported source, the "[HTML](sources.md/#html)" source will be selected as a default. This source is a general fallback that may work in some cases. If you think Obtainium has made the wrong choice, you can manually specify the source type to use.

For most sources, you don't need to be exact with the URL you enter; for example, any GitHub URL that contains the base repo URL would be accepted by the GitHub source (for example, `https://github.com/ImranR98/Obtainium/releases/latest` would automatically be trimmed down to `https://github.com/ImranR98/Obtainium`). However, your URL must be more precise in two situations:

1. When using the HTML source
      - For example, the Tor Android APK is at `https://www.torproject.org/download/` so entering only `https://www.torproject.org/` would not work.
2. When manually picking a source (overriding Obtainium's HTML fallback choice)

This page also lets you search for apps across sources that support this feature. Note that just because an app shows up in the search results does not mean it will be added successfully - it still needs to fulfill all other criteria.

Finally, this page lists all supported sources, along with additional info such as whether a source is searchable.

## Import/Export Page

Import/Export is available from Settings. It lets you export your Obtainium data so that it can be imported later. You can also enable automatic exports that happen whenever any data changes, and control whether secrets (such as API tokens) are included in the export.

This page also provides various other ways of importing large numbers of apps:

- **Obtainium import**: Restore an Obtainium export file.
- **URL list import**: Paste or load a file containing a list of app URLs to import them all at once.
- **Mass source imports**: Import apps from bulk sources like a GitHub user's starred repositories.

Cross-source app search is on the Add App page; it is not part of Import/Export.

## Settings Page

This page provides various UI and behaviour settings, organised into sub-pages:

- **Updates**: Background update interval and manual checks, background silent installs, Wi-Fi/charging constraints, check on start, parallel downloads, certificate pinning, install methods such as Shizuku and Root (with an option to pretend to be Google Play), and Verified Apps integration for verifying APKs before installation.
- **Source Specific**: Credentials for specific sources (e.g. GitHub/GitLab personal access tokens) and other source-specific configuration settings.
- **Appearance**: Theme (system/light/dark), black/dark mode, Material You dynamic colours, custom accent colour, sort order, language override, system font, in-app WebView, grouping by category or source, app-list density, and action-banner settings.
- **Categories**: Categories are managed from the Appearance page and the app detail view.

The About section of the Settings page provides links to the app source, this wiki, and the app logs. The crowdsourced app configurations link is on the Add App page.
