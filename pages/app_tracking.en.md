---
title: How Apps are Tracked
description: How Apps are Tracked in Obtainium
---

# How Apps are Tracked

## Basics

When you add an app URL to Obtainium, you must pick an app [source](sources.md). Sources define how app info and APK files will be extracted from the URL you enter. Most of the time, Obtainium will automatically select the appropriate source to use - when this is not possible, an "Override Source" dropdown will be presented.

At minimum, an app source must provide the following data for its apps:

- The app version (or a 'pseudo-version' - an identifier that changes for each new version of the app)
- At least one APK download URL that corresponds to the version that was provided

App sources may also provide other info - these enable extra features or UI benefits. For example:

- The app author's name
- The app's package ID
- The release date of the latest version
- Info for previous versions or variants of the app

In an ideal world, each app source would provide all required info in a straightforward way - with a single app per given URL with all required info provided in a standard format. However this is often not the case - there are many different ways app releases are handled even by the same source, so it isn't possible to have a fixed set of steps to handle them all. For this reason, you are presented with various additional options when adding an app, and these can be used to modify the way app info will be extracted. While the defaults work for most apps, you may want to understand these options to deal with edge cases - more info in the [App Sources](sources.md) section below.

Note: Many filter settings in Obtainium (including many source-specific optional filters) make use of [regular expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) - you should be familiar with these.

## Version Detection

When Obtainium is tracking an app that is currently installed, it grabs the version of the app from Android and compares it to the version string provided by the source. It then compares the two to decide whether an update is available or whether the install status of the app has changed. This comparison can only be made if the two versions follow the same format, which may not always be the case. For example, you could have any of these cases among others:

1. [Obtainium](https://github.com/ImranR98/Obtainium/releases/tag/v0.14.21-beta) from GitHub:

    - **Android-reported app version:** `0.14.21`
    - **Source-reported version:** `v0.14.21-beta` 

2. [Cheogram](https://git.singpolyma.net/cheogram-android/refs/2.12.8-2) from a SourceHut instance:

    - **Android-reported app version:** `2.12.8-2+free`
    - **Source-reported version:** `2.12.8-2`

3. [Tor](https://www.torproject.org/download/) from the Tor website:

    - **Android-reported app version:** `102.2.1-Release (12.5.6)`
    - **Source-reported version:** none (no version string is provided by this HTML source so a hash-based 'pseudo-version' is used instead)

4. [Quotable](https://github.com/Lijukay/Qwotable/releases/tag/v10) from GitHub:

    - **Android-reported app version:** `1`
    - **Source-reported version:** `v10`

Obtainium stores a list of "standard" formats which it uses to make this comparison (like `x.y.z` or `x.y`). If both versions being compared conform to the same format, the comparison will be made. If not, version detection will be disabled for that app. Obtainium also ignores cosmetic differences such as a leading `v` or `-release`/`-debug` suffixes, but pre-release qualifiers such as `beta` remain significant. A few store-based sources use a looser comparison instead. We never try to strip parts off the "real" OS-provided version.

[This part of the code](https://github.com/ImranR98/Obtainium/blob/main/lib/services/version_service.dart) defines how the various "standard" formats are generated and compared; [this file](https://github.com/ImranR98/Obtainium/blob/main/lib/utils/version_normalization.dart) handles cosmetic normalization.

It's always possible to expand that code to add support for more formats, but this requires careful consideration. For example if Android reports that an installed app's version is `1.2` but the source says the latest available version of that app is `1.2-4`, should we strip off the `-4` and say the two are the same (meaning there is no update available)? This may be fine in some contexts (where the `-4` is not actually indicative of a change in the app itself) but not in other contexts. So it wouldn't be a good idea to support that specific case.

Version detection being turned off should not usually have a significant impact on day-to-day use. If version detection is disabled for an app, you may occasionally run into inconsistencies between the real version of the app installed on your system and the version shown in the Obtainium UI. This should only happen in two cases:

1. If an app's version changes due to actions taken outside of Obtainium (for example if it gets updated by Google Play)
2. If an attempt by Obtainium to [silently update](#background-updates) the app in the background fails

In such cases, Obtainium would not be able to detect that the app's real OS version has changed and so it would not update its internal records accordingly - you would need to manually correct the inconsistency.

Several additional per-app options can affect how versions are handled:

- **Reconcile version string with version detected from OS**: Enabled by default. Disable it if version detection causes incorrect results for a specific app.
- **Use Version Code as OS Version**: When enabled, Obtainium will use the Android version code (a number) instead of the version name string when comparing against the source. This can resolve mismatches when the source provides version codes but the OS reports version names, or vice versa.
- **Release Date as Version**: Available for many sources, this toggle treats the release date as a pseudo-version instead of the version string from the source. This is useful when the source does not provide meaningful version information but the release date is reliable.
- **Trim version string with RegEx**: Extracts a version from a longer string. A global version-trimming regex can also be set in Settings → Updates.

See also: [Obtainium Issue #946 Comment](https://github.com/ImranR98/Obtainium/issues/946#issuecomment-1741745587)

## Background Updates

Obtainium checks for app updates in the background on a regular basis. You can control the frequency of these update tasks on the settings page.

Background update checking uses Android's WorkManager. This is battery-efficient but may be delayed by some OEMs' battery optimisation policies; disabling battery optimization for Obtainium can improve reliability.

Background checks and silent installs are controlled separately. The update interval controls when Obtainium checks for new releases, while "Enable background silent installs" controls whether Obtainium may install them silently.

You can restrict background work based on network and charging state. Each restriction has three modes: **Nothing** (skip background work), **Check only**, and **Check and update**.

A minimum update age can be set globally or per app under Settings → Updates to delay or suppress very recent releases.

You can also choose to check for updates every time the app is opened ("Check on start"), and/or every time you view an app's detail page.

### Silent Installation

After a background update checking task is completed, any available updates are divided into 2 categories:

1. Updates that can be applied in the background
2. Updates that cannot be applied in the background

With the default System installer, an update can be installed silently in the background when:

- The OS must be Android 12 or higher
- The app being installed must target a [recent Android API level](https://developer.android.com/reference/android/content/pm/PackageInstaller.SessionParams#setRequireUserAction(int))
- The currently installed version of the app must have been installed by Obtainium
- Background silent installs must be enabled in Obtainium and the app must not be exempted from background updates
- If there are multiple APKs available for the update, the additional options for that app must be configured such that Obtainium can filter these down to one APK

Shizuku (with either the Shizuku or Dhizuku backend) and Root can perform silent installs under their own permission rules, which may avoid some of the System installer's restrictions. The External installer always requires user interaction and cannot install silently.

Each available update is downloaded and installed if possible, and the user is then notified either of the update's availability or that it was installed in the background.

By default, parallel downloads are enabled. You can disable them under Settings → Updates to process updates one at a time, which uses less network bandwidth and system resources.

Note that due to technical limitations, background updates can only be installed on an asynchronous, best-effort basis. Success may only be confirmed the next time Obtainium is opened, and failures may be reported in an aggregated notification.

## Update Health

Settings → Update Health flags apps whose latest release or version is stale, that repeatedly fail update checks, whose source is archived, or whose filters hide newer releases. Detection thresholds can be adjusted, and per-app overrides are available in the app options.
