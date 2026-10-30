# Helper 1.9.137 — verification

The helper-only release was verified against the Mozilla-signed Firefox extension 1.13.19. The extension is unchanged; Mozilla's public catalog currently offers 1.13.8.

## What was checked

- Firefox 142 and 159 on Windows and Linux: permanent signed extension installation, restart, and local MP4/HLS exports with each exact helper binary.
- Per platform: native compatibility (4 cases), collection (8), page recovery (3), output parts (2), editing (3), and preview followed by export. The source-worker suite ran 49 tests: 48 passed and one environment-dependent smoke test was skipped.
- Local WebM fixtures: selected ranges, multiple parts, slow sequential responses, final frames and audio, source identity changes, interrupted responses, and scoped session data on redirects.
- A one-second clip from a reported public site was saved in isolated Firefox on Windows with audio and video. This short sample does not establish long-download reliability or measure bytes transferred.
- The Windows installer payload was checked and prepared in an isolated directory without registering browsers. The installer is not Authenticode signed. The published helper archives were audited for project Python source files.

## Published assets

| File | SHA-256 |
|---|---|
| Windows installer | `aec318f4b8cb595014b274889c2e701c7755b2dcba921927af731706d465c717` |
| Windows ZIP | `a35c6aa734f02a271129474fa8b7d0f37958db2a15f8c364c902ef0d23475f10` |
| Linux x86-64 archive | `0877401b1e3c8fd3418f6810ade35cf10aaf15d5a9e844fd8142736095afb2d9` |

[Download release and checksum file](https://github.com/FlamingFury28/video-clipper/releases/tag/helper-v1.9.137). Public downloads were read back and their SHA-256 digests checked against the verified local packages.

Selective transfer depends on the source, format and server. Some sources still require reading earlier data or downloading the full video. Synthetic tests do not establish compatibility with every website.
