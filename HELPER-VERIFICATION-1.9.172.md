# Helper 1.9.172 verification

Published binary packages: [helper-v1.9.172](https://github.com/FlamingFury28/video-clipper/releases/tag/helper-v1.9.172). This page summarizes local verification; it does not certify every website.

| Artifact | SHA-256 |
|---|---|
| Windows native helper | e99951c539a66ecb5c1a0d1037756bd3da0fa9ea47dc10775548742187be6bd0 |
| Linux x86_64 native helper | 784a98ab9e1fa4c534fecfe14f77beccdd17c8bb51a1631784b96dda97524143 |
| Windows installer | 53b34d7c43bb44959e322ae9f46af1535bff5636eaf320efe294b89a323ae4e6 |
| Windows ZIP | 3d679285f2c8b506fa1c96782ab123f789a50f49d65af84fc44a6add40e25ea7 |
| Linux archive | 75ecbd05becfb88f693d828ad4e8fafc58c42a62064daa646b4e0f8283a9e696 |

Actual binaries were tested through native messaging and with permanent, Mozilla-signed Firefox extensions after restart. Firefox 142 and 160 on Windows and Ubuntu 24.04/WSL produced the chosen MP4/HLS interval from the intended player on a two-video page. Both helpers also passed scoped synthetic-session, ambiguous-page rejection and legacy-protocol checks, plus real source-worker preview/export.

The signed 1.13.24 verification candidate exercised the new MediaSource path with encoded video/audio append chunks, real local IndexedDB and the actual helper on both systems. A single Save exported 51 correctly timed frames and correlated audio without additional HTTP requests during Save, using the approximately twelve seconds already loaded by the fixture. The reference video was ninety seconds long. Frame and PCM comparisons were independent of the exporter; Linux-generated output was compared by a separate Windows FFmpeg/NumPy oracle. This is a local fixture result, not a real-site bandwidth measurement.

Native binary cases additionally covered HTTP WebM end selections, missing audio, separate SourceBuffers and joined/separate parts. The Linux native reports explicitly deferred AV comparison; separate hash-bound independent checks verified all six outputs, including a selection ending at the loaded-fragment boundary. Missing audio produced a warning and a saved video.

The coordinated extension tests also preserved all eight project ranges and verified six multi-video collection cases: same-tab navigation, ordering, joined output, separate copies and persistent missing-file feedback. The public catalog counterpart changes only the manifest version from the tested signed candidate.

Windows setup was reproduced failing on the valid 574-file archive under the former fixed 400-file limit. The corrected installer verifies the exact version-pinned count and expanded size, the complete ZIP hash and the extracted helper hash. Payload verification and clean preparation with verified FFmpeg 8.1.2 passed in an isolated folder, with no browser registration. The actual binaries were not rebuilt for the wrapper fix.

Tests prevented audible output with a native null audio backend verified before media; system volume, personal Firefox profiles and existing browser registrations were unchanged. No real-site session consent was enabled. Firefox rejected the unsigned candidate and retained the signed extension after restart with signature enforcement active.

Limitations: some formats, HTTP servers or custom players do not qualify for selective export and may require the explicit full-source compatibility setting. Prior bytes for decoding, indices, keyframes and audio preroll can still be needed. DRM, live streams and closed shadow roots remain unsupported. New Firefox MediaSource capture is not claimed for the older Chromium ZIP. Snap/Flatpak and macOS/mobile helpers are unverified.

The XPI is Mozilla-signed. Windows helper/installer executables are not Authenticode-signed. Packages include known upstream notices and source archives for those dependencies; the Deno transitive-license inventory remains explicitly incomplete. Private project Python sources and workspace archives are excluded.
