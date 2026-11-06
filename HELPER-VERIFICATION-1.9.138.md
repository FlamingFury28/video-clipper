# Video Clipper Helper 1.9.138 — verification

The helper is distributed separately from the Mozilla-signed Firefox extension 1.13.19. The helper and Windows installer have no Authenticode signature.

| Asset | SHA-256 |
|---|---|
| Windows installer | `adda462ea9931ca15d97d26b957a8379922cf71d43cf470ce93de57cb7b603af` |
| Windows ZIP | `4f87284bf317b06184bffe839d95f12703e9d139063ff1c950642a46521ea1d4` |
| Linux x86_64 archive | `314908805f6d64dc246fb01911b65798abb1e94ffe630ade53c1d5eb09e1d503` |

The release assets were downloaded back from GitHub and checked against these hashes. The archives contain compiled helper runtimes and upstream notices, not project Python source.

The exact helper binaries passed 60 source tests per platform (one skipped), native compatibility, collection, recovery, separate-output and editing checks, plus preview/export. Firefox 142 and 159 on Windows and Linux exported MP4 and HLS after isolated permanent installation and restart of the signed extension.

Local WebM fixtures exercised selection at the beginning and end, VP8/Vorbis, silent and delayed audio, several parts, cancellation, redirects and changed source identity. Truncated fixture responses were rejected. A separate public-site sample saved a 30-second clip with audio and video; its traffic and individual frames were not measured.

Selective transfer depends on the server and file format. Some sources still require earlier data or the complete file. Tests do not guarantee compatibility with every website. Multi-channel audio fidelity beyond the tested signals remains unverified. Linux Snap/Flatpak browser integration is unverified.
