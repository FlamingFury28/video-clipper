# Helper 1.9.173 verification

Verified on 16 November 2026. Use with Firefox extension **1.13.27** for the new late hls.js export path. Updating the extension does not install the helper.

## Download integrity

| Public asset | SHA-256 |
|---|---|
| Windows ZIP | `8272ea9b58b2f08b384ce48c74262348f73016edda41a71400d60053c5a62d34` |
| Windows guided installer | `f0e47f16ee11423dff8d507c99a711a29786be7ea43491afed35ea9740af6654` |
| Linux x86_64 TAR.GZ | `13a40a1a6713e1ca437ceab2b4ab88970439dfd4c5aef66f9797d519ca3d172f` |

[Helper packages and checksums](https://github.com/FlamingFury28/video-clipper/releases/tag/helper-v1.9.173) · [Signed extension](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.13.27)

The Windows executable inside the helper package has SHA-256 `88f7ee6617c7566031973e52e4cb1a4b49812c5e609fa880fa09b8a01846e218`; the Linux executable has `ad73d34d9da4064d4540c3c82f4cc35f207907f67de12f01ded6c65c8774b6ff`. These exact binaries were tested; a source launcher was used only for earlier development reproductions. The installer has no separate Authenticode signature. It verifies its embedded package inventory and hash; its isolated preparation test passes without registering a personal browser.

## Changes and evidence

- Already-running supported hls.js VOD players can rearm capture while retaining the selected source, playback position and state. The player must expose a uniquely bound public instance. Different-source, ambiguous-player, live, encrypted and advertisement cases remain rejected.
- Fragmented MP4 initialization records are distinguished structurally from media records before their clock is excluded. Fourteen focused checks cover valid and invalid initialization data.
- Audio coverage is checked over the selected intervals. A gap between two unselected regions no longer causes a false missing-audio result; gaps within a selection remain rejected. Fourteen coverage checks pass.
- Out-of-order MP4 fragments are reordered only when packet hashes, stream identity, PTS/DTS, durations and sizes are independently preserved. Key/corruption flags remain checked; only FFprobe's order-dependent discard marker is normalized. The saved failure preserves all 550 packets after repair, and seven altered-identity cases are rejected.
- Missing AAC packet durations reported by FFprobe 6 are recovered only from a uniquely matching decoded frame with the same packet position, rational timestamp and packet identity. Ten checks pass; known durations are retained.

Actual helper binaries pass four native compatibility cases and a persistent source-worker preview/export case on each OS. Permanently signed extension 1.13.26 exports MP4/HLS after restart in Firefox 142 and 160 on Windows and Linux. This compatibility proof was completed before publishing the helper.

The final signed **1.13.27** passes unsigned-package rejection, permanent installation and restart with signature enforcement. On Firefox 160, Windows and Linux, it exports two distant selected parts from a nested open component after panel close/reopen with one Save click. Both results have 34 independently compared video frames and two PCM comparisons above 0.999 correlation at 0 ms displacement. The Linux output is independently compared on Windows; completion alone is not treated as an audio/video pass. The rendered setup links also point to helper 1.9.173 for the correct OS.

In that controlled 120-second HLS fixture, observed media traffic including initial playback and capture rearming was 5,632,017 bytes versus 12,461,204 bytes of complete source segments. Intervening segments 10–40 were absent, and Save caused no additional media request. This is an observed example, not a fixed saving: buffering, initialization and keyframe preroll require more data than the exact exported interval. Playing-state exports were verified separately.

## Scope

These are synthetic local media and isolated browser tests, not certification of every website. Firefox playback tests used a proven null audio backend before media navigation; system volume and personal browser profiles were untouched. Existing collection and recovery evidence is reused for unchanged code, rather than presented as a new full-suite run.

Selective mode does not silently download the full source. Unsupported sources can require the explicit full-source compatibility setting. Closed shadow roots, DRM and live streams are unsupported. Not every custom hls.js integration exposes the instance needed for safe late rearming.

The Windows installer and Linux x86_64 archive contain verified binaries and upstream notices, not private project Python sources. The Deno transitive license inventory remains incomplete and is not represented as a complete SBOM. No verified macOS/mobile package or Snap/Flatpak native-host setup is supplied.
