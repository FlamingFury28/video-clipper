# Helper 1.9.177 — verification

Binary-only maintenance release, compatible with signed Firefox extension 1.13.30. Install helper updates separately from the XPI.

| Executable | SHA-256 |
|---|---|
| Windows x64 | `c7d81289a6daf0aec4b5d4619f8ae719eafbdd89cc07efb06f18afc95df17465` |
| Linux x86_64 | `5f821ac6a29d73a04ce2373c2294d4c495c44f541332f2264b3a63b24a0dfc42` |

The missing-duration case is reproduced with the published 1.9.176 binary before correction. The new parser binds each sample duration to its own initialized track, time base, edit list, movie/track fragment or local chunk table, mdat range, byte position, size, SHA-256 and exact packet PTS/DTS. It does not estimate frame rate or rewrite source timestamps. Unknown and ambiguous data fail closed. The joined VFR intermediate is finalized to its attested OUT before final table verification, including an omitted preliminary last duration.

- 62 focused units pass: actual captured video/AAC priming, real copied MP4, changed hashes/clocks/addresses/counts, unsupported flags/references, cancellation, variable durations, trex defaults, 64-bit clocks/offsets, compact sizes and edit-time rescaling.
- Exact binaries and permanently installed signed 1.13.30, after restart on Firefox 142/160 Windows/Linux, pass eight MP4/HLS compatibility exports and eight normal/B-frame tail exports. Both OSes now qualify the previously failing B-frame case on both browser versions.
- Each tail export preserves ranges 116.240–116.880 and 117.240–117.880 seconds after panel reopen and one Save: 34 presented images and two independent PCM windows at zero measured displacement and correlations above 0.999. Native canvas checks verify image phase.
- Eight native compatibility cases, two persistent-worker preview/export cases, Windows/Linux rendered setup links, exact 574-entry installer payload verification and isolated tool preparation pass. No personal browser registration, profile, consent or system-volume changes. Playback uses a proven null audio backend.
- In the controlled Linux Firefox 160 B-frame case, all observed media bytes including loading/rearming are 617,643 versus 6,090,242 complete-fragment bytes. Segments 10–40 are absent; Save adds no media request. Initialization, buffering and preroll add overhead beyond exact exported seconds. This is not universal site certification or a fixed bandwidth saving.

Product evidence digest: `32458a828fe9e60405e302bf68948a2458ac526a5da32e30459b7547bd3749a7`. It pins 70 private source files, 530-file Windows and 495-file Linux runtimes, 57 reports, 259 lab files and three archives. Private project sources and workspace archives are not published. The separate full-track B-frame reference preserves all raw packet hashes, times and durations to avoid the known full-MPD decoder-reference audio shift.

Remaining limits include the older direct-DASH first-frame phase case, unknown clocks, external sample references, protected media and unsupported formats/players. Missing audio remains a warning. Selective mode never silently downloads a full source. Deno's transitive notice inventory remains incomplete; helper/installer have no separate Authenticode signature. Linux requires system FFmpeg/ffprobe.

[Downloads and checksums](https://github.com/FlamingFury28/video-clipper/releases/tag/helper-v1.9.177) · [Previous verification](HELPER-VERIFICATION-1.9.176.md)
