# Lichii Emulator Build 95 reference

Unofficial, factual reference for the release files of [zortos293/Lichii](https://github.com/zortos293/Lichii), the experimental open-source Nintendo Switch and Switch 2 emulator (GPL-3.0, C++). It lists the exact file names, byte sizes and SHA-256 digests of **build 95** (GitHub tag `build-94`), and of **build 83**, the newest build that has PGO packages attached, which package fits which system, how to verify a download, and what the release notes say about compatibility.

**This repository contains no binaries, no emulator code, and no games, ROMs, keys or firmware**, and it does not link to or explain how to obtain any of them. Download Lichii only from its official GitHub Releases page.

> Not affiliated with, run by or endorsed by zortos293, the Lichii or Eglantine contributors, or Nintendo. Nintendo Switch and game names are trademarks of their owners. Facts checked against the GitHub Releases API on November 7, 2026 (17:45 UTC).

A longer, regularly updated version of this reference is maintained at **[lichiiemulator.com](https://lichiiemulator.com/)**.

## Build 95 at a glance

| | |
|---|---|
| Release | [`build-94`](https://github.com/zortos293/Lichii/releases/tag/build-94), titled “Lichii nx2 build 95 (222877d)”, commit `222877d`, published 2026-11-07 10:02 UTC |
| Build number | The notes say this **is build 95**: the About screen and logs say `build-95`; the tag and download links say `build-94` by mistake. There is no separate build 94 release |
| Previous | [`build-93`](https://github.com/zortos293/Lichii/releases/tag/build-93), commit `09b78bd`, 2026-11-06 21:04 UTC; before that `build-88` (`55532f2`) and `build-83` (`5a50f50`) |
| Status | Marked **pre-release** (like every Lichii release), so `/releases/latest` does not point to it |
| Files attached | 7: Windows x86_64 MSVC zip (1), Linux x86_64 and ARM64 standard AppImage + tar.gz (4), macOS Apple Silicon zip + dmg (2) |
| PGO packages | None. The build 95 notes say “standard builds only; PGO builds are not included”; build 93 also shipped standard builds only, and build 88’s PGO files were removed on November 6. The newest attached PGO builds are in build 83 |
| Not published | Android APK, iOS app, Intel Mac build, installer `.exe` |
| Lineage | Fork of Eglantine (`Djihads80/Eglantine`), which derives from Eden, yuzu and Sudachi; named Eglantine up to build 65 |

## What changed in builds 93 and 95

Build 93 (since build 88):

- AMD shader correctness (#273) and Vulkan synchronisation (#295) fixes. The notes say these have compiler and test evidence but were not verified in affected AMD gameplay, and may cost some performance.
- MinGW AV1 decoder fix added to the source (#284; the release ships only the MSVC Windows zip), a shader-loading cancellation fix (#290), a performance profile seeded only for new configurations (#314), optional draw discard while pipelines compile (off by default, #224).
- Linux packages include `nx2_switches.txt` defaults (#287). New opt-in desktop compatibility reports (#303): right-click a game after playing; nothing is uploaded automatically.

Build 95 (since build 93, 56 merged changes):

- Ocarina of Time remake: near foliage no longer fades out (#410); white flashes on camera movement (#215), terrain drawn over the scene (#185) and the stale Z-target reticle (#397) fixed; Gerudo Valley rock and canyon shaders and other rejected shaders compile; GPU macro and shader-correctness fixes ported from upstream Eglantine, including white leaves on Intel (#329).
- A random crash with “Accessing an unallocated region of a SparseLargeVector” fixed (#485); it came from the Eden import and could affect any game. Two game-list scan crashes fixed.
- Performance: less GPU-thread bookkeeping (from Frizti), guarded and mesh pipelines saved in the Vulkan disk cache, time-critical threads kept on P-cores on hybrid Intel CPUs (`EDEN_HYBRID_CORES=0` turns it off), and an experimental *Pin GPU threads to their own cores* hack, **off by default**. No FPS gain is promised.
- The migration prompt’s **Keep Old Data** option now keeps your data (it used to move it). ARM Linux and macOS build again.
- Still open: AMD black foliage and haze, HUD flicker, cutscene audio drift, the first-launch shader stall on Linux. An NVIDIA device-lost crash in Ocarina of Time reported on build 93 is waiting for a retest.

Dark’s Dynamic FPS mod for Ocarina of Time arrived in build 88 and is still bundled (on by default; turn it off in Add-Ons).

## SHA-256 verification table: build 95 (tag `build-94`)

Sizes are exact bytes and digests are the SHA-256 values reported by the GitHub Releases API for tag `build-94`.

| File | Platform | Type | Bytes | SHA-256 |
|---|---|---|---:|---|
| `lichii-windows-x86_64.zip` | Windows x86_64 | MSVC, standard | 116,143,228 | `1560b9d46a20b54a8494316a650bfef12a905fbd6c612758d4509dcefca61164` |
| `lichii-linux-x86_64.AppImage` | Linux x86_64 | AppImage, standard | 111,389,176 | `90be7d77c941f009dd805931bd562ae64e0d799171d0efcfe63ac1a28d7787fa` |
| `lichii-linux-x86_64.tar.gz` | Linux x86_64 | tar.gz, standard | 30,988,590 | `940237f32764926aa9b2747e7b51500f916f1f3ad4057b051b104b781274502d` |
| `lichii-linux-aarch64.AppImage` | Linux ARM64 | AppImage, standard | 103,578,120 | `84cd883f77fe3607e0a814252f298113d3d6504130c4831e4fc69601887b1131` |
| `lichii-linux-aarch64.tar.gz` | Linux ARM64 | tar.gz, standard | 28,672,793 | `221a14966d65cf47f125899c655b2ba4df43110509b31def8a16df2e88cfd2d0` |
| `lichii-macos-arm64.zip` | macOS 15+ (Apple Silicon) | zip, not notarized | 74,962,570 | `86a1e58c6bb2c05445527add759080bc5e86a63f3a673f5b31e8d6cae06a00f7` |
| `lichii-macos-arm64.dmg` | macOS 15+ (Apple Silicon) | dmg, not notarized | 83,384,839 | `43bacbf59ace6fac96193c5393b0db029917b8a2cd527f3e2410933ff2365cdb` |

The same digests in `sha256sum` format are in [`SHA256SUMS-build-95.txt`](SHA256SUMS-build-95.txt).

## SHA-256 verification table: build 83 (all 12 files, including PGO)

Use these only if you want a PGO package: build 83 is the newest release with PGO files attached (builds 88, 93 and 95 have none).

| File | Platform | Type | Bytes | SHA-256 |
|---|---|---|---:|---|
| `lichii-windows-x86_64-pgo.zip` | Windows x86_64 | MinGW clang, PGO | 66,964,180 | `c5b3112a1b12e3773eb987c700d8f7978474394050397df748309c1ae66fb0bf` |
| `lichii-windows-x86_64.zip` | Windows x86_64 | MSVC, standard | 115,970,435 | `85419bbc902580790d276cf9faa312685619b492998e5819545da2fb455ade66` |
| `lichii-linux-x86_64-pgo.AppImage` | Linux x86_64 | AppImage, PGO | 140,151,288 | `86d6616b6a4c67304d2cc8f4a9d28ea669f6ced9cd799ced2fa768a26e1d0712` |
| `lichii-linux-x86_64.AppImage` | Linux x86_64 | AppImage, standard | 111,254,008 | `6f19d98a422fa5c766347e4a0c405c9c74335a0e7e461cdd76b8c4b2ba088a1c` |
| `lichii-linux-x86_64-pgo.tar.gz` | Linux x86_64 | tar.gz, PGO | 25,206,064 | `d4ae92c36dac97a486298dd8a4a815f0db2207edd9b8efea797096924c5aee38` |
| `lichii-linux-x86_64.tar.gz` | Linux x86_64 | tar.gz, standard | 30,858,203 | `ac6290b04025346cff1bd3338502ea0e4207c5ae320a46cd9abad3c39420e669` |
| `lichii-linux-aarch64.AppImage` | Linux ARM64 | AppImage, standard | 103,467,528 | `3a20ef92d58d1778e9e014b9e55d1dc1872dfea5e517bbbb6f96eb27bdc9ae22` |
| `lichii-linux-aarch64-pgo.AppImage` | Linux ARM64 | AppImage, PGO | 131,574,280 | `e1932934c933cb3352c27cbb46b7dacb03452ab95f3a90b2f75bcd9d58413d8e` |
| `lichii-linux-aarch64.tar.gz` | Linux ARM64 | tar.gz, standard | 28,547,883 | `1c8c56034a93e5b88608a89b98bdb892975392e5c7600ac83059237e649dee95` |
| `lichii-linux-aarch64-pgo.tar.gz` | Linux ARM64 | tar.gz, PGO | 23,686,152 | `fa14ea58edf2d177dcc5816169bca0be969ece4f4b77b63811a3b2b395fbc214` |
| `lichii-macos-arm64.zip` | macOS 15+ (Apple Silicon) | zip, not notarized | 74,866,832 | `908d6c05363ade69e6159f6523ac5eb52ae9417dd505a41adc2fc6e39f9c58b9` |
| `lichii-macos-arm64.dmg` | macOS 15+ (Apple Silicon) | dmg, not notarized | 83,204,304 | `4ab58155b438ae6d86735562f0ab27deaa0351b7ea215259814aba91efcdc1b6` |

`sha256sum` format: [`SHA256SUMS-build-83.txt`](SHA256SUMS-build-83.txt). Older lists are kept in [`SHA256SUMS-build-88.txt`](SHA256SUMS-build-88.txt) and [`SHA256SUMS-build-75.txt`](SHA256SUMS-build-75.txt).

## How to verify a download

Windows (Command Prompt or PowerShell):

```bat
CertUtil -hashfile lichii-windows-x86_64.zip SHA256
```

Linux:

```sh
sha256sum lichii-linux-x86_64.AppImage
# or check every file you downloaded at once, from the download folder:
sha256sum --ignore-missing -c SHA256SUMS-build-95.txt
```

macOS:

```sh
shasum -a 256 lichii-macos-arm64.zip
# or
shasum -a 256 --ignore-missing -c SHA256SUMS-build-95.txt
```

If the file name matches but the digest does not, do not run the file. Every build reuses the same file names, so always compare against the list for the build you downloaded. An in-browser checker that hashes the file locally (nothing is uploaded) is on the [download guide](https://lichiiemulator.com/download/).

## OS matrix: which file to pick (build 95)

| Your system | File | Notes |
|---|---|---|
| Windows 10/11 | `lichii-windows-x86_64.zip` | MSVC build, the only Windows file attached to build 95. Extract the whole archive into its own folder and run `lichii.exe`. For the MinGW PGO zip, use build 83. |
| Linux x86_64 | `lichii-linux-x86_64.AppImage` | glibc 2.39+ (Ubuntu 24.04, Fedora 40, Debian 13, Arch). `chmod +x` and run. The tar.gz build needs system Qt 6. |
| Linux ARM64 | `lichii-linux-aarch64.AppImage` | Same glibc/Qt rules. |
| Mac with Apple Silicon | `lichii-macos-arm64.zip` or `.dmg` | macOS 15 or newer. Not notarized: right-click → Open the first time. |
| Android, iPhone, Intel Mac | none | No official build exists. |

The renderer is Vulkan (MoltenVK on macOS). No RAM figure is published; the notes say “Failed to allocate 14336 MiB of backing memory” means Windows ran out of RAM plus page file. The build 75 notes called the MSVC zip the only Windows build with NVIDIA DLSS; the notes for builds 83 to 95 no longer mention DLSS.

## Compatibility notes (build 95)

There is no official compatibility list. From the release notes and open issues:

| Game | Status | Notes |
|---|---|---|
| Ocarina of Time remake | Boots and plays, heavy issues | Build 83 fixed vegetation, sky lighting and the AMD black scene; build 88 bundles Dynamic FPS (on by default); build 95 fixed near-foliage fade, white flashes, terrain over the scene and the Z-target reticle. Build 75 notes: 12–22 fps on Ryzen 5900X + RTX 3080. Still open: AMD black foliage and haze, HUD flicker, cutscene audio drift; crash after 5–10 minutes on build 83 (#205) |
| Star Fox | Playable with issues | 60 fps instead of 30 since build 75; build 83 fixed depth-stencil copies linked to crashes; RTX 50-series can lose the GPU device (build 75 notes suggest NVIDIA driver 610.88) |
| Donkey Kong Bananza | Runs well, not locked 60 | Build 83 waits for the current frame by default. Open: missing terrain (#202) |
| Mario Kart World | Runs, speed varies | Build 83 corrected presentation pacing; 30–38 fps in races on Apple M4 Pro (build 70) |
| Kirby Air Riders | Runs with stalls | Stalls while shaders build; an older crash report at “Loading Shaders” (#196) was closed as stale |
| Final Fantasy Resonance | Movie crash fixed | Build 83 fixed a VP9 movie playback crash |
| Fire Emblem: Fortune’s Weave | Not working well | Older black-screen report (#19) closed as stale, no fix named |
| Pokopia | Does not start | Black screen with only outlines and UI (#248) |

Full table with issue numbers and subsystem status: [compatibility and status](https://lichiiemulator.com/compatibility-status/). Version history: [changelog](https://lichiiemulator.com/changelog/). How Lichii relates to upstream: [Lichii vs Eglantine](https://lichiiemulator.com/vs-eglantine/).

## Spotting a fake download

- Not hosted on `github.com/zortos293/Lichii` (the old `zortos293/Eglantine` URL redirects to the same repo; any other owner is someone else).
- An APK, iOS app or single `setup.exe` installer.
- A “build 95 PGO” or “build 94 PGO” file: builds 88, 93 and 95 have no PGO files attached.
- A `lichii-win64.zip` from a lookalike domain: open issue #545 reports one from lichii.org that started `node.exe` running a script from `%TEMP%`. The official Windows file is `lichii-windows-x86_64.zip`, and the README names `lichii.zortos.me` as the project website.
- Bundled “BIOS”, keys, firmware or “all games included”.
- Asks for a survey, payment, “early access” fee or a password from another site. The README says every release is free and public.
- File name, size or SHA-256 differs from the tables above.

More: [Is Lichii safe?](https://lichiiemulator.com/is-lichii-safe/)

## Corrections

Spotted an outdated value? Open an issue here. Bugs in the emulator itself belong on the [official Lichii issue tracker](https://github.com/zortos293/Lichii/issues).

## License

Text in this repository is released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). SHA-256 values and file names are factual data from the official GitHub release.
