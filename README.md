# Lichii Emulator Build 75 reference

Unofficial, factual reference for the release files of [zortos293/Lichii](https://github.com/zortos293/Lichii), the experimental open-source Nintendo Switch and Switch 2 emulator (GPL-3.0, C++). It lists the exact file names, byte sizes and SHA-256 digests of **build 75**, which package fits which system, how to verify a download, and what the release notes say about compatibility.

**This repository contains no binaries, no emulator code, and no games, ROMs, keys or firmware**, and it does not link to or explain how to obtain any of them. Download Lichii only from its official GitHub Releases page.

> Not affiliated with, run by or endorsed by zortos293, the Lichii or Eglantine contributors, or Nintendo. Nintendo Switch and game names are trademarks of their owners. Facts checked against the GitHub Releases API on November 5, 2026.

A longer, regularly updated version of this reference is maintained at **[lichiiemulator.com](https://lichiiemulator.com/)**.

## Build 75 at a glance

| | |
|---|---|
| Release | [`build-75`](https://github.com/zortos293/Lichii/releases/tag/build-75), commit `c9ebb5c`, published 2026-11-05 |
| Status | Marked **pre-release** (like every Lichii release), so `/releases/latest` does not point to it |
| Files | 12: Windows x86_64 (2), Linux x86_64 and ARM64 (8), macOS Apple Silicon (2) |
| Not published | Android APK, iOS app, Intel Mac build, installer `.exe` |
| Lineage | Fork of Eglantine (`Djihads80/Eglantine`), which derives from Eden, yuzu and Sudachi; named Eglantine up to build 65 |

## SHA-256 verification table

Sizes are exact bytes as reported by the GitHub Releases API for tag `build-75`.

| File | Platform | Type | Bytes | SHA-256 |
|---|---|---|---:|---|
| `lichii-windows-x86_64-pgo.zip` | Windows x86_64 | MinGW clang, PGO (recommended) | 66,560,695 | `bf10ad4a528848236d79d77133fe2aeebf2f242b569622e9046004d8b4ceadba` |
| `lichii-windows-x86_64.zip` | Windows x86_64 | MSVC, standard (only build with NVIDIA DLSS) | 115,840,760 | `d12f73fd711fbea70cf94f5cdbaaff4acdd88bb8dcbb6c45a631a487428342b0` |
| `lichii-linux-x86_64-pgo.AppImage` | Linux x86_64 | AppImage, PGO (recommended) | 139,790,840 | `7459a50dbf16418e6b5d3cab61e70a86e60e4d7d479283bdd3f82e003587547f` |
| `lichii-linux-x86_64.AppImage` | Linux x86_64 | AppImage, standard | 110,819,832 | `669695e897c25ba72d47a323787b6066a10270b9c322d278245764e005bf6a87` |
| `lichii-linux-x86_64-pgo.tar.gz` | Linux x86_64 | tar.gz, PGO | 24,835,980 | `14e89925e6b27ce582564f7f47c8a3163a599398fc7e15da8fdcad276f543ed0` |
| `lichii-linux-x86_64.tar.gz` | Linux x86_64 | tar.gz, standard | 30,404,147 | `e40624eb805377e31c929df949c75f243fcba45b0f75eacd593c985886077a93` |
| `lichii-linux-aarch64.AppImage` | Linux ARM64 | AppImage, standard | 103,143,944 | `b29e8bdfff74041abcf9bfba344f611232dd89fbb3b956b98c142228c32cb1b7` |
| `lichii-linux-aarch64-pgo.AppImage` | Linux ARM64 | AppImage, PGO | 131,271,176 | `fb34937a83c1d346805af0e0748acda045bfa3065c91e755ee0997d916f9b0c3` |
| `lichii-linux-aarch64.tar.gz` | Linux ARM64 | tar.gz, standard | 28,133,064 | `c1a46b8b85cf118d5253dae441d7a14942ef5be91c3891a7378d2834c7423ed1` |
| `lichii-linux-aarch64-pgo.tar.gz` | Linux ARM64 | tar.gz, PGO | 23,335,122 | `f04336bca099624f1294dab462b6388e6bb4737c7ce9740a3f37af5baba506a0` |
| `lichii-macos-arm64.zip` | macOS 15+ (Apple Silicon) | zip, not notarized | 74,567,668 | `57e80779bcd6ae3281e06ed01087c761f7a0804f5e1e9efd36c11063e96d389c` |
| `lichii-macos-arm64.dmg` | macOS 15+ (Apple Silicon) | dmg, not notarized | 83,698,900 | `f91755130bba1bde7d00602a44665b65715579aa37a2d8b59dbffbe7628826ab` |

The same digests in `sha256sum` format are in [`SHA256SUMS-build-75.txt`](SHA256SUMS-build-75.txt).

## How to verify a download

Windows (Command Prompt or PowerShell):

```bat
CertUtil -hashfile lichii-windows-x86_64-pgo.zip SHA256
```

Linux:

```sh
sha256sum lichii-linux-x86_64-pgo.AppImage
# or check every file you downloaded at once, from the download folder:
sha256sum --ignore-missing -c SHA256SUMS-build-75.txt
```

macOS:

```sh
shasum -a 256 lichii-macos-arm64.zip
# or
shasum -a 256 --ignore-missing -c SHA256SUMS-build-75.txt
```

If the file name matches but the digest does not, do not run the file. An in-browser checker that hashes the file locally (nothing is uploaded) is on the [download guide](https://lichiiemulator.com/download/).

## OS matrix: which file to pick

| Your system | File | Notes |
|---|---|---|
| Windows 10/11, most people | `lichii-windows-x86_64-pgo.zip` | Bundles its DLLs, no Visual C++ redistributable needed. No DLSS. |
| Windows with NVIDIA RTX, want DLSS | `lichii-windows-x86_64.zip` | MSVC build; also the one to try if the PGO build shows graphical issues. |
| Linux x86_64 | `lichii-linux-x86_64-pgo.AppImage` | glibc 2.39+ (Ubuntu 24.04, Fedora 40, Debian 13, Arch). `chmod +x` and run. tar.gz builds need system Qt 6. |
| Linux ARM64 | `lichii-linux-aarch64.AppImage` | Same glibc/Qt rules. Open issue #95 reports a decompression assert in the aarch64 PGO AppImage only. |
| Mac with Apple Silicon | `lichii-macos-arm64.zip` or `.dmg` | macOS 15 or newer. Not notarized: right-click → Open the first time. |
| Android, iPhone, Intel Mac | none | No official build exists. |

Windows zips are portable: extract the whole archive into its own folder and run `lichii.exe`. The renderer is Vulkan (MoltenVK on macOS). No RAM figure is published; the notes say “Failed to allocate 14336 MiB of backing memory” means Windows ran out of RAM plus page file.

## Compatibility notes (build 75)

There is no official compatibility list. From the release notes and open issues:

| Game | Status | Notes |
|---|---|---|
| Ocarina of Time remake | Boots and plays, heavy issues | Too much fog and glow outdoors; about 12–22 fps on Ryzen 5900X + RTX 3080 |
| Star Fox | Playable with issues | 60 fps instead of 30 in build 75; RTX 50-series can lose the GPU device (notes suggest NVIDIA driver 610.88) |
| Donkey Kong Bananza | Runs well, not locked 60 | Build 70 notes |
| Mario Kart World | Runs, speed varies | 30–38 fps in races on Apple M4 Pro (build 70) |
| Kirby Air Riders | Runs with stalls | Stalls while shaders build |
| Fire Emblem: Fortune’s Weave | Not working well | Black screen (#19) |
| Pokopia | Does not start | Black screen (#79) |

Full table with issue numbers and subsystem status: [compatibility and status](https://lichiiemulator.com/compatibility-status/). How Lichii relates to upstream: [Lichii vs Eglantine](https://lichiiemulator.com/vs-eglantine/).

## Spotting a fake download

- Not hosted on `github.com/zortos293/Lichii` (the old `zortos293/Eglantine` URL redirects to the same repo; any other owner is someone else).
- An APK, iOS app or single `setup.exe` installer.
- Bundled “BIOS”, keys, firmware or “all games included”.
- Asks for a survey, payment, “early access” fee or a password from another site. The README says every release is free and public.
- File name, size or SHA-256 differs from the table above.

More: [Is Lichii safe?](https://lichiiemulator.com/is-lichii-safe/)

## Corrections

Spotted an outdated value? Open an issue here. Bugs in the emulator itself belong on the [official Lichii issue tracker](https://github.com/zortos293/Lichii/issues).

## License

Text in this repository is released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). SHA-256 values and file names are factual data from the official GitHub release.
