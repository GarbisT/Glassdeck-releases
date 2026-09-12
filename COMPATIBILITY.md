# What GlassDeck can read, and what you can control

GlassDeck shows whatever you are already playing. How much it can read, and how
much you can drive from the widget, depends entirely on which app or browser the
music is coming out of. Here is the order, best first.

## The short answer

### 1. A desktop music app — Apple Music, Spotify

These talk to GlassDeck directly. Nothing has to be visible, no tab has to be in
front, and there is no setting to switch on beyond granting permission the first
time.

Only these two ship a Mac app another app can read. Tidal, Deezer, Amazon Music,
Qobuz and SoundCloud are web players in a wrapper, so their desktop apps cannot
be read at all and you want their websites instead.

**You get** everything: artwork, an exact playhead, scrubbing, skip, shuffle,
repeat, and favourite on Apple Music.

### 2. A browser, with one setting turned on — Chrome, Brave, Edge, Vivaldi, Safari

Just as capable as a desktop app for web players, and it works on background
tabs, so the music can be three tabs deep while you work. It needs one switch
flipped once. Vivaldi and Safari keep that switch somewhere other than Chrome
does — see Setting it up.

**You get** artwork, an exact playhead, scrubbing and skip on any site; shuffle,
repeat and save on sites that offer them.

### 3. Opera

Opera is the one browser that cannot run JavaScript sent by another app: the
command is commented out of its scripting definition and no setting turns it
back on. Everything else about its scripting works, tab titles and addresses
included, so GlassDeck reads the player the way a screen reader would. That
works well, with two limits: the music tab has to be the one you are looking at,
and the progress bar is read-only. Switch to another tab and the widget drops to
just the track name with the buttons greyed out.

