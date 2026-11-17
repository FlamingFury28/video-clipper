<img src="assets/video-clipper.svg" width="72" height="72" alt="Video Clipper">

# Video Clipper — Trim & Crop Video

Turn a moment from a web video into an MP4 on your computer. Mark IN/OUT, preview the selection, then save. Combine several moments into one video or export each part separately. Crop directly over the original player, choose a phone format, adjust audio and add your watermark.

**English and Italian**, with automatic browser-language selection and an immediate language switch in Settings.

**[Install for Firefox](https://addons.mozilla.org/firefox/addon/video-clipper-in-out-mp4/)** · **[Download Windows helper installer](https://github.com/FlamingFury28/video-clipper/releases/download/helper-v1.9.190/VideoClipper-Helper-1.9.190-Windows-Setup.exe)** · **[English setup guide](INSTALL.md)** · **[Guida italiana](INSTALLAZIONE.md)**

## Start clipping

1. Install the extension from Mozilla Add-ons. First installation opens **Guided setup**.
2. On Windows x64, download the helper installer above and click **Install**. It prepares a permanent folder, connects Firefox and reuses installed video tools. If tools are missing, it can download a fixed, SHA-256-verified FFmpeg package from gyan.dev (about 105 MB). No administrator access, Python installation or manual PATH changes.
3. Return to **Settings → Guided setup → Check connection**, choose an output folder, then try a short clip.

**Install Firefox extension 1.13.45 and helper 1.9.190.** Selective download is the default for supported MP4, WebM, HLS and DASH videos.

Fixes a selective DASH save when the selected Shaka player changes AAC configuration in a scene that has not been buffered. With helper 1.9.190, Video Clipper can use the neighboring original segments if it observed the selected player from startup and can verify the audio boundary. Joined and separate clips keep their markers. A failed buffered export also returns the player to its previous position.

The XVideos HLS source detection and full failed-project recovery delivered in 1.13.38 remain included.

**Already installed in Firefox?** Open **Add-ons and themes → gear menu → Check for Updates**. For a signed XPI already downloaded, choose **Install Add-on From File** in the same menu. Keep the installed extension: its settings are preserved. Firefox controls installation and catalog update availability.

| Download | Use |
|---|---|
| [Firefox extension 1.13.45](https://github.com/FlamingFury28/video-clipper/releases/download/v1.13.45/VideoClipper-1.13.45-signed.xpi) | Mozilla-signed permanent installation |
| [Windows x64 guided installer](https://github.com/FlamingFury28/video-clipper/releases/download/helper-v1.9.190/VideoClipper-Helper-1.9.190-Windows-Setup.exe) | Recommended helper setup; English / Italiano |
| [Windows portable helper ZIP](https://github.com/FlamingFury28/video-clipper/releases/download/helper-v1.9.190/VideoClipper-Helper-1.9.190-Windows.zip) | Advanced manual installation |
| [Linux x86_64 helper](https://github.com/FlamingFury28/video-clipper/releases/download/helper-v1.9.190/VideoClipper-Helper-1.9.190-Linux-x86_64.tar.gz) | Extract and run installa-helper.sh; system FFmpeg required |
| [Chrome / Edge extension](https://github.com/FlamingFury28/video-clipper/releases/download/v1.13.13/VideoClipper-1.13.13-Chromium.zip) | Unpacked desktop installation; no store publication |
| [Extension SHA-256 checksums](https://github.com/FlamingFury28/video-clipper/releases/download/v1.13.45/VideoClipper-1.13.45-SHA256SUMS.txt) | Verify downloaded packages |

[Helper 1.9.190 SHA-256 checksums](https://github.com/FlamingFury28/video-clipper/releases/download/helper-v1.9.190/VideoClipper-Helper-1.9.190-SHA256SUMS.txt) verify the new helper packages. The signed 1.13.45 package and its checksums are published separately.

Extension 1.13.41 and helper 1.9.188 improve selective clipping from qualified legacy HLS H.264 players, including the first displayed frame. Reordered initial decode samples and distant parts preserve the native video/AAC timeline. Joined and separate exports are verified; missing source audio warns without blocking saving. Projects, queue, markers and output settings survive upgrade and recovery. Update both components for the IN=0 correction. This does not claim universal website or format support.

The Opus corrections already verified in 1.9.184 remain included:

Helper 1.9.184 adds selective saving for qualified DASH videos whose Opus audio spans several periods. It keeps the original audio continuity and precise image timestamps, including a boundary inside an audio packet. Single clips and joined parts are verified through the normal Save button without downloading the full source. Original PCM and final AAC were checked independently, including native Firefox 160 playback on Windows and Linux. If extension 1.13.39 is installed, update only the helper. Unqualified formats still require an explicit compatibility choice.

The HLS corrections already verified in 1.9.183 remain included:

Helper 1.9.183 corrects the IN/OUT clock for qualified XVideos clear HLS sources with H.264 video without B frames. It retains the image already visible at IN, preserves original audio delays and supports joined or separate parts. Actual compiled Windows/Linux helpers were checked with permanently installed Firefox 142/160; the long-cut reference verifies all 3,061 video frames and 5,740 AAC packets. Other codecs and reordered streams retain their existing bounded paths. If extension 1.13.39 is installed, update only the helper. Support is not universal; full-source compatibility remains an explicit setting.

Helper 1.9.182 introduced selective clipping across qualified clear DASH periods with H.264 video and AAC LC mono/stereo audio. It preserves native timing at early and late transitions, retains valid 44.1 kHz edge samples and supports one joined file or separate files. Actual Firefox 142/160 exports were verified on Windows and Linux, including three-period stereo sources and Shaka/dash.js players. The older HLS corrections from helper 1.9.181 remain included. If extension 1.13.39 is already installed, update only the helper for these DASH fixes. Website and format support is not universal.

## Preserve your cuts and recover a failed save

Version 1.13.38 expands the projects archive from 40 to 200 entries without deleting existing work. In **Clip → Project and shortcuts**, use **Save a copy of cuts** for a local JSON containing all ordered ranges, the active part and duration, even when project storage is unavailable. **Load cuts onto this video** explicitly restores those ranges after checking the current video and duration; this file does not include output settings or source identity. Private-window cuts can be exported and imported without creating persistent projects. Existing saved projects retain their export settings. Older matching XVideos drafts can use **Restore onto this video** to reopen the editor without starting a download. If a save fails, its status is shown instead of a misleading success.

Version 1.13.38 keeps all parts and export settings of failed attempts before waiting for the player. A lost or slow response no longer discards the plan or replaces the original settings with later changes. **Resume save** reuses the original composition without re-entering times, including after reload. **Settings → Recovery → Recover failed saves** permits one automatic retry for verified recoverable errors on the same selected video. For a player without a stable identity, use **Resume on this video** on its saved project. Interrupted jobs with uncertain outcomes require explicit resume. Update the existing extension to preserve projects and queue entries.

## Clips from several videos

1. Mark a part and choose **Add to collection** in the Clip tab. Wait for it to be saved.
2. Open another video in the same tab and add its part. You can leave the previous page: the clip is already an MP4 on your device.
3. Open **Collection**, reorder the clips, name the export, and choose **One file** or **Separate files**.

Up to 40 clips can be collected. Joined output fits the first clip without stretching the others; silent clips remain silent. Individual saved MP4s are retained even when you export a joined file. Removing an entry only removes it from the collection.

Firefox may revoke temporary page access on full navigation. Use **Keep active on this site** to explicitly allow the panel to reopen on that site, or reopen it from the extension button. Saved clips are retained either way. This permission does not enable browser-session sharing.

## Make it yours

- **Precise parts:** type times, drag IN/OUT, adjust with configurable steps, undo, preview and reorder.
- **One video or several files:** join parts or save numbered MP4 files. Existing files are not overwritten.
- **Crop on the page:** move or resize a simple rectangle over the original video. Choose Original/free, 9:16 phone, 16:9, 1:1 or 4:5 without stretching.
- **Audio and watermark:** change export volume, remove audio, remember your last choice and position a local logo.
- **Names and profiles:** choose the title source, fallback name, prefix/suffix and filename template. Save profiles and projects or queue exports.
- **Fits your browser:** use the Firefox theme palette, native light/dark colors and customizable shortcuts. History opens separately.
- **Help when needed:** configuration checks, privacy-conscious diagnostic reports and bounded source/context recovery.

## Compatibility and limits

The extension works with accessible HTML5 players, embedded frames, open shadow roots and dynamic pages. Choose another player manually when necessary. Source identity and duration checks help prevent saving the wrong video.

Helper 1.9.180 was tested with permanently installed signed extension 1.13.37 on Firefox 142/160, Windows and Linux: eight deterministic MP4/HLS exports, three real Beeg one-click saves, eight native cases, two previews and isolated installer preparation. Windows Firefox 160 saved the complete requested 09:47.832–11:19.498 interval with H.264 video and AAC audio; Windows Firefox 142 and Linux Firefox 160 saved a two-second excerpt from the same IN point. Seven new API tests and nine parent transport tests pass. Forty-six unchanged helper modules retain prior evidence; their older tests are not claimed as new runs. The existing YouJizz native IN-frame offset remains unchanged. The guided installer is for Windows x64. Linux uses system FFmpeg; Snap/Flatpak, macOS and mobile helpers remain unverified. Windows HEVC browser export remains unverified.

Some sites require optional, revocable per-site session access in the authenticated browser context. Advanced search and session access are separate. No other browser profile is read. DRM, live streams and closed shadow roots are unsupported. Unsupported sources can require selecting full-source compatibility in Settings. Selective mode does not silently start a complete download. “Original” quality is not lossless. Website compatibility is not universal.

## Privacy and verification

Conversion runs locally. There is no Video Clipper cloud editing or analytics service. Preferences, language choice, projects, watermarks, history and the collection stay on your device. For a tab you authorize, supported MediaSource capture keeps a bounded temporary local cache of encoded fragments; export validates that they belong to the selected player. The collection stores local file references, fingerprints, names and durations, without source URLs or cookies. Session values are excluded from exported diagnostic reports. Optional version checks contact GitHub; the installer contacts the FFmpeg vendor only when missing tools are requested. Read [Privacy](PRIVACY.md).

The XPI is Mozilla signed. The helper/installer have no separate Authenticode signature; checksums and verification metadata are supplied. This repository contains public documentation and downloads. Project Python sources remain private.

[Changes](CHANGELOG.md) · [Helper verification](HELPER-VERIFICATION-1.9.180.md) · [Older extension verification](VERIFICATION.json) · [Third-party notices](THIRD-PARTY-NOTICES.md) · [Report an issue](https://github.com/FlamingFury28/video-clipper/issues)

Helper 1.9.188 adds verified selective DASH saves across H.264 configuration or resolution changes, keeping one stable output size for joined or separate parts. It also fixes valid AAC clips ending at the original source tail on Windows and Linux. Selected fragments, decode neighbors and small original configuration witnesses are fetched; no implicit complete-source fallback. Website and format support remains limited to verified paths.
