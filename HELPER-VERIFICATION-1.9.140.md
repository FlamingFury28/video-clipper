# Helper 1.9.140 verification

The helper update is separate from the Mozilla-signed Firefox extension 1.13.19. Windows and Linux x86_64 binaries were tested with isolated Firefox 142 and 159 after permanent installation and restart of the signed extension. The Windows installer was prepared and verified in an isolated directory without registering a browser; it is not Authenticode-signed.

Checks covered MP4 and HLS export, preview, collections, recovery, separate and joined clips, source mutation, truncated responses, cancellation, redirect privacy and WebM video timing. A 1-fps synthetic source and a variable-frame-rate source were compared with Firefox; multiple intervals and duplicate or overlapping ranges were checked for video and audio alignment. On one 69 MB synthetic source, a selected interval transferred about 3 MB on Windows versus about 70 MB with helper 1.9.139. Results vary with the source and server; selective downloading cannot be guaranteed when a server does not support verifiable partial requests.

- Windows installer SHA-256: `3c084755e3e5a1de73100f89007c3fe5dc839653f5c3ccf8ecacd642ae5b9985`
- Windows ZIP SHA-256: `ce49d59be88f14c8fa99dff1b33fe1ecae00f380afe5fef932af4babc895f952`
- Linux x86_64 archive SHA-256: `22782c4834fb0e1d04f19166c005a99c51c0f5abf9ce3e881c2ba44c20fbcac9`
- Signed extension SHA-256: `82893a89bf5f0f0d641d46f70dcc574b29100b81d1dc121505f2ed111052da1a`

See the [release assets and checksum file](https://github.com/FlamingFury28/video-clipper/releases/tag/helper-v1.9.140). No project Python source is included in these helper packages.
