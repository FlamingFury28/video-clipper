<img src="assets/video-clipper.svg" width="72" height="72" alt="Video Clipper">

# Video Clipper — Trim & Crop Video

Turn a moment from a web video into an MP4 on your computer. Mark IN/OUT, preview the selection, then save. Combine several moments into one video or export each part separately. Crop directly over the original player, choose a phone format, adjust audio and add your watermark.

**English and Italian**, with automatic browser-language selection and an immediate language switch in Settings.

**[Install for Firefox](https://addons.mozilla.org/firefox/addon/video-clipper-in-out-mp4/)** · **[Download Windows helper installer](https://github.com/FlamingFury28/video-clipper/releases/download/helper-v1.8.3/VideoClipper-Helper-1.8.3-Windows-Setup.exe)** · **[English setup guide](INSTALL.md)** · **[Guida italiana](INSTALLAZIONE.md)**

## Start clipping

1. Install the extension from Mozilla Add-ons. First installation opens **Guided setup**.
2. On Windows x64, download the helper installer above and click **Install**. It prepares a permanent folder, connects Firefox and reuses installed video tools. If tools are missing, it can download a fixed, SHA-256-verified FFmpeg package from gyan.dev (about 105 MB). No administrator access, Python installation or manual PATH changes.
3. Return to **Settings → Guided setup → Check connection**, choose an output folder, then try a short clip.

**1.12.12 + helper 1.8.3 fix native Firefox MP4 timing.** When video starts after audio, saving up to the duration shown by Firefox could fail, and shorter clips could contain earlier frames. The verified video timeline is now aligned without moving audio or changing your markers. **Update both the extension and helper for this fix.**

**Already installed in Firefox?** Open **Add-ons and themes → gear menu → Check for Updates**. For a signed XPI already downloaded, choose **Install Add-on From File** in the same menu. Keep the installed extension: its settings are preserved. Firefox controls installation and catalog update availability.

| Download | Use |
|---|---|
| [Firefox extension 1.12.12](https://github.com/FlamingFury28/video-clipper/releases/download/v1.12.12/VideoClipper-1.12.12-signed.xpi) | Mozilla-signed permanent installation |
| [Windows x64 guided installer](https://github.com/FlamingFury28/video-clipper/releases/download/helper-v1.8.3/VideoClipper-Helper-1.8.3-Windows-Setup.exe) | Recommended helper setup; English / Italiano |
| [Windows portable helper ZIP](https://github.com/FlamingFury28/video-clipper/releases/download/helper-v1.8.3/VideoClipper-Helper-1.8.3-Windows.zip) | Advanced manual installation |
| [Linux x86_64 helper](https://github.com/FlamingFury28/video-clipper/releases/download/helper-v1.8.3/VideoClipper-Helper-1.8.3-Linux-x86_64.tar.gz) | Extract and run installa-helper.sh; system FFmpeg required |
| [Chrome / Edge extension](https://github.com/FlamingFury28/video-clipper/releases/download/v1.12.12/VideoClipper-1.12.12-Chromium.zip) | Unpacked desktop installation; no store publication |
| [SHA-256 checksums](https://github.com/FlamingFury28/video-clipper/releases/download/v1.12.12/VideoClipper-1.12.12-SHA256SUMS.txt) | Verify downloaded packages |

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

The previous signed release reproduces this MP4 discrepancy in isolated Firefox. Actual browser frames and audio establish the timeline; full, partial, joined and separate exports are checked independently on Windows Firefox 142 and the signed 1.12.12 after restart on Windows and Ubuntu Firefox 158. Truly invalid intervals remain rejected. All 92 JavaScript suites and 496 Python tests pass (six environment skips); twelve Chromium/native export checks pass. Ten of fourteen extension files are unchanged. Both helper binaries are rebuilt and verified; installer source, video tools and upstream notices are reused with matching hashes. No new permissions, session changes or personal browser profiles are involved. The guided installer is for **Windows x64**. Linux uses the archive and system FFmpeg; Snap/Flatpak helper access is unverified. No verified helper package is available for macOS, Android or iOS.

Some sites require optional, revocable per-site session access in the authenticated browser context. Advanced search and session access are separate. No other browser profile is read. DRM, live streams and closed shadow roots are unsupported. A full source video may need downloading before trimming. “Original” quality is not lossless. Website compatibility is not universal.

## Privacy and verification

Conversion runs locally. There is no Video Clipper cloud editing or analytics service. Preferences, language choice, projects, watermarks and history stay on your device. Session values are excluded from exported diagnostic reports. Optional version checks contact GitHub; the installer contacts the FFmpeg vendor only when missing tools are requested. Read [Privacy](PRIVACY.md).

The XPI is Mozilla signed. The helper/installer have no separate Authenticode signature; checksums and verification metadata are supplied. This repository contains public documentation and downloads. Project Python sources remain private.

[Changes](CHANGELOG.md) · [Verification](VERIFICATION.json) · [Third-party notices](THIRD-PARTY-NOTICES.md) · [Report an issue](https://github.com/FlamingFury28/video-clipper/issues)
