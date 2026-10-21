# Video Clipper — IN/OUT MP4 Trimmer for Firefox

Choose an HTML5 player, mark IN/OUT, preview the interval and export a local MP4 through the Windows companion helper. The interface is in Italian.

**Extension 1.3.1 is being submitted to the public Mozilla Add-ons catalog. Availability and automatic updates depend on Mozilla review. Export requires helper 1.3.0; the extension update does not update the helper.**

[Firefox add-on](https://addons.mozilla.org/firefox/addon/video-clipper-in-out-mp4/) · [Windows helper 1.3.0](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.3.1) · [Istruzioni italiane](INSTALLAZIONE.md) · [Privacy](PRIVACY.md) · [Changes](CHANGELOG.md)

## Install

1. Provide FFmpeg and ffprobe with libx264/AAC on Windows PATH. Start from the [official FFmpeg download page](https://ffmpeg.org/download.html#build-windows). They are not bundled. Reopen Firefox after changing PATH.
2. Download **VideoClipper-1.3.0-Windows.zip** from the release linked above and extract every file to a permanent folder.
3. Run **Installa helper.cmd** as the Windows user running Firefox. Keep the executable together with its `_internal` folder; if you move it, register it again. Python and helper dependencies are bundled. Administrator access is not required.
4. Install or update Video Clipper through the Mozilla Add-ons page when version 1.3.1 is approved. The helper ZIP contains no unsigned XPI to install. Users of an older self-distributed XPI need to install the AMO version when available.
5. Open the extension preferences and use **Verifica configurazione**. Set the destination and reload video pages that were open before upgrading.

The helper is not Authenticode signed. Do not disable Windows protections. Firefox 142+ and Windows 11 x64 are required for full export; the Windows helper is not supported on macOS, Linux or Android.

## Choose, trim and save

Activate Video Clipper from the toolbar, choose the intended video with **Cambia**, set **IN/OUT**, press **Anteprima**, then **Salva clip**. The compact editor keeps actions reachable and settings/history collapsible. Saved results offer open-file, open-folder and copy-path actions.

Timestamp repair runs on Enter or leaving the field, not while typing. Values beyond the duration are clamped, excess seconds/minutes are carried, milliseconds are rounded and ambiguous text restores the previous value. IN stays before OUT; only the edited marker changes. Undo restores actual range changes.

The chosen player's sources are tried first. Discovery includes linked videos, accessible dynamic/nested frames, inherited about:blank/srcdoc context, JW Player, Video.js public APIs and scoped X/Twitter sources. Ambiguous page extraction asks for a player or a single-video page. **Cerca altri video** preserves the selected range.

**Pannello e sessione → Usa la sessione Firefox per questo sito** is off by default. It asks for the displayed domains and cookie permission, reads the selected tab's cookie store and the top-level site's partition, and passes scoped cookies only to the local export job. Revoke consent in extension settings. Only consent is stored; temporary cookie files are cleaned on success, error and cancellation, with failures reported.

## Limits and checks

Export depends on downloadable media and yt-dlp support. Synthetic MP4, HLS and DASH exports were checked for the selected video, interval/duration and audio. The exact XPI passed six cases in isolated Firefox 158, including actual native-helper export; all 37 JavaScript suites passed. The helper suite ran 298 Python tests (296 passed, two Windows symlink-privilege skips). Additional live websites remain unverified.

DRM, live streams and closed shadow roots are unsupported. CSS/SVG-transformed iframes can affect floating-panel alignment. Resolution limits do not promise lossless export or frame-identical output on every source. UI/preview can be used without the helper; exporting requires helper 1.3.0 and FFmpeg/ffprobe.

## Troubleshooting and distribution

If Firefox reports an older or missing helper, extract the updated Windows package and run **Installa helper.cmd**, then check the configuration. If FFmpeg is missing, correct PATH and reopen Firefox. Expiring sources, authentication, CDN access and extractor support can still prevent exports. Report a reproducible problem in [Issues](https://github.com/FlamingFury28/video-clipper/issues), without cookies, tokens, private URLs or personal media.

This repository contains public documentation and compiled release assets. Project Python sources remain private. Third-party notices and unmodified upstream source archives are supplied with the helper. GitHub-generated source archives contain only this public documentation repository.
