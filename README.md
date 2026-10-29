# DIT/FM — All Morse. All the Time.

**A fictional, browser-based radio station where every voice, song, and station transmission is Morse code.**

**Current version:** v1.2.1 · **Platform:** GitHub Pages · **Status:** Working prototype / expanding official catalogue

DIT/FM reimagines radio as an all-Morse broadcast. Instead of conventional spoken presenters, its hosts have distinctive audio frequencies. Instead of recordings of songs, the station transmits the words of familiar tracks as synthesised dots and dashes. It is part nostalgic radio experiment, part listening challenge, and part interactive sound artwork.

> **The question behind the project:** Could you recognise a song you grew up with if all you heard were its words transmitted in Morse code?

## The idea

The station is built around two ways to listen:

1. **Radio:** Tune in to an ongoing, locally generated broadcast. Morse-code hosts introduce tracks and converse between transmissions; the system selects from available material.
2. **Track Player:** Choose a specific ready track, start from the beginning, and control playback independently of the station.

Only one audio source plays at once: starting an on-demand track stops the radio, and returning to the radio stops the track player.

The song data represents **lyrics converted into Morse**, not recordings of the original songs or their melodies. Recognising a track is primarily a matter of recognising its transmitted words and repeated patterns. Different tones and pitch treatments add character, but do not automatically reproduce the original tunes.

## Features so far

- **Morse-only station identity:** radio-style host interludes, station announcements, and Morse audio throughout the listening experience.
- **Three distinguishable hosts:** DOT (530 Hz), DASH (760 Hz), and ECHO (950 Hz), giving their transmissions recognisably different pitch registers.
- **Browser-generated audio:** Morse tones are synthesised in the browser; visitors do not need external audio services or downloaded song recordings.
- **Signal display:** an animated signal visualisation and transmission/readout interface.
- **Radio controls:** tune in, stop, skip, and adjust signal speed and volume.
- **Dedicated on-demand player:** searchable track selection with play, pause/resume, stop, a playback progress indicator, and seeking.
- **Official catalogue:** a separate `tracks.json` file listing both playable and pending tracks.
- **Three music collections:** 90s Classics, Y2K Hits, and 2000s Nostalgia.
- **Visitor experimentation:** visitors can enter their own Morse tracks, stored in their own browser rather than sent to the public repository.
- **Library import/export:** options for moving or backing up browser-local material.
- **Favicon set:** station-branded browser tab icon and touch icons.
- **Static hosting:** designed for GitHub Pages, with no required backend or database.

## Official music catalogue

The initial catalogue contains **28 selected songs**, spanning 1990–2009. **Seven currently have user-supplied Morse transcriptions and are marked ready**; **21 are awaiting Morse**. Three separate original demo pieces are also available in the station.

| Collection | Track | Artist | Catalogue status |
| --- | --- | --- | --- |
| 90s Classics | Wannabe | Spice Girls | Ready |
| 90s Classics | Barbie Girl | Aqua | Ready |
| 90s Classics | MMMBop | Hanson | Awaiting Morse |
| 90s Classics | Ice Ice Baby | Vanilla Ice | Awaiting Morse |
| 90s Classics | Wonderwall | Oasis | Awaiting Morse |
| 90s Classics | Smells Like Teen Spirit | Nirvana | Awaiting Morse |
| 90s Classics | Everybody (Backstreet’s Back) | Backstreet Boys | Awaiting Morse |
| 90s Classics | How Bizarre | OMC | Awaiting Morse |
| Y2K Hits | Bye Bye Bye | NSYNC | Awaiting Morse |
| Y2K Hits | Oops!... I Did It Again | Britney Spears | Ready |
| Y2K Hits | It Wasn’t Me | Shaggy | Awaiting Morse |
| Y2K Hits | Complicated | Avril Lavigne | Awaiting Morse |
| Y2K Hits | Lose Yourself | Eminem | Awaiting Morse |
| Y2K Hits | Hey Ya! | OutKast | Ready |
| Y2K Hits | Crazy in Love | Beyoncé | Awaiting Morse |
| Y2K Hits | Bring Me to Life | Evanescence | Ready |
| Y2K Hits | Yeah! | Usher | Awaiting Morse |
| Y2K Hits | Boulevard of Broken Dreams | Green Day | Ready |
| 2000s Nostalgia | Mr. Brightside | The Killers | Ready |
| 2000s Nostalgia | Hollaback Girl | Gwen Stefani | Awaiting Morse |
| 2000s Nostalgia | Don’t Cha | The Pussycat Dolls | Awaiting Morse |
| 2000s Nostalgia | Hips Don’t Lie | Shakira | Awaiting Morse |
| 2000s Nostalgia | Umbrella | Rihanna | Awaiting Morse |
| 2000s Nostalgia | Girlfriend | Avril Lavigne | Awaiting Morse |
| 2000s Nostalgia | Low | Flo Rida | Awaiting Morse |
| 2000s Nostalgia | Poker Face | Lady Gaga | Awaiting Morse |
| 2000s Nostalgia | Single Ladies (Put a Ring on It) | Beyoncé | Awaiting Morse |
| 2000s Nostalgia | I Gotta Feeling | The Black Eyed Peas | Awaiting Morse |

*Note: the collections are editorial playlists. “Mr. Brightside” is filed under 2000s Nostalgia despite its original 2003 release.*

## How a Morse track works

