# DIT/FM v1.2 — Official Morse music and on-demand player

Upload **index.html** and **tracks.json** to the root of your GitHub Pages repository. Enable Pages for that branch/root. The browser requires a click to start audio.

## v1.2
- 7 supplied full-length Morse transcriptions added to the official catalogue; 21 remain awaiting Morse.
- Separate **TRACK PLAYER** tab with individual selection, search, pause, stop, progress and seek.
- Radio and on-demand player are mutually exclusive: starting one stops the other.
- Visitor-created tracks remain in that visitor's browser storage; only tracks.json changes the official global library.
- Signal speed and volume sliders apply to both modes.

## Important
The radio is a **continuous locally generated broadcast**, not a globally synchronized livestream: different visitors may be listening to different tracks. Full lyrics-derived Morse may be subject to copyright permissions before public distribution.

## Editing
Add a valid `morse` string to the corresponding item in `tracks.json` and set `status` to `ready`. Separate Morse letters with spaces and words with `/`. Playback ignores song melody and uses configurable tone movement.

## Favicon update
This release adds `favicon.svg`, `favicon-32.png`, `apple-touch-icon.png`, and `favicon-192.png`. Keep the icons beside `index.html` when uploading to GitHub Pages. Browser tab icons may require a hard refresh because browsers cache favicons.
