# Install Video Clipper

[Italiano](INSTALLAZIONE.md) · [Firefox add-on](https://addons.mozilla.org/firefox/addon/video-clipper-in-out-mp4/) · [Downloads](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.13.19)

Use the Mozilla-signed direct extension **1.13.19** and helper **1.9.134**. The Mozilla catalog currently offers 1.13.8. The extension and helper update separately; selective download is enabled by default for supported sources.

If you have helper 1.9.1 or older, update the helper as well: updating only the extension does not include these fixes.

## Windows — recommended

1. Install the [signed Firefox extension 1.13.19](https://github.com/FlamingFury28/video-clipper/releases/download/v1.13.19/VideoClipper-1.13.19-signed.xpi) using Firefox’s **Install Add-on From File** menu. Its first-run page opens **Guided setup**. You can reopen it from Settings at any time.
2. [Download the Windows x64 installer](https://github.com/FlamingFury28/video-clipper/releases/download/helper-v1.9.134/VideoClipper-Helper-1.9.134-Windows-Setup.exe), open it and click **Install**. Firefox is selected by default; select Chrome/Edge only if you use them.
3. Return to **Settings → Guided setup → Check connection**. Choose the folder where you want to save clips. Open a video, activate Video Clipper and test a short interval.

The installer works for the current Windows account, under its local Programs/VideoClipper folder. It needs no administrator access or separate Python installation. It registers the helper automatically and preserves previous helper files. If browser registration fails, the previous connection is restored.

Installed FFmpeg/ffprobe and encoders are reused when healthy. Otherwise, leave **Prepare video tools automatically if missing** checked: the installer downloads about 105 MB directly from gyan.dev, verifies the exact size and SHA-256, then prepares tools beside the helper. No PATH changes or manual extraction. The original vendor download and license remain in the installed folder. If you decline the download, both tools and libx264/AAC must already be available.

The installer is not Authenticode signed. Download it from this repository and compare [SHA-256 checksums](https://github.com/FlamingFury28/video-clipper/releases/download/helper-v1.9.134/VideoClipper-Helper-1.9.134-SHA256SUMS.txt). It does not bypass Windows security controls. If setup fails, run it again after resolving the reported connection/disk problem. Keep a working old helper folder until the replacement is verified.

If Video Clipper was open during setup, close and reopen its panel. Reopen Firefox if it retains an old helper connection. The installer does not close the browser or modify its profiles.

## Language

In **Settings → General → Language**, choose **Automatic**, **Italiano** or **English**. Automatic follows the browser UI language: Italian for Italian locales, English otherwise. The choice applies immediately and is retained. Video titles, custom names, paths and site content are preserved.

## Linux x86_64

[Download the helper archive](https://github.com/FlamingFury28/video-clipper/releases/download/helper-v1.9.134/VideoClipper-Helper-1.9.134-Linux-x86_64.tar.gz). Extract it in full to a permanent folder and run `./installa-helper.sh firefox` as the user running Firefox. Do not use sudo for helper registration. Provide FFmpeg and ffprobe with libx264/AAC through your system's package manager, then reopen Firefox and run **Check connection**.

Moving the helper folder requires registration again. Keep the bundled files together. Snap/Flatpak browser access to the native helper has not been verified.

## Chrome and Edge

Extract the [Chromium extension ZIP](https://github.com/FlamingFury28/video-clipper/releases/download/v1.13.3/VideoClipper-1.13.3-Chromium.zip) to a stable folder. In `chrome://extensions` or `edge://extensions`, enable developer mode and **Load unpacked** that folder.

On Windows, choose Chrome/Edge in the guided helper installer. Registering Firefox alone does not connect the other browsers. The portable helper can also register with `VideoClipperHelper.exe --install --browser chrome` or `--browser edge`. No Chrome Web Store or Edge Add-ons publication is claimed.

No verified helper package is currently provided for macOS, Android or iOS.

## First save and troubleshooting

Choose the intended video, mark IN and OUT, preview, then save. In **Clip → Export**, choose joined/separate output, format, crop and audio. Choose a language and naming rules in Settings.

Use **Check connection** for helper/tools/output-folder problems. **Diagnostics** checks the selected player and optional permissions, and exports a report without cookie values, source URLs, video titles or local paths. For a site that needs authentication, enable optional per-site session access only in the browser context where you are logged in. Advanced source search is a separate permission.

Do not delete a registered helper folder before a replacement works. For portable installations, the package includes installation-status and rollback commands. Clearing history removes references, not saved clips. Read [Privacy](PRIVACY.md) and the compatibility limits in [README](README.md).
