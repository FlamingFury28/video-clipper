# Third-party notices — helper 1.8.0

Project Python sources remain private. This notice grants no open-source license to Video Clipper's own code. Upstream license rights are unaffected.

The Windows and Linux binary packages include a `THIRD-PARTY` directory, retained dependency license files, upstream source archives and `UPSTREAM-ARTIFACTS.json` with their origins/hashes. These upstream archives are not project source archives.

- **Python 3.14.5** and bundled standard libraries: Python license and bundled-library notices.
- **yt-dlp 2026.8.19:** Unlicense. **yt-dlp-ejs 0.8.0:** upstream license supplied with the package.
- **Deno 2.9.8:** MIT, with upstream notices/source references in `THIRD-PARTY/deno`. The official runtime contains V8 and other components. `NOTICE-COVERAGE.json` explicitly records that a complete version-specific transitive license inventory has not been established; this package is not a complete SBOM.
- **curl-cffi 0.16.3:** MIT, including the credited httpx component under BSD terms. libcurl/curl-impersonate and its crypto/compression/HTTP dependencies have their supplied notices in `THIRD-PARTY`.
- **cffi 2.1.1:** MIT-0. **pycparser 3.11:** BSD-3-Clause.
- **lz4 4.4.5:** BSD-3-Clause, including the bundled LZ4 library under BSD terms.
- **certifi 2026.7.22:** MPL-2.0; the complete unmodified upstream source archive and license are supplied in `THIRD-PARTY/sources`.
- **Public Suffix List**, snapshot 2026-10-22: MPL-2.0; data, license and provenance are supplied in `THIRD-PARTY/public-suffix`.
- **PyInstaller 6.22.3:** bootloader/loader under GPL with the bootloader exception permitting combined non-free programs; runtime hooks under Apache-2.0. See `PyInstaller-COPYING.txt` and `Apache-2.0.txt`. Build-only PyInstaller modules are excluded from the runtime graph.

**FFmpeg/ffprobe are not bundled.** Install a suitable build separately and follow its own license terms. The browser extension XPI is Mozilla signed; that signature does not sign or certify the companion helper or its dependencies. Package integrity and verification scope are described in [VERIFICATION.json](VERIFICATION.json).
