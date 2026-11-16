# Helper 1.9.176 — verification

Published binary-only maintenance update, compatible with signed Firefox extension 1.13.29. Extension and helper update separately.

| Exact executable | SHA-256 |
|---|---|
| Windows x64 | `eb89ac2eed888cc2447db795102553a2ecc4b07f35d9f3f9828837c542f4edd6` |
| Linux x86_64 | `a00242d1d0fb2deee6693b1ea0e21991c3f8eba94bef358ca808e5b8efd68b7a` |

- 32 focused units verify finite append-window admission, random-access resets, packet identity, clipping bounds, initialization and bounded local remuxing.
- Exact binaries: eight native compatibility cases and two persistent-worker preview/export cases. Signed extension 1.13.29, permanently installed and restarted on Firefox 142/160 Windows/Linux, produces eight MP4/HLS compatibility exports.
- Four signed native tail exports preserve two ranges, 116.240–116.880 and 117.240–117.880 seconds, after panel reopen with one Save: 34 presented images and two PCM windows, zero measured displacement and correlation above 0.999. Native canvas checks independently establish the expected image phase.
- Windows Firefox 160 also passes the reordered B-frame tail case. Linux FFprobe 6 omits packet durations in that additional case and still returns CAPTURE_CLOCK_UNAVAILABLE safely. This is an open limitation, not a passed Linux test.
- The B-frame full-MPD reference exposed a 64 ms FFmpeg audio-demux shift. A separate full-track reference preserves and compares every original packet hash, PTS and duration (3,000 video packets and 5,626 audio packets). It does not alter the product or relax its output checks.
- In the controlled Linux Firefox 160 tail fixture, all observed media traffic including initial loading/rearming was 2,095,944 bytes versus 11,736,444 bytes of complete fragments. Segments 10–40 were absent. Buffering, keyframes and preroll require data beyond exact exported bytes; no fixed saving or universal site compatibility is promised.
- Guided-setup links were rendered for Windows and Linux. Windows installer verifies its exact 574-entry payload and prepares verified FFmpeg tools in an isolated target with zero browser registrations. No personal helper, browser profile, consent or system volume was modified; browser media used a proven null audio backend.

Product evidence digest: `18eb1e221fe7242862fcf79c3edf7efe04dd065589921789dd7f4eabf9e68cf4`. It pins 69 private source files, exact 530-file Windows / 495-file Linux runtimes, 49 reports, 601 local lab files and the three archives. Private source files and workspace archives are not published. Earlier local 1.9.175 packages were not published or overwritten.

Known limits also include selected clipped video, rearranged clipped epochs, unproven clocks, DRM/live streams, unsupported players and the older direct DASH first-frame phase issue. Deno's transitive notice inventory remains incomplete. Helper and installer have no separate Authenticode signature. Linux needs system FFmpeg/ffprobe.

[Downloads and package checksums](https://github.com/FlamingFury28/video-clipper/releases/tag/helper-v1.9.176) · [Previous verification](HELPER-VERIFICATION-1.9.174.md)
