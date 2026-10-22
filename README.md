# Video Clipper — IN/OUT MP4 Trimmer for Firefox

Choose an HTML5 player, mark IN/OUT, preview the interval and export a local MP4 through the Windows companion helper. The interface is in Italian.

**Verified on 22 October 2026: the latest published GitHub release is [v1.4.1](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.4.1), with signed extension 1.4.1 and Windows helper 1.4.1. Install both from that release. Updating the extension does not update the helper.**

| Distribution | Extension | Helper / status |
|---|---|---|
| Published GitHub release | 1.4.1, Mozilla signed | 1.4.1 included in the Windows ZIP |
| Mozilla direct distribution (Self / unlisted) | 1.4.5 approved | Release notes require 1.4.2; helper 1.4.1 fails the v3 version check |
| Latest Mozilla direct distribution (Self / unlisted) | 1.4.6 approved | Release notes require 1.4.3; no corresponding helper release found on GitHub |
| Mozilla catalog (listed) | 1.4.2 | Awaiting Review; public availability is not confirmed |

The authenticated [Mozilla version manager](https://addons.mozilla.org/en-US/developers/addon/video-clipper-in-out-mp4/versions/) distinguishes **Self / Approved** from the catalog submission. The storefront explicitly says it is not a public listing and is visible only with elevated permissions. The automated approval email for 1.4.5 does not establish catalog publication. Direct signing and catalog publication remain separate.

The [1.4.5 AMO notes](https://addons.mozilla.org/en-US/developers/addon/video-clipper-in-out-mp4/versions/6609010) require helper 1.4.2, and the [1.4.6 notes](https://addons.mozilla.org/en-US/developers/addon/video-clipper-in-out-mp4/versions/6609239) require 1.4.3. These developer pages require the author's access. Their approved XPI download links do not supply the Windows helper. Do not combine either extension with helper 1.4.1 expecting full compatibility; use a matching complete distribution when available. No Windows helper 1.4.2/1.4.3 GitHub asset was found in this check.

[Firefox add-on](https://addons.mozilla.org/firefox/addon/video-clipper-in-out-mp4/) · [Signed extension + Windows helper 1.4.1](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.4.1) · [Istruzioni italiane](INSTALLAZIONE.md) · [Privacy](PRIVACY.md) · [Changes](CHANGELOG.md)

## Install

1. Provide FFmpeg and ffprobe with libx264/AAC on Windows PATH. Start from the [official FFmpeg download page](https://ffmpeg.org/download.html#build-windows). They are not bundled. Reopen Firefox after changing PATH.
2. Download [VideoClipper-1.4.1-Windows.zip](https://github.com/FlamingFury28/video-clipper/releases/download/v1.4.1/VideoClipper-1.4.1-Windows.zip) from the release linked above and extract every file to a permanent folder.
3. Run **Installa helper.cmd** as the Windows user running Firefox. Keep the executable together with its `_internal` folder; if you move it, register it again. Python and helper dependencies are bundled. Administrator access is not required.
4. In Firefox open `about:addons`, choose the gear menu → **Install Add-on From File**, and select **VideoClipper-1.4.1-signed.xpi** from the complete ZIP or the separate release asset. This is a permanent signed installation; verify extension version 1.4.1. Catalog availability and future automatic updates must be checked separately.
5. Open the extension preferences and use **Verifica configurazione**. Set the destination and reload video pages that were open before upgrading.

The helper is not Authenticode signed. Do not disable Windows protections. Firefox 142+ and Windows 11 x64 are required for full export; the Windows helper is not supported on macOS, Linux or Android.

## Choose, trim and save

Activate Video Clipper from the toolbar, choose the intended video with **Cambia**, set **IN/OUT**, press **Anteprima**, then **Salva clip**. Use **Aggiungi parte** to prepare multiple intervals of the same video and **Salva video unito** to export them in list order. Reordering is optional; preview plays the selected part. Overlapping or repeated intervals are supported. The compact editor keeps actions reachable and settings/history collapsible. Saved results offer open-file, open-folder and copy-path actions.

Timestamp repair runs on Enter or leaving the field, not while typing. Values beyond the duration are clamped, excess seconds/minutes are carried, milliseconds are rounded and ambiguous text restores the previous value. IN stays before OUT; only the edited marker changes. Undo restores actual range changes.

The chosen player's sources are tried first. Discovery includes linked videos, accessible dynamic/nested frames, inherited about:blank/srcdoc context, JW Player, Video.js public APIs and scoped X/Twitter sources. Ambiguous page extraction asks for a player or a single-video page. **Cerca altri video** preserves the selected range.

**Pannello e sessione → Usa la sessione Firefox per questo sito** is off by default. It asks for the displayed domains and cookie permission, reads the selected tab's cookie store and the top-level site's partition, and passes scoped cookies only to the local export job. Revoke consent in extension settings. Only consent is stored; temporary cookie files are cleaned on success, error and cancellation, with failures reported.

## Limits and checks

Export depends on downloadable media and yt-dlp support. The published 1.4.1 release records permanent signed installation and restart, single export, and reordered multi-part export using its helper binary, with duration, video/audio order and Firefox playback checks on synthetic local media. These checks do not certify every live website.

The [previous audit recorded in the repository](https://github.com/FlamingFury28/video-clipper/commit/fcd7230891952809081efd801569a2da1e2e1a38) reports that the downloaded Mozilla 1.4.5 XPI matched the local signed release hash. The exact GitHub Windows ZIP matched GitHub's SHA-256 digest. Its helper binary reports 1.4.1 and advertises v3 capabilities; the 1.4.5 extension's actual `currentV3Helper` predicate rejects that version and raises `HELPER_UPDATE_REQUIRED` on the v3 export path. A constrained public legacy path exists, but this does not establish full compatibility. This was an artifact/capability check, not a new end-to-end browser export with the mixed pair.

The follow-up audit independently downloaded the GitHub 1.4.1 ZIP and XPI, matched both against the published SHA-256 checksums, verified the embedded helper executable hash and confirmed that the XPI inside the ZIP is byte-identical to the separate asset. The 1.4.1 XPI blocks joined export without `multi-part-export-v1`; some of its other helper-update messages still name 1.4.0. Use the documented 1.4.1 helper for this package.

The exact Mozilla 1.4.5 download URL returned HTTP 404 in this follow-up public-access check. Its code inspection and the authenticated AMO channel/release-note findings above are therefore attributed to the linked previous audit; they were not independently repeated here. This does not establish removal of the unlisted version. No new browser export test was run.

DRM, live streams and closed shadow roots are unsupported. CSS/SVG-transformed iframes can affect floating-panel alignment. Resolution limits do not promise lossless export or frame-identical output on every source. UI/preview can be used without the helper; exporting with the published 1.4.1 extension requires its helper 1.4.1 and FFmpeg/ffprobe.

## Troubleshooting and distribution

If Firefox reports an older or missing helper, check the extension version before selecting a package. Extract the complete matching Windows package and run **Installa helper.cmd**, then check the connection. For extension 1.4.5, reinstalling GitHub's helper 1.4.1 will not satisfy the v3 requirement; obtain the required helper from a verified complete distribution. If FFmpeg is missing, correct PATH and reopen Firefox. Expiring sources, authentication, CDN access and extractor support can still prevent exports. Report a reproducible problem in [Issues](https://github.com/FlamingFury28/video-clipper/issues), without cookies, tokens, private URLs or personal media.

This repository contains public documentation and compiled release assets. Project Python sources remain private. Third-party notices and unmodified upstream source archives are supplied with the helper. GitHub-generated source archives contain only this public documentation repository.

The AMO description still refers to extension 1.3.1, helper 1.3.0 and the v1.3.1 release. Those are historical instructions, not installation guidance for 1.4.5/1.4.6. This documentation update does not change AMO metadata or publication channels.
