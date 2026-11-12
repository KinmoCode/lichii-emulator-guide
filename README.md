# Lichii Emulator Build 160 reference

Independent, factual reference for the release files of [zortos293/Lichii](https://github.com/zortos293/Lichii), the experimental open-source Nintendo Switch and Switch 2 emulator (GPL-3.0, C++). It lists the exact file names, byte sizes and SHA-256 digests of **build 160**, which package fits which system, how to verify a download, and what the release notes say about compatibility.

**This repository contains no binaries, no emulator code, and no games, ROMs, keys or firmware**, and it does not link to or explain how to obtain any of them. Download Lichii only from its GitHub Releases page.

> Not affiliated with, run by or endorsed by zortos293, the Lichii or Eglantine contributors, or Nintendo. Nintendo Switch and game names are trademarks of their owners. Facts checked against the GitHub Releases API on November 12, 2026 (UTC).

A longer, regularly updated version of this reference is maintained at **[lichiiemulator.com](https://lichiiemulator.com/)**.

## Build 160 at a glance

| | |
|---|---|
| Release | [`build-160`](https://github.com/zortos293/Lichii/releases/tag/build-160), “Lichii nx2 build 160 (2eb5f08)”, commit `2eb5f08`, published 2026-11-11 22:06 UTC |
| Previous | [`build-150`](https://github.com/zortos293/Lichii/releases/tag/build-150) (`17baed7`, 2026-11-10), [`build-130`](https://github.com/zortos293/Lichii/releases/tag/build-130) (`5cf95d7`), [`build-125`](https://github.com/zortos293/Lichii/releases/tag/build-125) (`678a7c9`), [`build-117`](https://github.com/zortos293/Lichii/releases/tag/build-117) (`89440b2`) |
| Status | Regular release (not pre-release); builds 116 through 160 are regular releases, so `/releases/latest` opens build 160 |
| Files attached | 12: Windows x86_64 PGO + standard zip, Linux x86_64 and ARM64 AppImage + self-contained tar.gz (standard and PGO), macOS Apple Silicon zip + dmg |
| PGO packages | Recommended: the notes open with “Recommended download: the PGO build.” Windows PGO uses clang-cl and ThinLTO with a profile trained on Ocarina of Time; Linux PGO uses clang with Eglantine’s profile |
| Own data folder | Since build 150, Lichii uses `%APPDATA%\lichii` on Windows and `~/.local/share/lichii` on Linux (importing safely from Eden on first run) |
| Not published | Official Android APK, iOS app, Intel Mac build, installer `.exe` |
| Lineage | Fork of Eglantine (`Djihads80/Eglantine`), which derives from Eden, yuzu and Sudachi; named Eglantine up to build 65 |

## What changed in builds 160 and 150

Build 160 (30 merged changes since build 150):

- **New look**: opens in the new **Lichii Dark** theme with icons throughout and a **What’s new** window (`Help → What’s New`; classic themes remain in settings). Settings dialogs scroll cleanly at any display scale; per-game overrides get a pink outline and reset button; the game list adds folder counts, full title IDs, favourite stars and 160 px cover sizes (#1365, #1371).
- **Game & crash fixes**: **Yoshi and the Mysterious Book** renders its 3D world (#1363, building on #1189 and #1284); **Ocarina of Time** guard house freeze is fixed by a built-in Texture Pool x2 patch (#1313); **Mario Kart World** characters and karts are lit properly (#1333) and dynamic FPS skips the game’s second-vblank wait (#1332); **The Duskbloods** network test boots to its menus (#552, #851, still stops at online checks) with reactive flushing and DLSS replacement (#828, #637, #638); built-in `nxformat` 1.0.3 avoids crashes when antivirus deletes `nxformat.dll` (#1232); AMD device memory overallocation is allowed (#1335); **Metroid Prime 4 NS2 Edition** large textures are backed (#1325).
- **New features & performance**: native **HDR output** (`HDR10`/scRGB passthrough, Off/Auto/On, #1326); **LAN play** under `Configure → Network → LAN play`, off by default (#1359); redesigned **frame stats overlay** with CPU/GPU % and a 5-second frame-time graph (#1345); RAM-bounded pipeline retention + SPIR-V rebuild cuts revisiting-area shader hitches from **360–770 ms down to ~55–75 ms**, with an option to build all cached shaders at boot (#1334, #1337); CPU/GPU submission optimizations ported from Fritchii EXP61 (#1327, #1329, #1331, #1332, #1095).

Build 150 (51 merged changes since build 130):

- Fixed Ocarina of Time white-wash lighting (#1236), Windows out-of-memory crash (#1210), ocarina ADPCM audio crackle (#1196), and dark fairy fountain / Water Temple walls (#1197).
- Added NVIDIA DLSS 4.5 model presets (E/F/J/K/L/M, default M) and quality modes (#1249, #941), plus AMD FSR 3.1 and FSR 4 upscaling in place of Ocarina of Time’s AA network (#1060–#1062).
- Moved data to `%APPDATA%\lichii` and `~/.local/share/lichii` (#1253), added `Help → Apply Recommended Settings…` (#1264), fixed macOS 15.0–15.3 launch (#1254), and made Linux `tar.gz` archives self-contained (#1255).

Open issue trackers to know about:

- The build 160 release notes list no known-issues section. On the issue tracker, top open tracking issue **#871** covers AMD Vulkan device loss / TDR in Ocarina of Time right after the intro movie or save load, and open issue **#1405** reports 4–7 fps in Ocarina of Time when HDR is enabled.

## SHA-256 verification table: build 160

Sizes are exact bytes and digests are the SHA-256 values reported by the GitHub Releases API for tag `build-160`.

| File | Platform | Type | Bytes | SHA-256 |
|---|---|---|---:|---|
| `lichii-windows-x86_64-pgo.zip` | Windows x86_64 | clang-cl + ThinLTO, PGO (recommended) | 90,614,716 | `77871df6b219a232df0c2da45f8229dc9ba854e74fe1d916d437fed92abb97ba` |
| `lichii-windows-x86_64.zip` | Windows x86_64 | clang-cl + ThinLTO, standard | 90,057,554 | `215459edfbd9f6c542b4548cabf4c16d487feca8ce1003a1094f9beda5f02460` |
| `lichii-linux-x86_64-pgo.AppImage` | Linux x86_64 | AppImage, PGO (recommended) | 144,095,736 | `cc1a09e46c3e060eaf109134040a1448ae08fdbd51b5866e13ea9f42b0d91332` |
| `lichii-linux-x86_64.AppImage` | Linux x86_64 | AppImage, standard | 115,538,424 | `809ee6a79a4ebcc902233a24ee1adef51688c10d4b61ccd29a83d7f17560f782` |
| `lichii-linux-x86_64-pgo.tar.gz` | Linux x86_64 | self-contained tar.gz, PGO | 155,150,185 | `3c89c881dce6c9cf9a06e42e15e350b6960f2fe8432d129555da8c9b379eea5f` |
| `lichii-linux-x86_64.tar.gz` | Linux x86_64 | self-contained tar.gz, standard | 124,922,838 | `8808893f08062c9a450234a3988eb2291dcda9d686a4d7e8780c0b6b6ec21962` |
| `lichii-linux-aarch64-pgo.AppImage` | Linux ARM64 | AppImage, PGO (recommended) | 135,477,768 | `fa1477a1b593534b88242ee7c492c72920bad9a172e7f3633927ea48aba8ad9e` |
| `lichii-linux-aarch64.AppImage` | Linux ARM64 | AppImage, standard | 107,633,160 | `976d6ea582ddb4664b15e40637bc677195aba1c44fca3ac3665018265ef56a4e` |
| `lichii-linux-aarch64-pgo.tar.gz` | Linux ARM64 | self-contained tar.gz, PGO | 146,288,148 | `dfabb2a33fcad8a2a333d0d93c19453e2c73b81bd936e8506aa80cf872931116` |
| `lichii-linux-aarch64.tar.gz` | Linux ARM64 | self-contained tar.gz, standard | 116,728,421 | `6fc1dc3cfb685d99f12fbeb3e2bc83f8d8f7fb0307b30cef658ba75150f58089` |
| `lichii-macos-arm64.zip` | macOS Apple Silicon | app zip (not notarized) | 79,273,315 | `73308d7fd8266f15f774bfb6b1921a88f160fe7c539522292bedce047a40a7b7` |
| `lichii-macos-arm64.dmg` | macOS Apple Silicon | disk image (not notarized) | 87,990,370 | `d73fe76be1eef2f5df83428236d9d9f2529dd1b887115865946e4f5aa5889e28` |

### Verify from a terminal

Windows PowerShell or Command Prompt:

```powershell
certutil -hashfile lichii-windows-x86_64-pgo.zip SHA256
```

Linux:

```sh
sha256sum lichii-linux-x86_64-pgo.AppImage
# or check every file you downloaded at once, from the download folder:
sha256sum --ignore-missing -c SHA256SUMS-build-160.txt
```

macOS:

```sh
shasum -a 256 lichii-macos-arm64.zip
# or
shasum -a 256 --ignore-missing -c SHA256SUMS-build-160.txt
```

If the file name matches but the digest does not, do not run the file. Every build reuses the same file names, so always compare against the list for the build you downloaded. An in-browser checker that hashes the file locally (nothing is uploaded) is on the [download guide](https://lichiiemulator.com/download/).

## OS matrix: which file to pick (build 160)

| Your system | File | Notes |
|---|---|---|
| Windows 10/11 | `lichii-windows-x86_64-pgo.zip` | Recommended by the notes. Extract the whole archive into its own folder and run `lichii.exe`. If the PGO build misbehaves, use `lichii-windows-x86_64.zip`. |
| Linux x86_64 | `lichii-linux-x86_64-pgo.AppImage` | glibc 2.39+ (Ubuntu 24.04, Fedora 40, Debian 13, Arch). `chmod +x` and run. Both `.tar.gz` archives are also self-contained for systems without FUSE: extract and run `lichii/lichii`. |
| Linux ARM64 | `lichii-linux-aarch64-pgo.AppImage` | Same rules: both AppImage and `tar.gz` are self-contained and need glibc 2.39+. |
| Mac with Apple Silicon | `lichii-macos-arm64.zip` or `.dmg` | macOS 15 or newer (15.0–15.3 launch fixed in build 150). Not notarized: right-click → Open the first time. |
| Android, iPhone, Intel Mac | none | No official Lichii release file exists. |

The renderer is Vulkan (MoltenVK on macOS). No official RAM figure is published; “Failed to allocate 14336 MiB of backing memory” means Windows ran out of RAM plus page file (set the page file to system-managed).

## Compatibility notes (build 160)

There is no official compatibility list. From the release notes and open issues:

| Game | Status | Notes |
|---|---|---|
| Ocarina of Time remake | Playable, “very stable” | 60+ fps for many users; built-in FPS Unlock (build 125), white-wash & Windows OOM fixed (build 150), guard house freeze fixed in build 160 (#1313); DLSS 4.5 presets/quality & AMD FSR 3.1/4. Open: AMD Vulkan device loss / TDR after intro or save load (#871), 4–7 fps with HDR on (#1405). (Windows Ocarina-focused fork: [Fritchii v5.8.4](https://lichiiemulator.com/frizti/)) |
| Mario Tennis Fever | Runs fully | Build 116+: texture glitches fixed, 60 fps; firmware controller button icons rendered in build 125 (#691, #821) |
| Yoshi and the Mysterious Book | 3D world renders | Build 160 (#1363): previously rejected shader forms fixed so the 3D world renders instead of staying black |
| Mario Kart World | Runs, lighting & dynamic FPS fixed | Characters and karts lit properly in builds 150/160 (#1231, #1333); dynamic FPS skips second-vblank wait (#1332); water surface & 30 fps clock lock fixed in build 125 (#690, #664) |
| Donkey Kong Bananza | Runs well, not locked 60 | Split back-thread draw boost in build 125 (#858); open terrain issue (#202) |
| The Duskbloods (network test) | Boots to menus | Build 160 (#552, #851): reaches menus with colour grading (#853) and DLSS replacement (#828), stops at online checks |
| Star Fox | Playable with issues | 60 fps gameplay since build 75; RTX 50-series device loss noted |
| Kirby Air Riders | Runs with stalls | White world fixed in build 70; much shorter shader hitches on revisit in build 160 (#1334) |

Full table with issue numbers and subsystem status: [compatibility and status](https://lichiiemulator.com/compatibility-status/). Version history: [changelog](https://lichiiemulator.com/changelog/). Ecosystem forks: [Switch 2 emulator forks](https://lichiiemulator.com/forks/) and [Lichii vs Eglantine](https://lichiiemulator.com/vs-eglantine/).

## Spotting a fake download

- Not hosted on `github.com/zortos293/Lichii` (the old `zortos293/Eglantine` URL redirects to the same repo; any other owner is someone else).
- An APK, iOS app or single `setup.exe` installer.
- A `lichii-win64.zip` from a lookalike domain: open issue #545 reports one from lichii.org that started `node.exe` running a script from `%TEMP%`. The README states Lichii has no download site other than its GitHub Releases page; `lichii.zortos.me` is the project’s site for game info and compatibility reports.
- Bundled “BIOS”, keys, firmware or “all games included”.
- Asks for a survey, payment, “early access” fee or a password from another site. The README says every release is free and public.
- File name, size or SHA-256 differs from the tables above.

More: [Is Lichii safe?](https://lichiiemulator.com/is-lichii-safe/)

## Corrections

Spotted an outdated value? Open an issue here. Bugs in the emulator itself belong on the [Lichii issue tracker](https://github.com/zortos293/Lichii/issues).

## License

Text in this repository is released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). SHA-256 values and file names are factual data from the GitHub release.
