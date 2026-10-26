# Video Clipper — IN/OUT MP4 Trimmer

Choose a video on a web page, mark IN/OUT, preview your selection and save an MP4 on your computer. Export several intervals as **one joined video or separate numbered files**. Crop directly over the original player, choose a phone or square format, adjust export audio and add a watermark. The interface is in Italian.

**Current direct release: [extension 1.11.0 + helper 1.8.0](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.11.0).** Install both components for all current export features. Updating the browser extension does not update the helper.

| Download | Purpose |
|---|---|
| [Firefox 1.11.0 — signed XPI](https://github.com/FlamingFury28/video-clipper/releases/download/v1.11.0/VideoClipper-1.11.0-signed.xpi) | Permanent installation; signed by Mozilla for direct distribution |
| [Windows helper 1.8.0](https://github.com/FlamingFury28/video-clipper/releases/download/v1.11.0/VideoClipper-Helper-1.8.0-Windows.zip) | Local export companion; extension downloaded separately |
| [Linux x86_64 helper 1.8.0](https://github.com/FlamingFury28/video-clipper/releases/download/v1.11.0/VideoClipper-Helper-1.8.0-Linux-x86_64.tar.gz) | Desktop Linux companion; extension downloaded separately |
| [Chromium extension 1.11.0](https://github.com/FlamingFury28/video-clipper/releases/download/v1.11.0/VideoClipper-1.11.0-Chromium.zip) | Unpacked installation in Chrome/Edge developer mode; no store publication |
| [SHA-256 checksums](https://github.com/FlamingFury28/video-clipper/releases/download/v1.11.0/VideoClipper-1.11.0-SHA256SUMS.txt) | Verify the four packages above |

[Installazione e guida in italiano](INSTALLAZIONE.md) · [Privacy](PRIVACY.md) · [Changes](CHANGELOG.md) · [Verification](VERIFICATION.json) · [Issues](https://github.com/FlamingFury28/video-clipper/issues)

## Install or upgrade

1. Provide **FFmpeg and ffprobe with libx264/AAC on PATH**. They are not bundled. Start from the [official FFmpeg download page](https://ffmpeg.org/download.html). Python, yt-dlp, EJS and Deno are bundled with the helper; no separate Python, Node or Deno installation is needed.
2. Extract the appropriate helper archive **in full** to a permanent folder. Keep `VideoClipperHelper` and its `_internal` directory together. Register it as the user running the browser: **Installa helper.cmd** on Windows, or `./installa-helper.sh firefox` on Linux. Do not use administrator access or sudo. Register again if you move the folder.
3. In Firefox open `about:addons`, choose the gear menu → **Install Add-on From File**, and select **VideoClipper-1.11.0-signed.xpi**. Reopen the browser to renew its helper connection, then reload open video pages.
4. Open extension settings, run **Verifica configurazione**, confirm helper **1.8.0**, choose the output folder and activate Video Clipper on a video page. Select the intended player before marking a clip.

For Chrome/Edge, extract the Chromium ZIP to a stable folder and load that folder through `chrome://extensions` or `edge://extensions` with developer mode enabled. Register the helper for that browser using the `chrome` or `edge` argument; registration for Firefox alone is insufficient. The [Italian guide](INSTALLAZIONE.md) includes exact commands and backup/restore instructions.

| Platform | Verified scope |
|---|---|
| Firefox 142+ on Windows x64 | Firefox 142.0 and 158.0.1 on Windows 11 x64 |
| Firefox desktop on Linux x86_64 | Firefox 158.0.1 on Ubuntu 24.04 via WSL; Snap/Flatpak packages unverified |
| Chrome/Edge on Windows x64 | Chrome 155 / Edge 156, unpacked extension |
| macOS, Android, iOS | No verified helper package available |

The XPI is Mozilla signed. The helper binaries have no separate code-signing signature; package hashes and verification metadata are provided.

## Edit on the page

- **Precise intervals:** IN/OUT fields, configurable fine/coarse steps, undo and preview of the selected part. Preview restores the earlier playback state. Reorder parts or repeat/overlap intervals from the same video.
- **Joined or separate:** choose one MP4 or a numbered file for each part in **Impostazioni → Salvataggi** or **Clip → Esportazione**. The source is acquired once and existing output files are not overwritten.
- **Crop on the original video:** **Clip → Esportazione → Ritaglia sul video** opens a rectangle on the page player. Drag, move or resize it; confirm with Enter or cancel with Esc. Choose Original/free, **9:16 phone, 16:9, 1:1 or 4:5**. Presets crop without stretching; a centered crop is used when no manual position is chosen.
- **Audio and watermark:** set export volume from 0 to 200% or remove the audio track. Show/hide audio controls and optionally remember the last choice. These settings affect exported files. Upload a local watermark and choose its position, size, opacity and margin; it is applied after cropping.
- **Personal defaults:** choose how the video name is obtained, a fallback name, prefix/suffix and filename template. Save output profiles, associate them with sites, keep projects and queue exports. Queued clips retain their output settings.
- **Less clutter:** history opens separately; completed jobs offer file/folder and copy-path actions. Firefox follows the active browser theme palette; other browsers use native colors and light/dark mode. Explicit light/dark overrides remain available.
- **Shortcuts and updates:** customize editor shortcuts and browser commands in settings. **Aggiornamenti** checks extension and helper versions together against published GitHub releases, on request and with separate network permission. It does not download or install updates automatically.

## Source access, recovery and limits

Accessible HTML5 players, dynamic pages, embedded frames and open shadow roots are supported. Automatic selection can be overridden manually. Source identity, duration and interval checks guard against saving a different video. Expired-source recovery is bounded and requires the replacement to match the selected video; it is not a promise that every website can be downloaded.

If needed, enable **Ricerca avanzata** for the site and play the intended video. Session access (**Usa la sessione del browser per questo sito**) is separate, optional, initially off and revocable. Grant it in the browser profile/context where you are authenticated. Cookie store and partition boundaries are preserved; another profile is not used. Configuration checks, diagnostics and context recovery are available in settings. Diagnostic reports omit cookie values, source addresses, titles and local paths.

Source access may require downloading the full video before trimming, using bandwidth, time and temporary disk space. A specifically selected audio track must resolve unambiguously. DRM, live streams and closed shadow roots are unsupported. Exit native video fullscreen before editing the crop; CSS-rotated or reflected players cannot use the crop overlay. Media orientation metadata is handled separately during export. “Original” quality is not lossless.

Verification covers isolated profiles and controlled media, including real output durations, frames, crop pixels and audio. For this release: **79 JavaScript suites; 474 Python tests (6 environment skips); 33 signed Firefox functional cases; 9 signature/restart checks; 16 binary checks; 24 Chrome/Edge cases**. These results do not certify every authenticated website. See [VERIFICATION.json](VERIFICATION.json).

## Distribution and privacy

The current **1.11.0 signed XPI is approved for direct distribution (unlisted / Self)**. Mozilla's separate catalog channel remains at **1.4.7, approved**; it does not contain the new 1.11.0 features. Use the GitHub release linked above for the current complete distribution. The XPI has no custom automatic-update URL. Checking for updates and installing them are separate actions.

Conversion runs locally. Requests go to the source websites/CDNs; there is no Video Clipper cloud editing or analytics service. Preferences, projects, watermarks and history stay on your device. Clearing history removes references, not saved files. Read the [privacy policy](PRIVACY.md), including optional session access and update checks.

This repository contains **public documentation and downloads**. Project Python sources remain private. Helper archives contain the verified binary and upstream licenses/source material required for dependencies; GitHub-generated source archives contain only this documentation repository. See [third-party notices](THIRD-PARTY-NOTICES.md).
