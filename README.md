# Lichii Emulator Build 88 reference

Unofficial, factual reference for the release files of [zortos293/Lichii](https://github.com/zortos293/Lichii), the experimental open-source Nintendo Switch and Switch 2 emulator (GPL-3.0, C++). It lists the exact file names, byte sizes and SHA-256 digests of **build 88** (and of **build 83**, the newest build that still has PGO packages attached), which package fits which system, how to verify a download, and what the release notes say about compatibility.

**This repository contains no binaries, no emulator code, and no games, ROMs, keys or firmware**, and it does not link to or explain how to obtain any of them. Download Lichii only from its official GitHub Releases page.

> Not affiliated with, run by or endorsed by zortos293, the Lichii or Eglantine contributors, or Nintendo. Nintendo Switch and game names are trademarks of their owners. Facts checked against the GitHub Releases API on November 6, 2026 (13:20 UTC).

A longer, regularly updated version of this reference is maintained at **[lichiiemulator.com](https://lichiiemulator.com/)**.

## Build 88 at a glance

| | |
|---|---|
| Release | [`build-88`](https://github.com/zortos293/Lichii/releases/tag/build-88), commit `55532f2`, published 2026-11-06 09:07 UTC |
| Previous | [`build-83`](https://github.com/zortos293/Lichii/releases/tag/build-83), commit `5a50f50`, published 2026-11-06 01:58 UTC; before that `build-75` (`c9ebb5c`, 2026-11-05) |
| Status | Marked **pre-release** (like every Lichii release), so `/releases/latest` does not point to it |
| Files attached | 7: Windows x86_64 MSVC zip (1), Linux x86_64 and ARM64 standard AppImage + tar.gz (4), macOS Apple Silicon zip + dmg (2) |
| PGO packages | The build 88 notes still link PGO files, but **none are attached to the release** (the links return 404 as of Nov 6, 13:20 UTC). The newest attached PGO builds are in build 83 |
| Not published | Android APK, iOS app, Intel Mac build, installer `.exe` |
| Lineage | Fork of Eglantine (`Djihads80/Eglantine`), which derives from Eden, yuzu and Sudachi; named Eglantine up to build 65 |

## What changed in builds 83 and 88

Build 83 (since build 75):

- Ocarina of Time remake: missing vegetation and material data, sky-ambient lighting, a glowing doorway, one-frame white flashes and a black 3D scene on AMD fixed. New built-in **Max Resolution** Add-On, on by default for the supported game build.
- perf9 optimizations merged; shader emission and Vulkan shader-module creation moved to bounded background workers.
- Fixed a race that could crash VP9 movie playback (FINAL FANTASY RESONANCE), invalid depth-stencil copies linked to Star Fox crashes, Mario Kart World presentation pacing; Donkey Kong Bananza now waits for its current frame by default.
- Opt-in local debug server; diagnostic tools stay off by default.

Build 88 (since build 83):

- The notes open with “**AMD fixes will be in the next build**”.
- Frizti performance ports: cached storage-buffer bindings, direct uniform-bank uploads, batched command-page readbacks, earlier GPU submission.
- Background preparation of cached graphics pipelines; Vulkan cache moved to v53 (compatible v52 caches are kept).
- FSR3 frame generation fixes; frame generation stays off by default.
- **Dark’s Dynamic FPS mod is bundled and on by default for the Ocarina of Time remake**; turn it off in the game’s Add-Ons. CPU Clock *Normal* is recommended; correct game speed at every frame rate is not guaranteed.
- Known issue: a fence-worker shutdown race can leave the emulator waiting when you close it; not fixed in this build. No universal FPS gain is promised.

## SHA-256 verification table: build 88

Sizes are exact bytes and digests are the SHA-256 values reported by the GitHub Releases API for tag `build-88`.

| File | Platform | Type | Bytes | SHA-256 |
|---|---|---|---:|---|
| `lichii-windows-x86_64.zip` | Windows x86_64 | MSVC, standard | 116,094,897 | `3405860a13f7b0729548ddb9402a355f4cfb1cd6a6d705fb8ea26f88879b0407` |
| `lichii-linux-x86_64.AppImage` | Linux x86_64 | AppImage, standard | 111,303,160 | `8ddfcb03cffb9761d1532751eb6e68a1cb8a225da38ac1a55b6fe5b190691be0` |
| `lichii-linux-x86_64.tar.gz` | Linux x86_64 | tar.gz, standard | 30,894,711 | `35d02bead188b68f62d41d8791ef32bf48b1c8de8e33de5c1b1a976609704dc6` |
| `lichii-linux-aarch64.AppImage` | Linux ARM64 | AppImage, standard | 103,516,680 | `8c6c73f77ec0ce03a366793348f46648b2b75ce620bf8c6c4daf33dbda8ee784` |
| `lichii-linux-aarch64.tar.gz` | Linux ARM64 | tar.gz, standard | 28,582,275 | `837708bd9fef3a6bc4376446586f877b61cde92340ea6700948984712692a7fc` |
| `lichii-macos-arm64.zip` | macOS 15+ (Apple Silicon) | zip, not notarized | 74,889,782 | `52d95fc1828d1a1e9b94a0770d00abba2f54e6681a4519563a76a86d6bf88ede` |
| `lichii-macos-arm64.dmg` | macOS 15+ (Apple Silicon) | dmg, not notarized | 83,291,315 | `ef824afa6a4fdc949fb79b5294684addeecdf257f0e88ec915dde5c747e8c23d` |

The same digests in `sha256sum` format are in [`SHA256SUMS-build-88.txt`](SHA256SUMS-build-88.txt).

## SHA-256 verification table: build 83 (all 12 files, including PGO)

Use these only if you want a PGO package: build 83 is the newest release with PGO files attached.

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

`sha256sum` format: [`SHA256SUMS-build-83.txt`](SHA256SUMS-build-83.txt). The older build 75 list is kept in [`SHA256SUMS-build-75.txt`](SHA256SUMS-build-75.txt).

## How to verify a download

Windows (Command Prompt or PowerShell):

```bat
CertUtil -hashfile lichii-windows-x86_64.zip SHA256
```

Linux:

```sh
sha256sum lichii-linux-x86_64.AppImage
# or check every file you downloaded at once, from the download folder:
sha256sum --ignore-missing -c SHA256SUMS-build-88.txt
```

macOS:

```sh
shasum -a 256 lichii-macos-arm64.zip
# or
shasum -a 256 --ignore-missing -c SHA256SUMS-build-88.txt
```

If the file name matches but the digest does not, do not run the file. Every build reuses the same file names, so always compare against the list for the build you downloaded. An in-browser checker that hashes the file locally (nothing is uploaded) is on the [download guide](https://lichiiemulator.com/download/).

## OS matrix: which file to pick (build 88)

| Your system | File | Notes |
|---|---|---|
| Windows 10/11 | `lichii-windows-x86_64.zip` | MSVC build, the only Windows file attached to build 88. Extract the whole archive into its own folder and run `lichii.exe`. For the MinGW PGO zip, use build 83. |
| Linux x86_64 | `lichii-linux-x86_64.AppImage` | glibc 2.39+ (Ubuntu 24.04, Fedora 40, Debian 13, Arch). `chmod +x` and run. The tar.gz build needs system Qt 6. |
| Linux ARM64 | `lichii-linux-aarch64.AppImage` | Same glibc/Qt rules. |
| Mac with Apple Silicon | `lichii-macos-arm64.zip` or `.dmg` | macOS 15 or newer. Not notarized: right-click → Open the first time. |
| Android, iPhone, Intel Mac | none | No official build exists. |

The renderer is Vulkan (MoltenVK on macOS). No RAM figure is published; the notes say “Failed to allocate 14336 MiB of backing memory” means Windows ran out of RAM plus page file. The build 75 notes called the MSVC zip the only Windows build with NVIDIA DLSS; the build 83 and 88 notes no longer mention DLSS.

## Compatibility notes (build 88)

There is no official compatibility list. From the release notes and open issues:

| Game | Status | Notes |
|---|---|---|
| Ocarina of Time remake | Boots and plays, heavy issues | Build 83 fixed vegetation, sky lighting and the AMD black scene; build 88 bundles Dynamic FPS (on by default). Build 75 notes: 12–22 fps on Ryzen 5900X + RTX 3080. Open: crashes after 5–20 minutes on build 83 (#205, #209) |
| Star Fox | Playable with issues | 60 fps instead of 30 since build 75; build 83 fixed depth-stencil copies linked to crashes; RTX 50-series can lose the GPU device (build 75 notes suggest NVIDIA driver 610.88) |
| Donkey Kong Bananza | Runs well, not locked 60 | Build 83 waits for the current frame by default. Open: missing terrain (#202) |
| Mario Kart World | Runs, speed varies | Build 83 corrected presentation pacing; 30–38 fps in races on Apple M4 Pro (build 70) |
| Kirby Air Riders | Runs with stalls | Stalls while shaders build; crash at “Loading Shaders” (#196) |
| Final Fantasy Resonance | Movie crash fixed | Build 83 fixed a VP9 movie playback crash |
| Fire Emblem: Fortune’s Weave | Not working well | Black screen (#19) |
| Pokopia | Does not start | Black screen (#79, #248) |

Full table with issue numbers and subsystem status: [compatibility and status](https://lichiiemulator.com/compatibility-status/). Version history: [changelog](https://lichiiemulator.com/changelog/). How Lichii relates to upstream: [Lichii vs Eglantine](https://lichiiemulator.com/vs-eglantine/).

## Spotting a fake download

- Not hosted on `github.com/zortos293/Lichii` (the old `zortos293/Eglantine` URL redirects to the same repo; any other owner is someone else).
- An APK, iOS app or single `setup.exe` installer.
- A “build 88 PGO” file: none is attached to the official build 88 release.
- Bundled “BIOS”, keys, firmware or “all games included”.
- Asks for a survey, payment, “early access” fee or a password from another site. The README says every release is free and public.
- File name, size or SHA-256 differs from the tables above.

More: [Is Lichii safe?](https://lichiiemulator.com/is-lichii-safe/)

## Corrections

Spotted an outdated value? Open an issue here. Bugs in the emulator itself belong on the [official Lichii issue tracker](https://github.com/zortos293/Lichii/issues).

## License

Text in this repository is released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). SHA-256 values and file names are factual data from the official GitHub release.
