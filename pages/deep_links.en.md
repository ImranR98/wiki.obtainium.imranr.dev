# Deep Links

Obtainium registers the `obtainium://` URI scheme. Any app, website, or QR code can hand it a
link and skip the manual "open Obtainium, tap Add, paste a URL" flow. There are three actions.

## Add a single app

```
obtainium://add/<url>
```

or, equivalently:

```
obtainium://add?url=<url>
```

Pre-fills the Add App screen with `<url>` as the source, the same as pasting it in by hand. If
Obtainium is already tracking an app with that exact URL, the link opens that app's page instead
of the Add screen.

## Import a full config

```
obtainium://app/<url-encoded JSON>
obtainium://apps/<url-encoded JSON array>
```

`app` takes a single app config object; `apps` takes a JSON array of them, for a bulk import in
one link. This is the same object shape used by app export/import and by the
[crowdsourced directory](https://apps.obtainium.imranr.dev)'s configs, at minimum:

```json
{"id": "com.example.app", "url": "https://github.com/example/app", "author": "example", "name": "Example App"}
```

Tapping the link shows a confirmation dialog with the raw JSON before anything is added, so this
is one tap plus one confirm, not a silent install. `additionalSettings` and every other field a
config supports work the same as anywhere else a config can be pasted in. The `id` is only a
bookkeeping key on the installing device; it does not need to be registered anywhere.

## Trigger an update check

```
obtainium://refresh
obtainium://refresh?id=<app id>
```

Checks every tracked app for updates, or just one app if `id` is given.

## Badging your project

Because `obtainium://app/` takes a full config, a project can put a "Get it on Obtainium" badge on
its own README or download page, no listing in the
[crowdsourced directory](https://apps.obtainium.imranr.dev) required.

**Get the badge.** Copy `assets/graphics/badge_obtainium.png` from
[the main repo](https://github.com/ImranR98/Obtainium/tree/main/assets/graphics) and host it
yourself rather than hotlinking `raw.githubusercontent.com`, which GitHub does not guarantee for
that use and can rate-limit. The file ships with transparent padding; most projects trim it and
display it around 161x48 (its 3.36:1 aspect ratio).

**Pick a link form.** A bare `obtainium://app/<encoded json>` link needs no third party, but does
nothing if tapped without Obtainium installed. The directory site offers a redirect page that
validates the payload, attempts the app link, and falls back to a "get Obtainium" prompt after a
couple of seconds without a response:

```
https://apps.obtainium.imranr.dev/redirect?r=obtainium://app/<encoded json>
```

Most projects badging themselves use this form so the badge still does something useful for a
visitor who does not have Obtainium yet.

### Seen in the wild

- [Delta Chat](https://delta.chat/en/download)
- [PrivacyNotes](https://privacynotes.app/#downloads)
