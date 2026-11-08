# Lichii Emulator Build 117 reference

Independent, factual reference for the release files of [zortos293/Lichii](https://github.com/zortos293/Lichii), the experimental open-source Nintendo Switch and Switch 2 emulator (GPL-3.0, C++). It lists the exact file names, byte sizes and SHA-256 digests of **build 117**, which package fits which system, how to verify a download, and what the release notes say about compatibility.

**This repository contains no binaries, no emulator code, and no games, ROMs, keys or firmware**, and it does not link to or explain how to obtain any of them. Download Lichii only from its GitHub Releases page.

> Not affiliated with, run by or endorsed by zortos293, the Lichii or Eglantine contributors, or Nintendo. Nintendo Switch and game names are trademarks of their owners. Facts checked against the GitHub Releases API on November 8, 2026 (16:00 UTC).

A longer, regularly updated version of this reference is maintained at **[lichiiemulator.com](https://lichiiemulator.com/)**.

## Build 117 at a glance

| | |
|---|---|
| Release | [`build-117`](https://github.com/zortos293/Lichii/releases/tag/build-117), “Lichii nx2 build 117 (89440b2)”, commit `89440b2`, published 2026-11-07 22:39 UTC |
| Previous | [`build-116`](https://github.com/zortos293/Lichii/releases/tag/build-116) (`92f0212`, 22:12 UTC the same day), which carries the full changelog; before that `build-94` (really build 95, `222877d`) |
| Status | Builds 116 and 117 are the **first regular releases** (not pre-release), so `/releases/latest` now opens build 117. Every earlier release is a pre-release |
| Files attached | 12: Windows x86_64 PGO + standard zip, Linux x86_64 and ARM64 AppImage + tar.gz (standard and PGO), macOS Apple Silicon zip + dmg |
| PGO packages | Back, and recommended: the notes open with “Recommended download: the PGO build.” Builds 88, 93 and 95 had none |
| Windows toolchain | Both zips are built with clang-cl and ThinLTO (no more MSVC/MinGW split); the PGO zip adds a profile trained on Ocarina of Time, so other games gain less |
| Not published | Android APK, iOS app, Intel Mac build, installer `.exe` |
| Lineage | Fork of Eglantine (`Djihads80/Eglantine`), which derives from Eden, yuzu and Sudachi; named Eglantine up to build 65 |

## What changed in builds 116 and 117

Build 117 (since build 116):

- Fixes a crash on AMD Radeon RX 6000 (RDNA2), RX 5000 (RDNA1), Vega and Polaris cards in `amdvlk64.dll` while Ocarina of Time builds its shaders after boot (#657). The faster matrix path from #583 now only runs on RDNA3 and newer; RX 7000/9000 and NVIDIA are unchanged. Everything else is the same as build 116.

Build 116 (since build 95):

- Ocarina of Time remake: “very stable”, many users get 60+ fps. Hyrule Field grass no longer disappears (#551); blown-out sky and haze on AMD fixed (#351, #432); option to turn off the game’s sharpening anti-aliasing (#616); Dynamic FPS stays real down to 10 fps (#584); about 11% faster in Kokiri village (#446).
- NVIDIA DLSS Super Resolution for Ocarina of Time on RTX cards (#606, experimental): *Emulation → Configure → Graphics → Use NVIDIA DLSS in place of a game’s DLSS*.
- Mario Tennis Fever runs fully at 60 fps with the texture glitches fixed.
- GPUs without mesh shaders (GTX 10-series, RX 5000, MoltenVK) draw mesh-shader scenes through compute (#569).
- Neural-network shaders on the GPU’s matrix units: Ocarina 41 → 60 fps on RDNA4 (#583); +12% standing, +24% walking on NVIDIA (#582). Lossless Scaling frame generation loads again (#587).
- Stability: images that do not fit in VRAM fail cleanly (helps 8 GB AMD cards, #440); framebuffers stay within device limits (Apple GPUs, #427); no silent audio padding (#585).
- Features: FPS limit (#270), Switch 2 microphone capture (#497), frame-generation status in the status bar (#537), updater with in-place AppImage updates, one rollback copy, a PGO fallback and a digest check (#509, #504).

Known issues in the build 117 notes:

- White streaks or trails at night in Ocarina of Time (Navi, fireflies, smoke): turn off the DLSS option above. A fix is being tested.
- Splatoon Raiders: characters too dark, green tint, lower FPS than in earlier builds. Being investigated.

## SHA-256 verification table: build 117

Sizes are exact bytes and digests are the SHA-256 values reported by the GitHub Releases API for tag `build-117`.

| File | Platform | Type | Bytes | SHA-256 |
|---|---|---|---:|---|
| `lichii-windows-x86_64-pgo.zip` | Windows x86_64 | clang-cl, PGO (recommended) | 87,342,665 | `1d1d2aef20f73d2b426863dc9b203c6a2920e3a6882019afe6b34c74d79929ac` |
| `lichii-windows-x86_64.zip` | Windows x86_64 | clang-cl, standard | 86,974,110 | `da8d154c277d79b05b94f2102b532440d2d6d5c6c462643e75d65689f30ef7dc` |
| `lichii-linux-x86_64-pgo.AppImage` | Linux x86_64 | AppImage, PGO | 140,442,104 | `a2eda749105395ac6910c905f0f3c564528b7bfd132ebaf7616963fe28c6dd98` |
| `lichii-linux-x86_64.AppImage` | Linux x86_64 | AppImage, standard | 111,479,288 | `f0441333e371efae484c97b317e75eda40cc212e4a208da6bb9df25e16daa1a1` |
| `lichii-linux-x86_64-pgo.tar.gz` | Linux x86_64 | tar.gz, PGO | 25,543,213 | `0fb60d7309f3ba46b1184a6478bc2aed3ba64966cb3fae4bbe62c44f413235ef` |
| `lichii-linux-x86_64.tar.gz` | Linux x86_64 | tar.gz, standard | 31,146,150 | `9899e37cff6b895fbba71f855ebca8d45d90826366a8023c45931fabdfe34b7c` |
| `lichii-linux-aarch64-pgo.AppImage` | Linux ARM64 | AppImage, PGO | 131,918,344 | `806b61f47ebce1d041d0184d76c672f24c5a2c59cace321a8bfa9585a9730c01` |
| `lichii-linux-aarch64.AppImage` | Linux ARM64 | AppImage, standard | 103,766,536 | `1e73722359df7492f9e32821ce9e26ba949e4cb028f0618783ba5b57895cbf13` |
| `lichii-linux-aarch64-pgo.tar.gz` | Linux ARM64 | tar.gz, PGO | 24,013,789 | `b16d86d79a34b8cf094af3a9bdb09f2daa74ed568a4caff2a311bb72d7a01f97` |
| `lichii-linux-aarch64.tar.gz` | Linux ARM64 | tar.gz, standard | 28,838,199 | `2d6d2b3b6817c5ac4d79b94e065693e137efd3cac20237edfec53a34cff8672e` |
| `lichii-macos-arm64.zip` | macOS 15+ (Apple Silicon) | zip, not notarized | 75,138,876 | `b1279cc3ce766c9e17220d756ca23635867ef7071623223d6d71b12e4ca6c7f1` |
| `lichii-macos-arm64.dmg` | macOS 15+ (Apple Silicon) | dmg, not notarized | 84,615,804 | `aec50f4a65f4afd2fee2653f24325d214b50b7cb8dcc0f0d4b88260663f9bf7d` |

The same digests in `sha256sum` format are in [`SHA256SUMS-build-117.txt`](SHA256SUMS-build-117.txt). Older lists are kept in [`SHA256SUMS-build-95.txt`](SHA256SUMS-build-95.txt), [`SHA256SUMS-build-88.txt`](SHA256SUMS-build-88.txt), [`SHA256SUMS-build-83.txt`](SHA256SUMS-build-83.txt) and [`SHA256SUMS-build-75.txt`](SHA256SUMS-build-75.txt).

## How to verify a download

Windows (Command Prompt or PowerShell):

```bat
CertUtil -hashfile lichii-windows-x86_64-pgo.zip SHA256
```

Linux:

```sh
sha256sum lichii-linux-x86_64-pgo.AppImage
# or check every file you downloaded at once, from the download folder:
sha256sum --ignore-missing -c SHA256SUMS-build-117.txt
```

macOS:

```sh
shasum -a 256 lichii-macos-arm64.zip
# or
shasum -a 256 --ignore-missing -c SHA256SUMS-build-117.txt
```

If the file name matches but the digest does not, do not run the file. Every build reuses the same file names, so always compare against the list for the build you downloaded. An in-browser checker that hashes the file locally (nothing is uploaded) is on the [download guide](https://lichiiemulator.com/download/).

## OS matrix: which file to pick (build 117)

| Your system | File | Notes |
|---|---|---|
| Windows 10/11 | `lichii-windows-x86_64-pgo.zip` | Recommended by the notes. Extract the whole archive into its own folder and run `lichii.exe`. If the PGO build misbehaves, use `lichii-windows-x86_64.zip`. |
| Linux x86_64 | `lichii-linux-x86_64-pgo.AppImage` | glibc 2.39+ (Ubuntu 24.04, Fedora 40, Debian 13, Arch). `chmod +x` and run. Standard AppImage and tar.gz (system Qt 6) also attached. |
| Linux ARM64 | `lichii-linux-aarch64-pgo.AppImage` | Same glibc/Qt rules. |
| Mac with Apple Silicon | `lichii-macos-arm64.zip` or `.dmg` | macOS 15 or newer. Not notarized: right-click → Open the first time. No PGO build for macOS. |
| Android, iPhone, Intel Mac | none | No release file exists. |

The renderer is Vulkan (MoltenVK on macOS). No RAM figure is published; the notes say “Failed to allocate 14336 MiB of backing memory” means Windows ran out of RAM plus page file.

## Compatibility notes (build 117)

There is no official compatibility list. From the release notes and open issues:

| Game | Status | Notes |
|---|---|---|
| Ocarina of Time remake | Playable, “very stable” per build 116 | Many users at 60+ fps; Hyrule Field grass and AMD sky/haze fixed; optional DLSS on RTX (can leave white trails at night). Build 117 fixes a crash on AMD RX 6000 and older. Open reports from older builds: crash after 5–10 minutes on build 83 (#205), hang when closing (#222), ~29 fps CPU-bound (#117) |
| Mario Tennis Fever | Runs fully | Build 116: texture glitches fixed, 60 fps |
| Star Fox | Playable with issues | 60 fps instead of 30 since build 75; RTX 50-series can lose the GPU device (build 75 notes suggest NVIDIA driver 610.88) |
| Donkey Kong Bananza | Runs well, not locked 60 | Open: missing terrain (#202) |
| Mario Kart World | Runs, speed varies | 30–38 fps in races on Apple M4 Pro (build 70) |
| Kirby Air Riders | Runs with stalls | Stalls while shaders build |
| Splatoon Raiders | Runs, regressed | Build 117 notes: too dark, green tint, lower FPS; being investigated |
| Pokopia | Does not start | Black screen with only outlines and UI (#248) |

Full table with issue numbers and subsystem status: [compatibility and status](https://lichiiemulator.com/compatibility-status/). Version history: [changelog](https://lichiiemulator.com/changelog/). How Lichii relates to upstream: [Lichii vs Eglantine](https://lichiiemulator.com/vs-eglantine/).

## Spotting a fake download

- Not hosted on `github.com/zortos293/Lichii` (the old `zortos293/Eglantine` URL redirects to the same repo; any other owner is someone else).
- An APK, iOS app or single `setup.exe` installer.
- A `lichii-win64.zip` from a lookalike domain: open issue #545 reports one from lichii.org that started `node.exe` running a script from `%TEMP%`. The README now says Lichii has no download site other than its GitHub Releases page; `lichii.zortos.me` is the project’s site for game info and compatibility reports.
- Bundled “BIOS”, keys, firmware or “all games included”.
- Asks for a survey, payment, “early access” fee or a password from another site. The README says every release is free and public.
- File name, size or SHA-256 differs from the tables above.

More: [Is Lichii safe?](https://lichiiemulator.com/is-lichii-safe/)

## Corrections

Spotted an outdated value? Open an issue here. Bugs in the emulator itself belong on the [Lichii issue tracker](https://github.com/zortos293/Lichii/issues).

## License

Text in this repository is released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). SHA-256 values and file names are factual data from the GitHub release.
