---
title: App Sources
description: Information specific to certain sources
---

# App Sources

The way that an app is added, checked for updates, and installs will vary depending on source and the settings configured for that app by the user.

The following options are available for all apps regardless of source:

- Track-Only: Enabling this toggle allows you to receive update notifications for apps without attempting to actually download their APKs. This is useful to track updates for apps where no APKs are available, or where they cannot easily be extracted by Obtainium. Some sources are exclusively track-only - for example [ApkMirror](#apkmirror). Note that [version detection](app_tracking.md/#version-detection) will not work for any apps added as track-only.
- Version Detection: See the section on [version detection](app_tracking.md/#version-detection).
- Filter APKs by Regular Expression: When more than one APK is available for an app release, the user is prompted to pick one manually. Aside from being inconvenient, this means the app will not be updated silently in the background even when doing so would have otherwise been possible. This option lets the user specify a regular expression that can be used to filter out APK that don't match it (ideally down to one option).
- Attempt to filter APKs by CPU architecture if possible: This toggle will tell Obtainium to automatically filter out any APKs that don't appear to be compatible with the user's device. The logic used to do this is very simple and is based on the APK filename, so it is not always reliable and the user may still need to do their own filtering in many cases.
- App Name: This allows the user to specify their own name for the app instead of using the one Obtainium extracts.
- Exempt from background updates: This toggle will prevent the app from being updated silently in the background even if background updates are enabled and this app would otherwise have fulfilled all criteria to be updated in the background.
- Skip update notifications: This toggle tells Obtainium to avoid notifying the user that this app has an update available or that it was updated in the background.

Aside from those, each app has additional source-specific options. Most of those are self-explanatory and may be updated frequently, so they are not covered in this Wiki. However, some sources do have more unique behaviours that need more explanation, and these are covered below.

## Currently supported App sources

- Open Source - General:
    - [GitHub](https://github.com/)
    - [GitLab](https://gitlab.com/)
    - [Codeberg](https://codeberg.org/) (Forgejo)
    - [F-Droid](https://f-droid.org/)
    - Third Party F-Droid Repos
    - [IzzyOnDroid](https://android.izzysoft.de/)
    - [SourceHut](https://git.sr.ht/)
- Other - General:
    - [APKPure](https://apkpure.net/)
    - [Aptoide](https://aptoide.com/)
    - [Uptodown](https://uptodown.com/)
    - [itch.io](https://itch.io/)
    - [Huawei AppGallery](https://appgallery.huawei.com/)
    - [Tencent App Store](https://sj.qq.com/)
    - [Vivo App Store](https://h5appstore.vivo.com.cn/)
    - [RuStore](https://rustore.ru/)
    - [Apk4Free](https://apk4free.net/)
    - [CoolAPK](https://www.coolapk.com/)
    - [Farsroid](https://farsroid.com/)
    - [LiteAPKs](https://liteapks.com/)
    - Jenkins Jobs
    - [APKMirror](https://apkmirror.com/) (Track-Only)
    - [RockMods](https://rockmods.net/) (Track-Only)
- App-Specific:
    - [Telegram App](https://telegram.org)
    - [Neutron Code](https://neutroncode.com)
- Direct APK Link
- "HTML" (Fallback): Any other URL that returns an HTML page with links to APK files

## GitHub

GitHub puts a cap on the number of API requests you can make in a given period of time. Since Obtainium uses the GitHub API to grab release info, you may run into a "rate limit" error if you have more than a few dozen GitHub apps. You can get around this by getting a Personal Access Token.

GitHub also allows developers to host multiple releases of their app. This usually means older versions of the same app, but may also include pre-releases, variants, etc. - so Obtainium provides various filters that let you navigate this and grab the exact releases you are interested in.

Some additional options have less obvious behaviour:

- **Verify Latest Tag**: When enabled, Obtainium will pick the release that the developer has marked as "latest" rather than the one that is chronologically the most recent. The two are usually the same but may differ in some cases. This comes at the cost of making an extra API call to GitHub (leading to rate limits more quickly).
- **Sort Method**: Controls how releases are sorted when multiple are available. By default, releases are sorted by date, but "smart name" sorting attempts to infer version order from release titles, and "name" sorting uses strict alphanumeric ordering. The "smart name with date fallback" option uses name-based sorting but falls back to date-based sorting when names cannot be compared.
- **Use Latest Asset Date as Release Date**: When enabled, the release date shown will reflect the date of the most recently uploaded asset within a release rather than the release's own publication date.
- **Check for Repo Rename**: If enabled, Obtainium will detect when a repository has been renamed and prompt you to update the app's URL accordingly.

You can also provide a **GitHub Proxy Prefix** (e.g. `gh-proxy.com`) in the source-specific settings. When set, all GitHub API requests will be routed through that proxy, which can help with rate limiting or accessibility issues in some regions.

The GitHub source supports **search** and lets you filter results by a minimum star count.

### Creating a GitHub Personal Access Token

1. Login to [GitHub](https://github.com).

2. Go to the [Fine-grained tokens](https://github.com/settings/personal-access-tokens) section in developer settings.

3. Select **Generate new token**.

4. Give your token name and set an expiry date.

5. Scroll to the bottom and select **Generate token**.

6. Copy the token and paste it into the Obtainium settings. Make sure to copy your token now as you will not be able to see it again.

## GitLab

GitLab releases sometimes contain APKs that are attached in non-standard ways, such that Obtainium cannot get to them easily. The GitLab API provides a far more reliable way to extract APKs but it cannot be used without an API key. While this shouldn't be an issue for most GitLab repos, you can add your own Personal Access Token in Obtainium's settings for more reliable APK extraction in edge cases where it does turn out to be a problem.

Just like GitHub, GitLab also allows developers to host older releases of the same app, so additional options are provided as appropriate.

### Creating a GitLab Personal Access Token


1. Login to [GitLab](https://gitlab.com).

2. Go to the [personal access tokens](https://gitlab.com/-/user_settings/personal_access_tokens) section in settings.

3. Select **Add new token**.

4. Give your token name and set an expiration date.

5. Tick the `read_api` box.

6. Scroll to the bottom and select **Create personal access token**.

7. Copy the token and paste it into the Obtainium settings. Make sure to copy your token now as you will not be able to see it again.

!!! info "When is this needed?"
    See [this explanation](https://github.com/ImranR98/Obtainium/issues/3#issuecomment-1234695412) about non-standard APK attachments in GitLab releases


## F-Droid Third Party Repo

Unlike with most other sources, F-Droid repos contain info about multiple apps all under the same URL. This means that, in addition to the repo URL, you must provide the name or ID of the app you want separately in the "App ID or Name" field. If you're not sure what apps are available in a given repo, you can use the "Search Source" button on the [Import/Export page](ui_overview.md/#importexport-page) to find out.

Note that Obtainium cannot automatically tell that a given URL points to a third-party F-Droid repo. This means that by default, adding a third-party F-Droid repo to Obtainium will result in the incorrect use of the [HTML source](#html) (a fallback source Obtainium uses for any URL it does not recognize). You must manually select "F-Droid Third Party Repo" from the "Override Source" dropdown to get around this.

The additional version selection options have distinct behaviour:

- **Try Selecting Suggested Version Code**: Obtainium will attempt to use the version code that the F-Droid repo has marked as the suggested/current version. This is the default and works well for most repos.
- **Auto-Select Highest Version Code**: Instead of the suggested version, Obtainium will select the release with the highest version code number from the repo. This can be useful if the repo does not properly mark a suggested version, or if you want to ensure you always get the numerically highest version available.

## APKMirror

APKMirror is a "Track-Only" source. This means that while you can add an APKMirror URL to Obtainium for update notifications, you will not be able to actually download and install the app. This is because the maintainers of APKMirror do not allow it (see [issue #44](https://github.com/ImranR98/Obtainium/issues/44)).

## HTML

The 'HTML' source is a fallback option for any app sources that are not explicitly supported by Obtainium. Because of its flexibility, it is also a way of supporting niche, less popular sources without bloating the app.

The HTML Source works in this way:

1. It sends a request to the source URL provided by the user, and parses the response as HTML. It then looks for links on the page.
2. It filters out certain links. By default, this is any link that doesn't end in `.apk` but you can use "Custom APK Link Filter" to specify your own filter.
3. It sorts the remaining links. This sorting is alphanumeric sorting on the whole link, but you can choose to sort by only the last segment of the link. This last segment is usually the filename but may not be if you used your own filter in step 2.
4. It applies yet another optional user-defined filter on all remaining links. The difference between this filter and the one from step 2 is that this one is a more general filter that all Sources have - it is inherited from the parent `AppSource` class (the APK filter option described in [App Sources](#app-sources)). It's probably easier to use this in some situations rather than having a single more complicated regular expression in step 2 (see [this comment](https://github.com/ImranR98/Obtainium/issues/954#issuecomment-1745977857) for an example). It is also useful when used in combination with the intermediate link option.
5. Of the remaining links, it picks the first one (or the last one if you enabled the reverse option).
6. Now that we have the final APK link, we need a unique release ID to go with it so that when the ID changes, we know the app has an update available. For other Sources, the unique release ID is the app version, but for the HTML Source, it might not be possible to extract a version string. By default, this is just a hash of the link. There are three pseudo-versioning methods available:
    - **Partial APK Hash** (default): A hash of a portion of the APK file itself. This is more reliable than the URL hash because it depends on the file content, not the URL, but requires downloading part of the APK to compute.
    - **APK Link Hash**: A hash of the APK download URL. This changes whenever the URL changes.
    - **ETag**: Uses the HTTP ETag header from the APK download response. This can be useful when the server provides stable ETags but the download URL itself does not change between versions.
    - Additionally, links often have version strings embedded within them. Obtainium can't know how to extract these on its own (different websites would have different ways of doing it), so the user can choose to specify a regular expression that can be applied to the link in order to extract the version - this is what the "Version Extraction" field is for.
    - But often it can be difficult to come up with a regular expression that accurately matches the version while excluding extra characters. For this, we have the "Match Group" option that lets the user specify which group in the regular expression we should use as a version.
    - There is also a "Version Extract Whole Page" toggle. When enabled, Obtainium will attempt to find a version string anywhere on the HTML page rather than just in the link URL. This is useful when the version is displayed on the page but not embedded in the download link.
    - The version extraction feature isn't really necessary - using link hashes is easier and more reliable. Some users might just want it since having the real version looks nicer/more accurate and it allows Obtainium, in most cases, to use [version detection](app_tracking.md/#version-detection).

You can also set **custom request headers** for the HTML source. This allows you to override the default headers (e.g. User-Agent) when the target website requires specific headers to serve the APK correctly.

As for the **Intermediate Link** filter, if this is used (see [issue #820](https://github.com/ImranR98/Obtainium/issues/820) for a situation where this is useful), the HTML source adds a preliminary step before the normal process:

1. It looks for links on an initial HTML page.
2. It filters out any links that don't match the intermediate link filter.
3. It grabs the first remaining link and then feeds that link as the input for the normal HTML Source process described above.

The intermediate link step has its own sub-options for controlling how links are filtered and sorted:

- **Auto Filter by Architecture**: Automatically filters intermediate links by CPU architecture if detectable from the link text.
- **Filter by Link Text**: When enabled, the intermediate link filter regex is applied to the visible link text rather than the URL itself.
- **Match Links Outside `<a>` Tags**: Also matches links that appear outside of standard anchor tags (e.g. in JavaScript data structures embedded in the page).
- **Skip Sorting / Reverse Sort / Sort by Last Link Segment**: These control how intermediate links are ordered before picking the first one.

## Notes for Various Other Sources

- HTML: The HTML source includes default request headers that should be appropriate for most sites. In some cases (for example [SourceForge](https://sourceforge.net/)), you may need to delete them (and possibly specify your own).
- Codeberg: This source is almost identical to GitHub in its additional options and also supports search.
- F-Droid: Any app from F-Droid is likely to be [signed](https://developer.android.com/studio/publish/app-signing) with a different key than releases of the same app from other sources. This means that trying to update from an F-Droid release of a given app to a release from another source (for example GitHub) is likely to fail.
- Tencent App Store: APKs from this source may be of pure 32-bit ([armeabi-v7a](https://developer.android.com/ndk/guides/abis#v7a)) architecture and cannot be installed on some devices using newer Arm architecture SoCs.
- Any source that does not have a specific host associated with it (like [third-party F-Droid repos](#f-droid-third-party-repo), Jenkins instances, and SourceHut instances) will not be automatically recognized by Obtainium. You must manually pick the right source from the "Override Source" dropdown.
- Some sources (like APKPure) may provide [XAPK files](https://apkpure.com/xapk.html) instead of APK files. Obtainium's XAPK support is incomplete and may not work reliably.
