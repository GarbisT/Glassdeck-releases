# GlassDeck releases

Downloads and release information for **GlassDeck**, a floating glass now-playing
widget for macOS. The application source lives elsewhere; this repository exists
so that the installer and the version manifest have a public home.

## For people

Get the latest build from the [Releases page](https://github.com/GarbisT/Glassdeck-releases/releases/latest).

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
