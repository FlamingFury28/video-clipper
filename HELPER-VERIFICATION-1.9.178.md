# Helper 1.9.178 verification

The helper update is published separately from extension 1.13.32. Install both components; updating the XPI alone does not replace an older helper.

The exact helper binaries were exercised with permanently installed, Mozilla-signed extension 1.13.31 after restart. Extension 1.13.32 changes only its version and guided-setup helper URLs: all 15 other payload files match 1.13.31 byte for byte. Its exact signed XPI separately passed unsigned-install rejection, permanent installation and restart with signature enforcement.

## Verified cases

- 96 focused unit checks cover exact media tables, codec opt-in, sample clocks, MPD identity, explicit lists, SIDX, missing audio, maximum-OUT planning and URL compatibility guards.
- 23 isolated Firefox exports on Windows/Linux using Firefox 142 and 160: eight MP4/HLS compatibility exports and 15 captured/direct DASH exports, including AV1, H264, VP9/Opus, video-only SIDX, maximum OUT and same-origin script endpoints. Each export uses one Save click and preserves its selected parts after reopening.
- Independent image and waveform comparisons bind the outputs to their source samples. The controlled maximum-OUT VP9/Opus export has 96 presented images and measured audio displacement of -0.5 ms. Linux native-deferred reports retain their original state and are bound to separate positive AV comparisons.
- Eight native compatibility cases and two preview/export checks use these exact binaries. The Windows installer passed payload verification and preparation into an isolated folder with no personal browser registration.
- Null audio backend and zero output devices were verified before browser media. Tests did not change system volume or personal profiles.

## SHA-256

| File | SHA-256 |
|---|---|
| Windows helper executable | `bf82b39baa3ba69c92b514d0b17b8d2988e8b20f8238d83cc49df2b6d9367688` |
| Linux helper executable | `3c37a4fd9db985507b41238332b16b8194f30c0b97efaa74aeb69386c4e4641a` |
| Windows helper ZIP | `fb85a475709cbe18907fc210e14539e36468d76ba685a8d9009654c2643064fd` |
| Linux helper archive | `b9c29d7645a5830ba587c2c8e11b70ca8d9a0e48982ba2696a3b1c09583901fd` |
| Windows guided installer | `fca6ae7e95c222226847a9c96167fabd3893d7ddfe59edb3f524d698d26614a3` |
| Signed Firefox 1.13.32 XPI | `485a59051be2836a259bdc799d5c743c611d375e04ccf538afce4fe9ba4ac270` |

[Helper release and checksums](https://github.com/FlamingFury28/video-clipper/releases/tag/helper-v1.9.178) · [Signed extension release](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.13.32)

## Scope

Tests use controlled local fixtures; they do not certify every website. For one maximum-OUT VP9/Opus case, all observed media traffic, including player loading and preroll, was 846,033 bytes versus 8,487,727 full-fragment bytes; intervening segments 10–40 were absent. This is not a fixed saving promise.

Missing audio produces a warning. A changed manifest, changed local media, unsupported clock or incomplete selected epoch remains rejected. No silent full-source fallback is added. Windows HEVC browser export remains unverified. Other site/format limits remain; full-source compatibility is an explicit setting.

The helper/installer have no separate Authenticode signature. Upstream notices are included, with the inherited incomplete Deno transitive inventory stated in the package. Public packages contain binaries and upstream notices, not project Python sources or workspace archives.