**You get** artwork, a playhead, skip, shuffle and repeat *while the music tab is
in front*. No scrubbing, unless you start Opera with a debugging port — and with
that port Opera is as capable as any browser here, background tabs included. See
[Scrubbing in Opera](#scrubbing-in-opera).

### 4. A browser without that setting

The track name from the tab, and nothing to press. YouTube Music is the
exception: it is read from the address bar, so it keeps artwork and a rough
playhead with no setup at all.

### Firefox is not supported

Firefox has no scripting worth the name: no tabs, no addresses, and no way to run
JavaScript on another app's behalf. Its window title *is* readable, and on a site
like YouTube Music that title carries the track, so the song name alone could be
shown.

That is the whole of it. No artwork, no playhead, nothing to press. Measured, not
assumed: with Firefox's own accessibility engine switched on, its page is exposed
as a tree of some seventeen hundred elements and not one labelled play, pause,
next or progress control appears in it.

A now-playing widget that can only name the song, with every button greyed out,
is not worth installing, so GlassDeck does not read Firefox at all rather than
pretend to support it.

## By service

| Service, and where to play it | Track & artwork | Playhead | Scrub | Play & skip | Shuffle | Repeat | Favourite |
| --- | --- | --- | --- | --- | --- | --- | --- |
| **Apple Music** — the Music app | Yes | Exact | Yes | Yes | Yes | Off, all, one | Yes |
| **Spotify** — the Spotify app | Yes | Exact | Yes | Yes | Yes | On or off ¹ | No ² |
| **Spotify** — open.spotify.com in Chrome, Brave, Edge, Vivaldi | Yes | Exact | Yes | Yes | Yes | Off, all, one | Yes ³ |
| **Spotify** — open.spotify.com in Safari | Yes | Exact | In 5s steps ⁴ | Yes | Yes | Off, all, one | Yes |
| **YouTube Music** — Chrome, Brave, Edge, Vivaldi | Yes | Exact | Yes | Yes | Press only ⁵ | Off, all, one | Yes |
| **YouTube Music** — Opera | Yes | Exact | Only with a port | Yes | Press only ⁵ | Off, all, one | No |
| **YouTube Music** — Safari | Yes | Exact | Yes | Yes | Press only ⁵ | Off, all, one | Yes |
| **Tidal** — listen.tidal.com | Yes | Exact | Yes | Yes | No | No | No |
| **Deezer** — deezer.com | Yes | No | No | No | No | No | No ⁶ |
| **Bandcamp** — bandcamp.com | Browse pages only ⁷ | No | No | No | No | No | No |
| **Anything else on the web** | Usually | Usually | Usually | Usually | No | No | No ⁸ |

¹ Spotify's app has all three repeat states, but publishes only a yes or no to
other apps — see below.
² Spotify's app offers no way to save the current track.
³ The web player gives more than the app: repeat-one and saving. During an
advert Spotify removes the whole control group, so those buttons grey out until
the song comes back.
⁴ Safari's progress control only accepts five-second increments, so a scrub lands
on the nearest one.
⁵ See "Shuffle on YouTube Music" below.
⁶ Deezer says what is playing but exposes no player to reach into, so the widget
shows it and cannot drive it.
⁷ Album pages announce nothing at all and are not picked up. Discover pages give
a title and artist with no artwork.
⁸ Most sites announce what they are playing in a standard way, and those work.
Shuffle, repeat and favourite are always site-specific.

### Repeat-one in Spotify's app cannot be seen from outside it

Spotify's own window has all three repeat states and you can use them normally.
What Spotify publishes to other apps is a single yes-or-no answer: repeat-off
says no, and **both repeat-all and repeat-one say yes**. So when you switch
Spotify from all to one, the widget's button does not change, because nothing it
can read has changed. It shows the repeat-all icon for both, and its tooltip says
so rather than claiming a state it cannot know. Pressing the widget's repeat
button from either one turns repeat off.

This applies to Spotify's app alone. The web player reports all three properly.

### Shuffle on YouTube Music is a press, not a switch

Its button is labelled the same whether shuffle is on or off; the only
difference is the colour of the icon. The widget can turn shuffle on and off for
you, but it cannot tell you which it currently is, so the button does not light
up. True in every browser. Spotify is the opposite: it says so plainly, and the
widget shows it.

## Setting it up

### Chrome, Brave, Edge

Turn this on once. It is off by default, and until it is on GlassDeck cannot
read your tabs at all.

```
View ▸ Developer ▸ Allow JavaScript from Apple Events
```

### Vivaldi

The same switch, somewhere else entirely. Vivaldi has no Developer menu, so
following the Chrome instructions sends you hunting for a menu that does not
exist.

```
Settings ▸ Privacy and Security ▸ Apple Events ▸ Allow JavaScript from Apple Events
```

### Safari

Tick *Show features for web developers* in Advanced first, or the Developer tab
will not appear. Note this is in Safari's settings, not in the Develop menu.
Without this switch Safari is read-only.

```
Safari Settings ▸ Developer ▸ Allow JavaScript from Apple Events
```

### Permissions macOS will ask for

**Accessibility** lets the widget press your player's buttons. **Automation**
lets it ask an app what is playing, once per app. **System Audio Recording** is
only for the visualiser — decline it and the bars fall back to an animation.

On the wide layout the spectrum does not cost you the album art: it runs as a
band behind the title and along the progress bar, and a button beside the
settings one switches it on and cycles the six styles. Compact and Vinyl still
trade one for the other, because they have nowhere else to put it. The wide
layout can also show a turning record in place of the cover.

The first time GlassDeck speaks to a new app, macOS holds the request until you
answer the prompt. If it seems to hang for a minute, the dialog is waiting for
you somewhere.

### If a browser will not play along

Three different things make a browser refuse to be read, and they look
identical from the outside — GlassDeck will tell you it was refused but cannot
tell you which:

1. **The switch is off.** The paths are above.
2. **The browser is on its profile picker.** Until you choose a profile, the
   Developer menu is greyed out and the browser refuses. Choosing one is enough.
3. **The music is playing in an "installed" web app.** A site added with the
   browser's own Install button gets its own icon and window, and that window
   refuses to be read no matter what the switch says. It is not an application
   and not an ordinary tab, so nothing can see it. Its own menu offers to open
   it in the browser; do that, or install the service's real application.

The third is the one nobody works out alone. If your player looks like an app
but has a three-dot menu offering "Open in Chrome", that is what you have.

### If Accessibility looks on but nothing works

macOS records that permission against the app's signature. An entry added by a
different copy of GlassDeck — one signed by somebody else, or an unsigned build —
sits in the list looking enabled while applying to nothing.

Remove it with the minus button, then add GlassDeck back from your Applications
folder with the plus. The setup guide's badge turns green within a second or two.
Moving or reinstalling the app on its own does not cost you the permission.

### Scrubbing in Opera

Moving the playhead needs JavaScript, and Opera is the one browser that will not
run any on another app's behalf, so the widget's progress bar is read-only
there. The one way round it is to start Opera with a debugging port.
Quit Opera fully, then run this in Terminal:

```bash
open -na Opera --args --remote-debugging-port=9222
```

Opera then behaves like Chrome in every respect we have tested: background tabs,
real state, and scrubbing that works. This was verified against a running Opera
on 12 September 2026, after an earlier note here implied the port did nothing
for it.
**Understand the trade first.** A debugging port lets any program on your Mac
drive that browser and read what is in your tabs. Fine on a machine only you use,
a poor idea on a shared one, and you have to start Opera that way every time.

## Things that surprise people

### One thing that looks like Spotify and is not

Chrome can turn a website into what looks like an app, with its own icon and
window. A Spotify installed that way is a Chrome window, not Spotify's desktop
app, and GlassDeck sees it as neither. If your Spotify came from Chrome's
"Install" button rather than from spotify.com, either install the real app or
just use the web player in a normal tab, which is fully supported.

### Spotify's app and Spotify's website are one player, not two

One Spotify account plays in one place at a time. Start the web player and the
desktop app stops and reports itself paused, and the other way round. So the two
Spotify rows above are two ways of reaching the same stream, not two sources you
can run side by side. If you press play in the widget while the website holds the
stream, the website is what starts.

### A video in another tab will take the widget over

GlassDeck watches a handful of sites for playback, and **ordinary YouTube is one
of them**, including Shorts. Start a video in another tab, or pause your music
while one is open, and that video becomes the thing that is playing. The widget
will show it, and the buttons will control it rather than your music.

The sites it watches: YouTube, YouTube Music, Spotify, SoundCloud, Apple Music,
Bandcamp, Tidal and Deezer. Anywhere else is ignored, so a video on a news site
or a social feed will not interrupt anything.

### Playing in more than one place

GlassDeck follows whatever is actually making sound, and prefers a desktop music
app over a browser tab when both are going. When nothing is playing it stays on
the last thing you listened to rather than jumping around.

### Edge puts background tabs to sleep

Edge saves memory by suspending tabs you have not touched in a while. GlassDeck
gives up on a sleeping tab quickly rather than waiting on it, so the browser
stays readable. Edge never sleeps the tab that is making sound, so your music is
never the one affected.

## How this was verified

Nothing here is taken from documentation. Spotify's repeat states were read out
of the running app one at a time while its control was switched by hand. Apple
Music, Spotify (the app, the web player in Chrome and the web player in Safari)
and YouTube Music in Chrome, Vivaldi, Edge, Safari and Opera were driven through
the widget itself, with every control pressed and every setting put back
afterwards.

Tidal, Deezer and Bandcamp were verified by inspecting what their players expose
to the Mac while a track was playing, which is what determines each row, but the
widget has not yet been pointed at them end to end.

GlassDeck has so far only been run on Apple silicon. Anything not listed has not
been tested.

_Last updated: 12 September 2026._
