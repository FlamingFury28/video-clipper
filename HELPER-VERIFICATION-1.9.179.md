# Helper 1.9.179 verification

The Windows x64 and Linux x86_64 packages contain compiled runtimes and upstream notices, without private project Python sources or workspace archives. Compatible with signed Firefox extension 1.13.32; 1.13.33 updates only guided setup links and its version.

Helper 1.9.179 fixes selective recovery from YouJizz: protocol-relative CDN references inherit HTTPS, valid legacy HLS cache hints are accepted and raw network timeouts keep a precise diagnostic. The helper updates separately from the extension. The stricter native IN-frame comparison still shows about two frames of offset on this player; that is not claimed fixed.

Verified: two real-page saves with exact binaries, eight deterministic MP4/HLS exports in Firefox 142/160 with signed permanent installation/restart and rival-player identity, eight native compatibility cases, two preview/export cases and isolated installer payload/preparation. Tests were silent with forced null audio backend checked before media navigation. Markers and player position were preserved.

Fourteen focused cases pass. The HLS comparison has no introduced failures: 25 of 26 inherited cases pass; repeated AES-key URI handling remains rejected in both parent and candidate. The strict native image comparison remains failed (about two frames of IN offset), not concealed as a pass. The exact reported network timeout was not reproduced. Forty-four byte-identical helper modules retain qualified parent evidence. No experimental DASH-period audio code is bundled.

[Helper release and SHA-256 checksums](https://github.com/FlamingFury28/video-clipper/releases/tag/helper-v1.9.179)

Windows binary SHA-256: `e5ed29fd8138a00d58ece101360922ec697c8334c326c206519ccb0aa3ccbdcb`.
Linux binary SHA-256: `a6d741a806a1782308544196d924a518e1b1af2c58977adfd0a76df0fdea2c47`.
Installer SHA-256: `e55b24a3d39043302316edf74776f7ec3f9f3ec12a64b3d18b08991c294dc704`.

No Authenticode signature is claimed for the helper/installer. Website and format coverage varies; selective mode never silently starts a complete-source download. Optional site session consent remains off unless explicitly granted. No personal browser profile, system volume or helper registration was changed by qualification.
