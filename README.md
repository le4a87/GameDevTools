# GameDevTools

Utilities for game development workflows.

## Fab Free Asset Library Queue

`tamperMonkeyScript.txt` is a browser userscript for Fab that helps collect currently visible free Unreal Engine assets into your Fab library. It adds a floating **FAB Library Queue** panel on Fab pages, scans visible listing cards, filters out assets that are already in your library, queues available free offers, and submits them to your library one at a time.

The script is intended for the free Unreal Engine asset channel:

```text
https://www.fab.com/channels/unreal-engine?is_free=1
```

It runs in your browser session, so it uses your normal Fab login cookies and the Fab web APIs available to the page. It does not require a separate API key.

## Prerequisites

1. Install a userscript browser extension.
   Recommended options:
   - [Tampermonkey](https://www.tampermonkey.net/)
   - [Violentmonkey](https://violentmonkey.github.io/)
   - [Greasemonkey](https://www.greasespot.net/)

2. Sign in to Fab in the same browser profile where the userscript extension is installed.

3. Open the free Unreal Engine channel:

   ```text
   https://www.fab.com/channels/unreal-engine?is_free=1
   ```

## Setup

1. Open your userscript extension dashboard.

2. Create a new userscript.

3. Replace the default contents with the contents of [`tamperMonkeyScript.txt`](./tamperMonkeyScript.txt).

4. Save and enable the userscript.

5. Refresh the Fab page. A **FAB Library Queue** panel should appear in the lower-right corner.

## Recommended Usage

Start with a small visible batch before using the automated scan.

1. Open the free Unreal Engine Fab channel.

2. Use Fab filters and sorting as desired.

3. Click **Scan visible free assets**.

4. Review the log in the floating panel.

5. Click **Add next to library** once or twice to confirm the script is selecting the expected assets.

6. Click **Add queued to library** to process the remaining queued assets.

7. Use **Auto-scroll + scan** only after confirming the manual flow works for your current Fab page.

The auto-scroll flow performs multiple scan passes, scrolls down the page to load more assets, and then starts adding queued assets to your library.

## Examples

### Add the currently visible free assets

1. Go to:

   ```text
   https://www.fab.com/channels/unreal-engine?is_free=1
   ```

2. Click **Scan visible free assets**.

3. Click **Add queued to library**.

### Review assets one at a time

1. Click **Scan visible free assets**.

2. Click **Add next to library**.

3. Check the panel log.

4. Repeat until the queue is empty.

### Scan additional page results

1. Click **Auto-scroll + scan**.

2. Leave the tab open while the script scrolls and scans.

3. Watch the panel log for skipped, queued, added, or failed listings.

## Behavior Notes

- Already-acquired listings are hidden from the page after detection.
- The script prefers free, non-professional license offers when multiple offers are discovered.
- Failed items are placed back at the front of the queue so they can be retried.
- The script waits between API calls to avoid firing all requests at once.
- Fab page markup and internal API endpoints can change. If the panel stops working, review browser console output for messages prefixed with `[FAB Library Queue]`.

## Cautions

- Only use the script while signed in to the Fab account where you want the assets added.
- Confirm the queued assets are free before running bulk actions.
- Do not close the tab while the queue is processing.
- Use the script at your own discretion and in accordance with Fab's terms and any applicable marketplace rules.
