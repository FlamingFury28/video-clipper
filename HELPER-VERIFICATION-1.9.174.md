# Helper 1.9.174 / catalog 1.13.29 verification

Verified on 16 November 2026. Install [Firefox extension 1.13.29](https://addons.mozilla.org/firefox/addon/video-clipper-in-out-mp4/) and [helper 1.9.174](https://github.com/FlamingFury28/video-clipper/releases/tag/helper-v1.9.174) for the additional supported late dash.js export path. They update separately.

## Public package hashes

| Asset | SHA-256 |
|---|---|
| Signed Firefox 1.13.29 XPI | `5983f97ce81f37f2ac4dfe06a5a1e82287d0ec5b0ead3983bb3cea73876cb7b8` |
| Windows helper ZIP | `c9480dd539af3a5647f63f8486b7ef88e20cc544a7d11710a5908ebc3ce9d661` |
| Windows guided installer | `a86bd81c64a24cb60bb5bef88f1cda54f780505ae1c539449e1b3f5c57e031e5` |
| Linux x86_64 TAR.GZ | `dbb6e9575324aeefe2f5f9bb59035823bc4e59e5a34e0ff123147b7da4b0dd11` |

[Extension download and checksums](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.13.29) · [Helper packages and checksums](https://github.com/FlamingFury28/video-clipper/releases/tag/helper-v1.9.174)

The exact tested native executables have SHA-256 `097b98e7fb0b2d5719dd49ec08fdc00e09c8b7d436fe3372f206cae02138f81c` on Windows and `0a68ed86cae315c86a1db60d1274f734bf76cb95ff961f60336b6341086582b4` on Linux. Source launchers were used only for development reproductions, not final native-binary claims.

## Five reproduced defects

- An already-running dash.js player was recognized but could not rearm capture. The adapter now reuses the exact publicly exposed engine and URL while retaining playback state and clip parts.
- Finite MSE append windows were always rejected. The helper accepts them only after proving every captured packet fits their conservative intersection and every observed offset matches exactly.
- Repeated empty MP4 initialization epochs were treated as media. Only structurally verified zero-sample initialization epochs can now be skipped.
- A rejected native append/remove call discarded earlier accepted data. It now rolls back only its own provisional operation.
- A valid new native operation can be accepted before the earlier updateend event is delivered. A bounded FIFO retains native completion order. Trusted native events, framing checks, cancellation and resource limits remain mandatory.

Focused checks include 17 append-window tests, 14 earlier initialization-clock checks, 20 dash.js rejection guards, 15 HLS rejection guards and nine actual-background-port capability cases with explicitly synthetic leases. Actual browser reproductions separately exercise native InvalidStateError failures and accepted removes during a real update event; no synthetic trusted event is used to prove media export.

## Signed browser and binary evidence

The approved direct package **1.13.28** passes unsigned rejection, permanent installation and restart with signature enforcement. With the exact helper binaries, it exports parts **0.240–0.880** and **91.240–91.880 seconds** after panel reopen, with one Save, on Firefox **142 and 160**, Windows and Linux. All four runs exercise rejected native appends/removes and accepted queued operations.

Independent comparisons verify 34 video frames and both audio parts at 0 ms displacement, with PCM correlations above 0.9986. Linux output is compared independently on Windows and bound to the native report and output hashes; a deferred Linux completion report alone is not counted as an audio/video pass. Rendered guided-setup links point to the correct helper 1.9.174 package for each OS.

Catalog **1.13.29** changes only manifest.version from that signed direct package: the other seventeen files are byte-identical. Its own Firefox 160 unsigned-rejection/permanent-install/restart checks pass. The functional export evidence is reused by that explicit payload comparison.

Signed extension 1.13.27 also passes eight MP4/HLS compatibility exports after restart on both Firefox endpoints and OSes. Native compatibility has four cases per OS; persistent worker preview/export has one per OS. Existing evidence for unchanged collection, recovery and editing code is retained rather than described as a new full-suite run.

In the signed Firefox 160 Linux DASH fixture, observed media traffic was **5,011,423 bytes** versus **11,736,444 bytes** of complete fragments; intervening segments 10–40 were absent. This includes initial loading and rearming. Save may fetch missing selected fragments. Buffering, initialization and keyframes add overhead; no fixed saving or exact-byte-only transfer is promised.

## Limits and installation

Late dash.js recovery currently requires a uniquely bound exposed VOD engine, one clear video track, at most one clear audio track and no text tracks. Finite append windows qualify only when all cached packets are proved unclipped. DRM, live streams, closed roots and other unqualified cases remain restricted. Selective mode does not silently start a complete-source download; unsupported sources can require the explicit compatibility setting.

These are controlled local media tests, not certification of every website. Playback tests used a proven null audio backend before media navigation. System volume and personal browser profiles were untouched.

The Windows installer verifies its exact 574-entry payload and passes isolated preparation with verified FFmpeg 8.1.2 tools, without registering personal browsers. It has no separate Authenticode signature. Linux uses system FFmpeg/ffprobe. Upstream notices are included; the Deno transitive inventory remains incomplete and is not presented as a complete SBOM. Project Python sources, workspace archives and FFmpeg binaries are excluded from the public helper packages. No verified macOS/mobile package or Snap/Flatpak native-host setup is supplied.
