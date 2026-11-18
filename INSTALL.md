# Install Video Clipper

[Italiano](INSTALLAZIONE.md) · [Firefox add-on](https://addons.mozilla.org/firefox/addon/video-clipper-in-out-mp4/) · [Downloads](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.13.51)

Install Firefox extension **1.13.51** from Mozilla Add-ons and helper **1.9.192** from GitHub.

Save a clip on a compatible multi-period DASH video even when playback is in a different period. Video Clipper keeps your cuts and playback position for both joined and separate MP4 files. Install helper 1.9.192 for this change.

Helper 1.9.188 adds verified selective DASH saves across H.264 configuration or resolution changes, keeping one stable output size for joined or separate parts. It also fixes valid AAC clips ending at the original source tail on Windows and Linux. Selected fragments, decode neighbors and small original configuration witnesses are fetched; no implicit complete-source fallback. Website and format support remains limited to verified paths.

Extension 1.13.41 and helper 1.9.188 improve selective clipping from qualified legacy HLS H.264 players, including the first displayed frame. Reordered initial decode samples and distant parts preserve the native video/AAC timeline. Joined and separate exports are verified; missing source audio warns without blocking saving. Projects, queue, markers and output settings survive upgrade and recovery. Update both components for the IN=0 correction. This does not claim universal website or format support.

The Opus corrections already verified in 1.9.184 remain included:

Helper 1.9.184 adds selective saving for qualified DASH videos whose Opus audio spans several periods. It keeps the original audio continuity and precise image timestamps, including a boundary inside an audio packet. Single clips and joined parts are verified through the normal Save button without downloading the full source. Original PCM and final AAC were checked independently, including native Firefox 160 playback on Windows and Linux. If extension 1.13.39 is installed, update only the helper. Unqualified formats still require an explicit compatibility choice.

The HLS corrections already verified in 1.9.183 remain included:

Helper 1.9.183 corrects the IN/OUT clock for qualified XVideos clear HLS sources with H.264 video without B frames. It retains the image already visible at IN, preserves original audio delays and supports joined or separate parts. Actual compiled Windows/Linux helpers were checked with permanently installed Firefox 142/160; the long-cut reference verifies all 3,061 video frames and 5,740 AAC packets. Other codecs and reordered streams retain their existing bounded paths. If extension 1.13.39 is installed, update only the helper. Support is not universal; full-source compatibility remains an explicit setting.

Helper 1.9.182 introduced selective clipping across qualified clear DASH periods with H.264 video and AAC LC mono/stereo audio. It preserves native timing at early and late transitions, retains valid 44.1 kHz edge samples and supports one joined file or separate files. Actual Firefox 142/160 exports were verified on Windows and Linux, including three-period stereo sources and Shaka/dash.js players. The older HLS corrections from helper 1.9.181 remain included. If extension 1.13.39 is already installed, update only the helper for these DASH fixes. Website and format support is not universal.

After updating, **Check connection** should report helper **1.9.192**. The XPI alone does not update the installed helper.

Version 1.13.38 keeps all parts and export settings of failed attempts before waiting for the player. A lost or slow response no longer discards the plan or replaces the original settings with later changes. **Resume save** reuses the original composition without re-entering times, including after reload. **Settings → Recovery → Recover failed saves** permits one automatic retry for verified recoverable errors on the same selected video. For a player without a stable identity, use **Resume on this video** on its saved project. Interrupted jobs with uncertain outcomes require explicit resume. Update the existing extension to preserve projects and queue entries.

The XVideos HLS source detection and full failed-project recovery delivered in 1.13.38 remain included.

Version 1.13.38 expands the projects archive from 40 to 200 entries without deleting existing work. In **Clip → Project and shortcuts**, use **Save a copy of cuts** for a local JSON containing all ordered ranges, the active part and duration, even when project storage is unavailable. **Load cuts onto this video** explicitly restores those ranges after checking the current video and duration; this file does not include output settings or source identity. Private-window cuts can be exported and imported without creating persistent projects. Existing saved projects retain their export settings. Older matching XVideos drafts can use **Restore onto this video** to reopen the editor without starting a download. If a save fails, its status is shown instead of a misleading success.

## Windows — recommended

1. Install [Video Clipper from Mozilla Add-ons](https://addons.mozilla.org/firefox/addon/video-clipper-in-out-mp4/). Its first-run page opens **Guided setup**. You can reopen it from Settings at any time.
2. [Download the Windows x64 installer](https://github.com/FlamingFury28/video-clipper/releases/download/helper-v1.9.192/VideoClipper-Helper-1.9.192-Windows-Setup.exe), open it and click **Install**. Firefox is selected by default; select Chrome/Edge only if you use them.
3. Return to **Settings → Guided setup → Check connection**. Choose the folder where you want to save clips. Open a video, activate Video Clipper and test a short interval.

The installer works for the current Windows account, under its local Programs/VideoClipper folder. It needs no administrator access or separate Python installation. It registers the helper automatically and preserves previous helper files. If browser registration fails, the previous connection is restored.

Installed FFmpeg/ffprobe and encoders are reused when healthy. Otherwise, leave **Prepare video tools automatically if missing** checked: the installer downloads about 105 MB directly from gyan.dev, verifies the exact size and SHA-256, then prepares tools beside the helper. No PATH changes or manual extraction. The original vendor download and license remain in the installed folder. If you decline the download, both tools and libx264/AAC must already be available.

The installer is not Authenticode signed. Download it from this repository and compare [SHA-256 checksums](https://github.com/FlamingFury28/video-clipper/releases/download/helper-v1.9.192/VideoClipper-Helper-1.9.192-SHA256SUMS.txt). It does not bypass Windows security controls. If setup fails, keep its exact error code. A failed helper check or incomplete package is different from a failed tools download; use the displayed details when choosing what to retry. Keep a working old helper folder until the replacement is verified.

If Video Clipper was open during setup, close and reopen its panel. Reopen Firefox if it retains an old helper connection. The installer does not close the browser or modify its profiles.

## Language

In **Settings → General → Language**, choose **Automatic**, **Italiano** or **English**. Automatic follows the browser UI language: Italian for Italian locales, English otherwise. The choice applies immediately and is retained. Video titles, custom names, paths and site content are preserved.

## Linux x86_64

[Download the helper archive](https://github.com/FlamingFury28/video-clipper/releases/download/helper-v1.9.192/VideoClipper-Helper-1.9.192-Linux-x86_64.tar.gz). Extract it in full to a permanent folder and run `./installa-helper.sh firefox` as the user running Firefox. Do not use sudo for helper registration. Provide FFmpeg and ffprobe with libx264/AAC through your system's package manager, then reopen Firefox and run **Check connection**.

Moving the helper folder requires registration again. Keep the bundled files together. Snap/Flatpak browser access to the native helper has not been verified.

## Chrome and Edge

Extract the [Chromium extension ZIP](https://github.com/FlamingFury28/video-clipper/releases/download/v1.13.13/VideoClipper-1.13.13-Chromium.zip) to a stable folder. In `chrome://extensions` or `edge://extensions`, enable developer mode and **Load unpacked** that folder.

On Windows, choose Chrome/Edge in the guided helper installer. Registering Firefox alone does not connect the other browsers. The portable helper can also register with `VideoClipperHelper.exe --install --browser chrome` or `--browser edge`. This separate Chromium build is older than the Firefox release; the new Firefox MediaSource capture is not claimed for it. No Chrome Web Store or Edge Add-ons publication is claimed.

No verified helper package is currently provided for macOS, Android or iOS.

## First save and troubleshooting

Choose the intended video, mark IN and OUT, preview, then save. In **Clip → Export**, choose joined/separate output, format, crop and audio. Choose a language and naming rules in Settings.

Use **Check connection** for helper/tools/output-folder problems. **Diagnostics** checks the selected player and optional permissions, and exports a report without cookie values, source URLs, video titles or local paths. For a site that needs authentication, enable optional per-site session access only in the browser context where you are logged in. Advanced source search is a separate permission.

Do not delete a registered helper folder before a replacement works. For portable installations, the package includes installation-status and rollback commands. Clearing history removes references, not saved clips. Read [Privacy](PRIVACY.md) and the compatibility limits in [README](README.md).
