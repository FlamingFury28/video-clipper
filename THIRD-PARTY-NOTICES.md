# Third-party notices — Video Clipper 1.2.0 Windows bundle

The Video Clipper project sources remain private. Third-party license rights are unaffected. No open-source license is granted to the project's own code by this notice.

- Python 3.14.5 and its bundled libraries: see THIRD-PARTY/Python-LICENSE.txt, including the bundled-library notices.
- yt-dlp 2026.8.19: Unlicense.
- curl-cffi 0.16.3: MIT; the package credits httpx (BSD). The included libcurl reports curl 8.21.0-IMPERSONATE, BoringSSL, zlib 1.3.1, brotli 1.2.0, zstd 1.5.7, nghttp2 1.63.0, ngtcp2 1.20.0 and nghttp3 1.15.0. Their notices are in THIRD-PARTY/.
- cffi 2.1.1: MIT-0; pycparser 3.11: BSD-3-Clause.
- lz4 4.4.5: BSD-3-Clause, with bundled LZ4 library under BSD terms.
- certifi 2026.7.22: MPL-2.0. Its complete unmodified upstream source archive, including license text, is supplied in THIRD-PARTY/sources/.
- PyInstaller 6.22.3: bootloader and loader under GPL with the bootloader exception permitting combined non-free programs; runtime hooks under Apache-2.0. See THIRD-PARTY/PyInstaller-COPYING.txt and Apache-2.0.txt. Build-only PyInstaller modules are excluded from the runtime module graph.

The dependency-specific notices included under VideoClipperHelper/_internal/*.dist-info/licenses/ are retained. THIRD-PARTY/sources/ also includes unmodified upstream source archives for the Python dependencies and the credited httpx component. UPSTREAM-ARTIFACTS.json records their source URLs and hashes. FFmpeg/ffprobe are not included in this package; install them separately from the links in the installation guide.
