# DIT/FM v1.1 — Official Catalogue

Static GitHub Pages radio station. Includes **28 official song catalogue entries** in `tracks.json` grouped as 90s Classics (8), Y2K Hits (10), and 2000s Nostalgia (10). All 28 are marked `awaiting_morse` and are **not playable** until dot-and-dash transcriptions are supplied. Three original demo broadcasts remain playable.

## Deploy
Upload `index.html` and `tracks.json` to the **root** of your GitHub Pages repository, then enable Pages (main branch / root). Keep the two files together. Use an HTTP server to test locally; opening `index.html` with `file://` often blocks loading `tracks.json`.

## Add an official track
Open `tracks.json` in an editor. Find the song by its `id` or `title`. Paste the Morse code as a single JSON string in its `morse` field, separating letters with spaces and words with ` / `. Optionally update `pitch` (Hz) and `style` (`flat`, `rise`, `bounce`, or `chord`). Set `status` to `ready` for administrative clarity. Once published to GitHub, the station detects playable entries based on the valid, nonempty `morse` value — so it cannot accidentally broadcast unfilled placeholders.

Example of *format only* (fictional demo, not song lyrics):
```json
"morse": ".... . .-.. .-.. --- / .-- --- .-. .-.. -.."
```
Keep all commas and quotation marks valid JSON. Each entry also has a collection and year for filtering. Other visitors cannot alter repository tracks via the website. Their custom additions remain in their own browser's localStorage. Only users with repository write access can publish official changes.

## Copyright
Publishing encoded copyrighted song lyrics may still require permission. Track titles and artists alone are metadata, not transcribed lyrics. The station uses local browser-generated audio; no Spotify or YouTube streams.
