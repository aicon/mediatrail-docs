# Now Watching

[Magyar változat](hu/now-watching.md)

While a companion app is playing or paused, MediaTrail can show one or more **Now Watching** strips at the top of the home page — one strip per device.

![Now Watching on the home page](screenshots/now-watching-desktop2.png)

## What you need

- A running MediaTrail (see [Install](install.md)).
- A companion client: [NuvioMobile-MT](https://github.com/aicon/NuvioMobile-MT) or [NuvioTV-MT](https://github.com/aicon/NuvioTV-MT). Official upstream Nuvio apps do not send these player events.
- No separate scrobbler container. The MediaTrail image already includes the addon.

## Setup

1. In MediaTrail open **Settings → Integrations → Nuvio** while signed in as the account that should receive the strips.
2. Copy the addon address (`…/nuvio/<your-token>/manifest.json`). It is personal to that MediaTrail account.
3. In each companion install open **Settings → Addons**, add that address, and remove any old scrobbler or untokened MediaTrail URL.
4. Play a movie or episode. Each device appears as its own strip on **that** account’s home page.

## Multi-device behaviour

| Behaviour | Detail |
| --- | --- |
| Stable order | Strips keep first-seen order; a progress tick does not jump a device to the top |
| One strip per device | A phone and two TVs can show at the same time without overwriting each other |
| Per MediaTrail account | Playback follows the token in the addon URL; other users do not see your strips |
| Automatic label | Companions send a stable id plus a label such as `telefon · Pixel 8` or `TV · Shield` |
| Rename | Edit the name on the strip; the custom name survives stop and dismiss |
| Pause / stop / dismiss | Only that device’s strip is affected |
| Finished watch | Saved when the client sends `stop` and progress is at least **90%** |
| Idle cleanup | A watching strip with no progress ages out after about three minutes; a paused strip after about ten. Operators can change that under [Runtime](runtime.md) |

Seek should also send progress so the strip stays in sync. Leaving the player should send `stop`.

## Not the same as Nuvio import

[Imports](imports.md) can pull finished history from a Nuvio profile on a schedule. That path does not drive the live strips, and it does not replace per-device Now Watching rows.

The library overview is on [Library](library.md).
