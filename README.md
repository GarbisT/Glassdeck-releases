# GlassDeck releases

Downloads and release information for **GlassDeck**, a floating glass now-playing
widget for macOS. The application source lives elsewhere; this repository exists
so that the installer and the version manifest have a public home.

## For people

Get the latest build from the [Releases page](https://github.com/GarbisT/Glassdeck-releases/releases/latest).

GlassDeck needs macOS 14 or later and runs on Apple silicon and Intel Macs.

- **[What works where](COMPATIBILITY.md)** — every player, browser and service,
  what each one gives you, and the one switch most browsers need. Read this
  before deciding GlassDeck cannot see your music.
- **[Privacy](PRIVACY.md)** — everything it reads, everywhere it connects, and
  the fact that none of it reaches the developer. No account, no analytics, no
  telemetry.
- **[Licence](LICENSE.md)** — the terms the app is distributed under. It is
  proprietary: yours to use, not yours to redistribute.

The app links to both of these from its setup guide and from the About submenu
in the menu bar, so the copies here are the ones people actually read. They are
mirrors of the versions in the application's own repository; change them there
first.

## For the app

`appcast.json` is what a running copy of GlassDeck reads to find out whether a
newer version exists. It never downloads anything by itself: it shows a line in
the menu bar and opens the Releases page when you click it. Automatic checking
can be turned off in the app under Updates.

| Field | Meaning |
| --- | --- |
| `version` | Marketing version, compared component by component |
| `build` | Build number, used only to break a tie between equal versions |
| `url` | Where the menu item sends people |
| `notes` | One line, shown under the update in the menu |
| `minimumSystemVersion` | Lowest macOS this build supports |

Publish the release before updating this file. The other order points every
running copy at a download page that does not exist yet.
