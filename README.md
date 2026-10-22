# Video Clipper — IN/OUT MP4 Trimmer for Firefox

Choose an HTML5 video, mark IN/OUT, preview the interval and save a local MP4. Join multiple intervals from the same video in list order, with optional reordering and selected-part preview. The interface is in Italian.

**Published release: [1.4.6](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.4.6), with Mozilla-signed extension 1.4.6 and verified Windows helper 1.4.3. Update both components. Updating the extension does not update the helper.**

[Windows ZIP](https://github.com/FlamingFury28/video-clipper/releases/download/v1.4.6/VideoClipper-1.4.6-Windows.zip) · [Signed XPI](https://github.com/FlamingFury28/video-clipper/releases/download/v1.4.6/VideoClipper-1.4.6-signed.xpi) · [SHA-256 checksums](https://github.com/FlamingFury28/video-clipper/releases/download/v1.4.6/VideoClipper-1.4.6-SHA256SUMS.txt) · [Istruzioni italiane](INSTALLAZIONE.md) · [Privacy](PRIVACY.md) · [Changes](CHANGELOG.md)

## Install or upgrade

Requires **Windows 11 x64, Firefox 142+ and FFmpeg/ffprobe with libx264/AAC on PATH**. Python, yt-dlp, EJS and Deno are bundled. FFmpeg/ffprobe are separate; reopen Firefox after changing PATH. Start at the [official FFmpeg download page](https://ffmpeg.org/download.html#build-windows).

1. Download **VideoClipper-1.4.6-Windows.zip** and extract every file to a permanent folder.
2. Run **Installa helper.cmd** as the Windows user running Firefox. Keep `VideoClipperHelper.exe` together with its `_internal` folder. Administrator access is unnecessary. Register the helper again if you move the folder.
3. In Firefox open `about:addons`, choose the gear menu → **Install Add-on From File**, and select **VideoClipper-1.4.6-signed.xpi** from the ZIP or the separate asset. This is a permanent signed installation.
4. Verify extension version **1.4.6**, use **Verifica configurazione** in preferences, select the destination and reload open video pages. The installed helper should report **1.4.3**.

If upgrading from 1.4.1, install the new XPI **and** register the new helper. If the extension is already 1.4.6, install/register helper 1.4.3 from this ZIP. Re-running the installer from an old ZIP leaves the old binary in use. Extension 1.4.5 requires helper 1.4.2 for v3; helper 1.4.1 does not satisfy that requirement.

The helper has no separate Authenticode signature. The extension XPI is signed by Mozilla. The Windows helper is not supported on macOS, Linux or Android.

## Use and source selection

Activate Video Clipper, choose the intended video, set IN/OUT, press **Anteprima**, then **Salva clip**. **Aggiungi parte** and **Salva video unito** create one MP4 from multiple intervals of the same video, including repeated or overlapping intervals. List order determines the result; reordering is optional. Preview plays only the selected part.

Timestamp correction runs on Enter or leaving a field. Check the resulting interval; ambiguous input restores the previous valid value. The panel can dock at a page edge, float on the video or use the Firefox sidebar. Preferences/history are collapsible; completed results provide file/folder and copy-path actions.

Selected-player sources take priority. This release improves Vidstack source detection, player-state changes, HLS/DASH download handling, audio selection and MP4 duration checks. Seeing a player or a successful preview does not guarantee an exportable source.

When needed, enable **Ricerca avanzata** for the site and play the intended video. Ambiguous candidates require an explicit selection. Source discovery and **Usa la sessione Firefox per questo sito** are separate optional permissions, initially off and revocable. For authenticated media, grant session access in the Firefox profile/context where you are authenticated. Cookie store and partition context are preserved; other profiles are not used to bypass consent.

A specifically identified audio track must map uniquely to a downloadable rendition; unresolved audio selection fails instead of silently substituting another language. Authenticated export may download the full source before trimming, requiring time, bandwidth and temporary disk space.

## Verified distribution and limits

The exact XPI and helper binary match their recorded verification hashes. Permanent installation and restart were checked with Firefox signature enforcement active in isolated profiles. Signed-extension exports with helper 1.4.3 passed on Firefox **142.0 (3 cases)** and **158.0.1 (6 cases)** with local MP4/HLS/DASH media. The helper binary also has **4 native checks** and **34 v3/refresh tests** recorded. These are local/synthetic checks; they do not certify every live website.

DRM, live streams and closed shadow roots are unsupported. Authentication, source expiry, CDN access and unsupported transport can still prevent export. A requested audio source that cannot be resolved causes an error; preview availability depends on the source.

## Mozilla distribution

Extension **1.4.6 is Self / Approved (unlisted)**. Its signed XPI is distributed in the GitHub release above. The separate catalog submission **1.4.2 remains Awaiting Review** in the authenticated Mozilla version manager checked on 22 October 2026. The storefront warns that it is not a public listing and is visible only with elevated permissions. Direct signing does not establish catalog publication.

The package has no custom automatic-update URL. Install future complete signed releases from [Releases](https://github.com/FlamingFury28/video-clipper/releases); catalog availability and update behavior are separate. The [Mozilla product page](https://addons.mozilla.org/firefox/addon/video-clipper-in-out-mp4/) is not the download route prescribed for this direct distribution.

For a missing/old helper, register the new package and check the reported version. For missing FFmpeg/ffprobe, correct PATH and reopen Firefox. Report reproducible errors in [Issues](https://github.com/FlamingFury28/video-clipper/issues) without cookies, tokens, private URLs or personal media.

Project Python sources remain private. Release assets contain the verified binary, signed extension, documentation and upstream licenses. GitHub-generated source archives contain this public documentation repository.
