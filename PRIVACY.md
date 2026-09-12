# GlassDeck and your privacy

GlassDeck shows what you are already playing. To do that it has to look at your
music apps and browsers, which is exactly the sort of thing you should want a
clear answer about. Here is the whole answer.

**There is no account, no sign-in, no analytics and no telemetry. Nothing about
you, your Mac or your listening is sent to the developer, ever. There is no
server to send it to.**

## What stays on your Mac

GlassDeck saves your preferences in the standard macOS preferences store, under
`io.github.garbist.glassdeck`. That is the complete list of what it keeps:

- how the widget looks: shape, glass style, material, frost, tint, translucency,
  contrast scrim, corner radius, sheen, grain, control style, visualizer style,
  the artwork slot, whether the wide panel shows a cover or a record, and which
  scrubber handle you chose
- where you left the widget on screen, and whether it floats above other windows
  or shows on all Spaces
- whether it hides itself when nothing is playing, and how long it waits first
- any keyboard shortcuts you assign, as the key and modifiers you chose. Nothing
  is assigned unless you assign it, and nothing else about your typing is read
  or stored: a shortcut is registered with macOS, which tells GlassDeck only
  that your combination was pressed
- the browser debugging port, if you changed it
- whether the setup guide has been shown, and your update-check preference

**No history of what you played is written down.** Not the track, not the artist,
not the times, not the app it came from. The current track lives in memory while
it is on screen and is replaced by the next one.

## What it reads while it runs, and why

| What | Why | macOS asks you |
|---|---|---|
| Apple Events to Music, Spotify and your browsers | To ask what is playing, and to press play, pause and skip | Automation, once per app |
| The accessibility tree of a browser window | Real playhead position, scrubbing, shuffle and repeat when no other route works | Accessibility, once |
| A loopback connection to your browser's debugging port | Reads a background tab's player without bringing it to the front | No prompt; the connection never leaves your Mac |
| A tap on the audio your Mac is already playing | Draws the spectrum analyser bars | Audio recording, once, and only if you turn the analyser on |

The audio tap deserves its own paragraph, because "audio recording" sounds
alarming. The samples go into a small fixed buffer in memory, get turned into
bar heights, and are overwritten by the next batch. Nothing is written to disk
and nothing is transmitted. Set the visualizer to Off and the tap is torn down
rather than left running.

## What leaves your Mac

Four things, all of them ordinary web requests, none of them to the developer.

**1. The update check, to GitHub.** Once a day at most, GlassDeck fetches a small
file from `raw.githubusercontent.com` to see whether a newer version exists. The
request carries nothing but itself. It downloads nothing and installs nothing; if
there is a newer version it puts a line in the menu and waits for you to click.
Turn it off under Updates and no request is ever made unless you ask for one.

**2. Track details for YouTube and YouTube Music, to Google.** When you are
playing in one of those, GlassDeck asks YouTube's public endpoints for the proper
title, artist and length of the video you are playing, using its video
identifier. Google therefore sees that a request was made for that video from
your address. You are already playing it in your browser, so this adds nothing
Google did not already know, but it is a request GlassDeck makes rather than your
browser, and you should know it happens.

**3. Cover art, from wherever the art is hosted.** For YouTube this is Google's
thumbnail servers. For any other web player it is whatever address the page
itself gives for the artwork, which means the service you are listening to. The
request fetches an image and sends nothing with it.

**4. Nothing else.** There is no fifth item.

## What is never sent anywhere

Your listening history. Your library. Your playlists. Audio from your Mac. Your
preferences. Your IP address to anyone other than the hosts named above, in
requests you can stop by not using the feature that makes them.

## Turning things off

- **Updates:** Updates ▸ Check Automatically, in the menu bar icon.
- **Audio:** set the visualizer to Off, in either settings panel.
- **Permissions:** revoke Accessibility, Automation or Audio Recording at any
  time in System Settings ▸ Privacy & Security. GlassDeck keeps working with less
  detail rather than stopping.
- **All of it:** quit from the menu bar icon, from the widget's right-click menu,
  or from the Quit row in settings.

## Removing GlassDeck completely

Quit it, drag the app to the Trash, and remove its preferences:

```
defaults delete io.github.garbist.glassdeck
```

Then remove GlassDeck from the Accessibility, Automation and Audio Recording
lists in System Settings ▸ Privacy & Security, which macOS keeps independently of
the app.

## Questions

Open an issue at
<https://github.com/GarbisT/Glassdeck-releases/issues>.

_Last updated: 12 September 2026._
