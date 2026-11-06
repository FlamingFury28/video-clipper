# Video Clipper Helper 1.9.139 — verification

The helper is distributed separately from the Mozilla-signed Firefox extension 1.13.19. The helper and Windows installer have no Authenticode signature.

| Asset | SHA-256 |
|---|---|
| Windows installer | `ce860225a9ed1a7f2573240ae58a248af251596c0300f7884b5df2b70d14af45` |
| Windows ZIP | `9264a6b57da50d0fc39c591a31b3648c33aa3309f1b4bfa5307de8c9e2152ca1` |
| Linux x86_64 archive | `9c3aa44bcac14295e70c54b4b312f286f11ac30e0eae5f86a2d01610cdbc5d30` |

The release assets were downloaded back from GitHub and checked against these hashes. The archives contain compiled helper runtimes and upstream notices, not project Python source.

The exact helper binaries passed 62 source tests per platform (one skipped), native compatibility, collection, recovery, separate-output and editing checks, plus preview/export. Firefox 142 and 159 on Windows and Linux exported MP4 and HLS after isolated permanent installation and restart of the signed extension.

A local VP9/Opus fixture with keyframes about 60 seconds apart was tested near its end. The previous helper transferred about 2.50 MB for a 1.88 MB file; the new helper transferred about 601 KB on Linux and 666 KB on Windows, with sampled frames and audio matching. Tests also cover multiple parts, source changes, redirects, cancellation and truncated responses.

Selective transfer depends on the server and file format. Some sources still require earlier data or the complete file. Tests do not guarantee compatibility with every website. Multi-channel audio fidelity beyond the tested signals remains unverified. Linux Snap/Flatpak browser integration is unverified.
