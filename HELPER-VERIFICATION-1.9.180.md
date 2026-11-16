# Helper 1.9.180 — verification

Helper 1.9.180 fixes Beeg source resolution after its API changed: numeric API ids are normalized without changing the selected video identity, and the separate play-reference request supplies the HLS playlist. Updating the helper is sufficient for this fix; the signed 1.13.33 extension remains compatible. Existing YouJizz IN-frame timing limits remain documented.

Helper 1.9.180 was tested with permanently installed signed extension 1.13.33 on Firefox 142/160, Windows and Linux: eight deterministic MP4/HLS exports, three real Beeg one-click saves, eight native cases, two previews and isolated installer preparation. Windows Firefox 160 saved the complete requested 09:47.832–11:19.498 interval with H.264 video and AAC audio; Windows Firefox 142 and Linux Firefox 160 saved a two-second excerpt from the same IN point. Seven new API tests and nine parent transport tests pass. Forty-six unchanged helper modules retain prior evidence; their older tests are not claimed as new runs. The existing YouJizz native IN-frame offset remains unchanged. The guided installer is for Windows x64. Linux uses system FFmpeg; Snap/Flatpak, macOS and mobile helpers remain unverified. Windows HEVC browser export remains unverified.

The original public helper 1.9.179 reproduced SOURCE_UNAVAILABLE during resolve with HTTP 400 on the reported Beeg page. Canonical metadata requests succeeded without cookies, but the current response no longer includes HLS resources. The site's public JavaScript confirms a separate play-reference endpoint. The new adapter validates the metadata file id and relative playlist reference before media retrieval. Wrong ids and unrelated URLs are rejected; original public ids and request headers are retained.

Two early source-wrapper runs saved successfully but their test playback-state assertions failed during site startup. Those original failed reports are preserved. Final tests first establish a ready, paused player and verify the exact compiled binaries. The full requested Windows export contains 2,292 video frames at 25 fps, AAC audio and 91.68 seconds of media, reflecting frame boundaries. Both two-second excerpts contain 50 video frames and AAC audio. All three preserve IN/OUT and the paused player position.

Tests used isolated browser profiles with mandatory signature verification, permanent addon installation and restart. A forced null cubeb backend was checked with zero channels/output devices and parent/child native witnesses before media navigation. No personal profile, registry registration, system volume, consent or credential was changed. Installer verification used payload checking and isolated preparation with no registered browsers.

| Artifact | SHA-256 |
| --- | --- |
| Windows helper | 48f50a57b626e3e5c037c8b0bcbc03a51e631c333074af2b75fe42b667fbe590 |
| Linux helper | 121983f2aab802e4032c1ffb7d3eb3070c3446892b80ec55c8016387130bee83 |
| Windows ZIP | 73976cd9a997540c3e0b6ae2ae30cdb5ae928f6de2016ad45c2bf22e2325439f |
| Linux TAR | d7e3d9f59ee174f65265451ed7a795026eaf93fc5ee0f4e4857e12b10aca7df4 |
| Windows installer | f18dd05c539e4782c432a1b94ea69492919ec423736cdf9eb0ea6a6952da4f93 |

Upstream runtime payloads match helper 1.9.179 (529 Windows and 494 Linux files, with stdlib ZIP entries compared byte-for-byte). License notices are retained. Packages contain no project Python sources or workspace archives. The helper/installer have no separate Authenticode signature; the compatible XPI is Mozilla signed. General selective-format research remains paused and excluded.

[Download helper 1.9.180](https://github.com/FlamingFury28/video-clipper/releases/tag/helper-v1.9.180) · [Firefox extension](https://addons.mozilla.org/firefox/addon/video-clipper-in-out-mp4/)
