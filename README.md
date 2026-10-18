# Video Clipper — IN/OUT MP4 Trimmer for Firefox

Video Clipper lets you choose an HTML5 video player, mark an IN/OUT interval, preview it, then save a local MP4 through a Windows companion helper. Adjust markers by **0.1 or 1 second**, enter timestamps, and undo interval edits. Preview restores the previous playback position and paused/playing state.

The controls can reserve space on any side of the page, float over the selected video, or use Firefox's native sidebar. Player detection includes accessible frames, dynamically replaced videos and **open shadow DOM** components.

**Current signed release: 1.2.0. Interface: Italian. Supported export environment: Windows 11 x64 and Firefox 142+.**

Version 1.2.1 has been submitted for the public Mozilla Add-ons catalog and is awaiting review. It updates only the manifest's version, installed name, description and homepage; player and export behavior are unchanged from 1.2.0. The Windows helper remains compatible at 1.2.0. Until Mozilla publishes the new version, use the signed 1.2.0 assets below.

[Download the Windows package](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.2.0) · [Istruzioni in italiano](INSTALLAZIONE.md) · [Privacy](PRIVACY.md) · [What's new](CHANGELOG.md)

## Install

1. Install FFmpeg and ffprobe with libx264 and AAC support, and put their folder on your Windows PATH. Start from the [official FFmpeg download page](https://ffmpeg.org/download.html#build-windows). FFmpeg is **not** bundled. Reopen Firefox after changing PATH so it inherits the new setting.
2. Download **VideoClipper-1.2.0-Windows.zip** from Releases. Extract **all** its contents to a permanent folder, for example a VideoClipper folder under your user directory. Do not run inside the ZIP or move the folder after registration.
3. Run **Installa helper.cmd**. It checks the helper, registers the native host for the current Windows user, and keeps a backup of an existing native manifest. Administrator access and a separate Python installation are not required. Python, yt-dlp, curl-cffi and lz4 are included in the executable bundle.
4. In Firefox, open **about:addons**, choose the gear menu → **Install Add-on From File**, and select **VideoClipper-1.2.0-signed.xpi**. Verify version 1.2.0 in the add-on details. The XPI is signed by Mozilla; signing alone is not a claim of recommendation or public-store approval.
5. Open the add-on's **Preferenze** and press **Verifica collegamento**. Choose a destination folder. Reload video pages that were already open before upgrading.

Keep `VideoClipperHelper.exe` together with its `_internal` directory. If you move the extracted folder, run `Installa helper.cmd` again from its new location. The helper executable is not separately Authenticode-signed; the Firefox XPI has a Mozilla signature. Windows may show an unknown publisher for the helper. Do not disable Windows protections to install it.

## Clip a video

Activate Video Clipper from the Firefox toolbar. Use **Cambia video** if the page contains several players. Set **IN** and **OUT** with **Usa tempo attuale**, timestamp input or the 0.1/1-second controls. Press **Anteprima**, then **Salva clip**.

Choose Originale, 1080p or 720p as a resolution limit; smaller videos are not upscaled. Follow download/conversion progress or cancel the save. On completion you can open the file or folder, copy the path and revisit recent results in local history. Closing the panel lets an active save continue; use **Annulla salvataggio** to cancel it.

## Compatibility and limits

Export depends on an accessible media source and yt-dlp support. Downloadable direct MP4 and HLS sources are supported where available. DRM media is unsupported, and seeing a player does not guarantee export. Closed shadow roots are not inspected. CSS/SVG-transformed iframes may affect floating-panel alignment. The Windows helper is not supported on macOS, Linux or Android.

Originale sets the available resolution limit; it does not mean lossless or copy-only export. A 0.1-second marker adjustment describes the UI controls, not a guarantee of frame-perfect output on every source. Preview and player selection can be used without the helper; **MP4 export requires it**.

## Troubleshooting

- **No such native application:** extract the entire package and rerun `Installa helper.cmd` as the same Windows user running Firefox. Keep the folder in place, then reopen Firefox and check the connection.
- **FFmpeg/ffprobe missing:** add the folder containing both executables to PATH, reopen Firefox, then check the connection again. The bundle does not install FFmpeg for you.
- **A site fails to export:** try a short interval from an ordinary downloadable MP4. Site access, authentication, expiring URLs and yt-dlp compatibility can affect a particular source. DRM is unsupported.
- **Updating an older copy:** install the newer signed XPI with the same extension ID and register the helper from the new extracted package. An automatic-update toggle does not read files from your local project folder. This self-distributed 1.2.0 XPI has no automatic update URL; use signed releases to update manually.

Report a reproducible problem in [Issues](https://github.com/FlamingFury28/video-clipper/issues). Include versions and the visible error; do not post cookies, tokens, private URLs or personal media.

## Distribution

This repository contains public documentation and installable release assets. The project's Python sources and development repository remain private. Firefox extensions inherently ship JavaScript inside their XPI. Third-party components retain their own licenses; see **THIRD-PARTY-NOTICES.md**, `THIRD-PARTY/` and the bundled dependency notices. The third-party source archives are unmodified upstream material, not the Video Clipper project sources.