A Morse generator turns words into dots (`.`) and dashes (`-`). In the catalogue:

- A **space** separates Morse characters (letters or punctuation).
- A **slash** (`/`) separates words.
- Tone duration and the spaces between signals are determined by playback timing.
- Each song has an associated pitch and audio style.

A short, original demonstration (not a song lyric):

```text
-.. .. - / ..-. --
```

This represents “DIT FM.” The player converts this notation into audio. Long transcriptions can take considerably more time to transmit than the length of the original recorded song, particularly at slower Morse speeds.

## The official catalogue vs visitor-created songs

**Official songs** are shipped as data in `tracks.json`. When the project owner updates that file in the GitHub repository and GitHub Pages publishes the change, everybody receives the updated catalogue.

**Visitor-created songs** are saved in the visitor’s browser storage (`localStorage`). They:

- do **not** change the GitHub repository;
- do **not** automatically appear for other visitors;
- may be lost if browser storage is cleared or the site is opened on another device.

The current site is **not** a community submission system, shared cloud library, or repository editor. Adding visitor submissions with moderation would be a separate future development.

## Running the project locally

For a simple local preview, open `index.html` in a current desktop browser. For the most reliable loading of the official JSON catalogue, run a basic local web server instead:

```bash
python -m http.server 8000
```

Then visit `http://localhost:8000`.

The browser requires a user click or tap before it can start audio; this is normal browser autoplay protection.

## Publishing on GitHub Pages

1. Create or open the GitHub repository used for DIT/FM.
2. Place the release files in the repository root (or in the configured publishing directory):

   ```text
   index.html
   tracks.json
   favicon.svg
   favicon-32.png
   favicon-192.png
   apple-touch-icon.png
   README.md
   ```

3. In **Settings → Pages**, select the relevant branch and publishing folder (for example, `main` and `/ (root)`).
4. Save, then open the URL GitHub Pages provides.
5. Press the station’s play/tune-in control to start audio.

When replacing a previous version, upload all changed files while preserving their relative paths. If a newly uploaded favicon is not visible, try a hard refresh or allow the browser’s favicon cache to update.

## Adding another official song

The recommended editorial workflow is:

1. Choose a pending entry in the official catalogue.
2. Convert the words you have permission to use into Morse, retaining spaces between letters and `/` between words.
3. Review the Morse text for malformed symbols and accidental joined characters.
4. Open `tracks.json` and find the matching entry by `id` or title.
5. Fill its `morse` field and change `status` from `awaiting_morse` to `ready`.
6. Keep its other metadata (title, artist, year, collection, pitch, style) intact unless deliberately changing the sound profile.
7. Publish the updated JSON file and test it in both the radio and the on-demand player.

For reference, entries use fields similar to:

```json
{
  "id": "official-example",
  "title": "Example Song",
  "artist": "Example Artist",
  "year": 2001,
  "collection": "Y2K Hits",
  "status": "ready",
  "morse": "-.. .. - / ..-. --",
  "pitch": 700,
  "style": "bright"
}
```

*The example above is illustrative, not an actual official track. Use an existing entry’s metadata and supported style values as a template.*

## Architecture and hosting limitations

DIT/FM is a **client-side static website**. The primary files are HTML/CSS/JavaScript (`index.html`) and the official JSON catalogue (`tracks.json`). Audio is generated in the browser with web audio synthesis, and personal additions use browser-local storage.

The radio currently behaves like an ongoing **broadcast experience for each listener**, not a single server-hosted livestream. Listeners do **not** necessarily hear the same track at the same moment, and there is no shared global playhead, live DJ backend, or scheduled broadcast server.

Audio playback behaviour and performance can differ by browser and device. Long lyric-based Morse tracks are a particular area for future testing and tuning.

## Project history

| Version | Development milestone |
| --- | --- |
| **v1.0** | Initial all-Morse station; synthesised hosts and radio transmission experience; foundational browser-based site. |
| **v1.1** | Official 28-song catalogue, separated from visitor-created tracks; pending/ready catalogue structure. |
| **v1.2** | Seven supplied Morse tracks made playable; separate searchable on-demand track player with transport controls; playback modes kept mutually exclusive. |
| **v1.2.1** | Added browser/favicon and touch-icon assets without changing the core radio and track-player concept. |

## Ideas for future development

These are **proposals, not completed features**:

- More official tracks and more curated era/genre collections.
- A 90s or Y2K **Mystery Hour** where listeners guess songs before titles are revealed.
- Richer host personalities, scheduled shows, themed station IDs, and Morse-only mock advertisements.
- More varied instrument-like Morse timbres, independent speed controls, and configurable song pitch arrangements.
- Better accessibility, guidance for new Morse listeners, and interactive decoding aids.
- A moderated submission flow for community tracks.
- Optional true synchronisation if the project ever needs every listener to hear the same broadcast at the same time.

## Credits and rights

**Project concept, curation, and creative direction:** the DIT/FM project creator. The website has been developed iteratively with AI assistance.

Songs are credited to their original artists in the catalogue. The song titles and artist names are identification metadata. **Morse conversion does not remove copyright from underlying lyrics.** Before publicly distributing full lyric-derived transcriptions, ensure that the necessary rights or permissions apply. The project does not claim ownership of any third-party compositions or lyrics.

---

**DIT/FM — All Morse. All the Time.**

*A strange little radio station for people who remember the songs, even when they can no longer hear the melodies.*
