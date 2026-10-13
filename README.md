<p align="center">
  <a href="https://workflowind.agcunae.com/apps/">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="docs/brand/novafoods-logo-white.svg">
      <img alt="Nova Foods" src="docs/brand/novafoods-logo.svg" width="200">
    </picture>
  </a>
</p>

<h1 align="center">Nova Deck</h1>

<p align="center">
  <b>Presentations and slide shows; an open-source, clean-room reimplementation of Microsoft PowerPoint, rebuilt in pure Rust.</b>
</p>

<p align="center">
  Build decks with themes, layouts, shapes, pictures, tables, charts, transitions and animations,
  open and save PowerPoint files, and present them full screen. Native on macOS, Windows, Linux
  and FreeBSD, and in the browser. Every button is also a command that the CLI and AI agents
  (through MCP) can drive.
</p>

<p align="center">
  <img alt="Status: early development" src="https://img.shields.io/badge/status-early%20development-f26b1d?style=flat-square">
  <img alt="License: MIT OR Apache-2.0" src="https://img.shields.io/badge/license-MIT%20OR%20Apache--2.0-blue?style=flat-square">
  <img alt="Written in Rust" src="https://img.shields.io/badge/written%20in-Rust-b7410e?style=flat-square">
  <img alt="Platforms" src="https://img.shields.io/badge/platforms-macOS%20·%20Windows%20·%20Linux%20·%20BSD%20·%20Web-555?style=flat-square">
</p>

<p align="center">
  <a href="https://workflowind.agcunae.com/inbox"><img alt="Talk to the Nova Foods IT team" src="https://img.shields.io/badge/Join%20us%20on%20Suporte-5865F2?style=for-the-badge&logo=discord&logoColor=white" height="40"></a>
</p>

<p align="center">
  <a href="https://workflowind.agcunae.com/apps/novadeck"><b>Nova Deck on workflowind.agcunae.com/apps</b></a> ·
  <a href="https://workflowind.agcunae.com/apps/">Nova Foods</a> ·
  <a href="https://workflowind.agcunae.com/apps">All Nova Foods Apps</a>
</p>

> [!NOTE]
> **Nova Foods is a community of artists from all walks of life.** Painters, photographers,
> filmmakers, illustrators, designers, animators, hobbyists, and people who picked up a pencil
> last week. If you make things, you're one of us. **[Come say hi on Suporte](https://workflowind.agcunae.com/inbox).**

<p align="center">
  <img alt="Nova Deck editing a slide: ribbon, slide thumbnails with sections, a process diagram on the canvas, notes and status bar" src="docs/images/editor.png" width="900">
</p>

<p align="center">
  <a href="#what-works-today">What works</a> ·
  <a href="#getting-started">Getting started</a> ·
  <a href="#agents-cli-and-mcp">Agents, CLI and MCP</a> ·
  <a href="#roadmap">Roadmap</a> ·
  <a href="#downloads">Downloads</a> ·
  <a href="#the-crafting-apps">The Nova Foods Apps</a> ·
  <a href="#license-and-credits">License</a>
</p>

## What works today

Nova Deck is in alpha, heading for beta (see the [roadmap](ROADMAP.md)).
Today it can:

- **Make decks**: slide masters and eleven layouts with placeholders that inherit position and
  formatting, eight original themes with colour and font schemes, sections, notes, comments,
  headers and footers, custom slide sizes.
- **Draw**: 150+ preset shapes with adjust handles, connectors that stay glued to shapes, freeform,
  curve and scribble tools, merge shapes (union, combine, fragment, intersect, subtract), gradient,
  picture and pattern fills, outlines with dashes and arrowheads, shadows, glow, soft edges and
  reflections.
- **Write**: in-place text editing with full font and paragraph formatting, bullets and numbering,
  columns, autofit, vertical text, fields and hyperlinks.
- **Add content**: pictures with crop and corrections, tables with styles, charts, SmartArt basics,
  audio and video (MP3, AAC, FLAC, ALAC, Ogg, Opus, WAV, AIFF; H.264, HEVC, VP9, AV1).
- **Present**: transitions (including Morph), entrance/emphasis/exit and motion-path animations,
  by-paragraph builds, full-screen slide show, presenter view, pen, rehearse timings, media playback.
- **Exchange files**: open and save PowerPoint `.pptx`, export PDF (slides, notes pages, handouts
  with selectable text), PNG/JPEG and outlines. Unsaved work is kept by AutoRecover.
- **Automate**: 200+ commands with undo, all scriptable from the CLI, a JSON control channel and an
  MCP server for AI agents.

<table>
  <tr>
    <td width="50%"><img alt="A selected shape with the Shape Format tab" src="docs/images/shape-format.png"><br><sub>Shape Format contextual tab and selection handles</sub></td>
    <td width="50%"><img alt="The Format Shape pane editing a gradient fill" src="docs/images/format-pane.png"><br><sub>Format Shape pane: gradient type, direction and stops</sub></td>
  </tr>
  <tr>
    <td width="50%"><img alt="Slide Sorter view with transitions under each slide" src="docs/images/slide-sorter.png"><br><sub>Slide Sorter with each slide's transition</sub></td>
    <td width="50%"><img alt="Nova Deck in dark mode showing a chart slide" src="docs/images/dark-mode.png"><br><sub>Dark mode, with a native chart</sub></td>
  </tr>
</table>

<p align="center">
  <img alt="All eight slides of the Northern Lights sample deck" src="docs/images/sample-deck.png" width="900"><br>
  <sub>The built-in sample deck, rendered by <code>novadeck-cli render --sample --all</code></sub>
</p>

## Getting started

```sh
git clone https://github.com/EuLucaDev/novadeck
cd novadeck
cargo run --release -p novadeck-cli -- render --sample --all --scale 1 out/
```

On Linux, the build also needs the ALSA headers for slide-show sound: `alsa-lib-devel` on Fedora,
`libasound2-dev` on Debian and Ubuntu, `alsa-lib` on Arch. Without them it stops at `alsa-sys`.

Fonts come from [novafoods-fonts](https://github.com/EuLucaDev/novafoods-fonts): clone it next to this repo
(`../novafoods-fonts`) and local builds pick it up automatically; without it Nova Deck uses your system
fonts.

Each [GitHub release](https://github.com/EuLucaDev/novadeck/releases) has ready-made builds, on Linux as
an AppImage, a `.deb`, an `.rpm` and a tarball. On Gentoo, the community [::snakebyte
overlay](https://github.com/switch87/snakebyte-overlay) packages the Linux release as
`app-office/novadeck-bin` (not maintained by the Nova Deck team):

```sh
eselect repository add snakebyte git https://github.com/switch87/snakebyte-overlay.git
emaint sync -r snakebyte
echo 'app-office/novadeck-bin ~amd64' >> /etc/portage/package.accept_keywords/novadeck
emerge --ask app-office/novadeck-bin
```

### Logs

The desktop app writes its `log` records to standard error and to `logs/novadeck.log` in the
settings directory, beside `ui.json` and `prefs.json` (Linux `~/.config/novadeck/logs/`, or
`$XDG_CONFIG_HOME/novadeck/logs/`; macOS `~/Library/Application Support/Nova Deck/logs/`; Windows
`%APPDATA%\Nova Deck\logs\`). A start from a desktop menu or the Dock has no terminal, so this file
is what to attach to a bug report: the crash guard's panic report, a failed crash-recovery save,
PowerPoint parts skipped on import and audio output problems land there. Each launch moves the
previous log to `novadeck.1.log` (and that one to `novadeck.2.log`), so the log of a run that
crashed survives the next start. The file stops growing at 16 MiB. `--version` writes no file.

| Variable | Effect |
|---|---|
| `RUST_LOG` | Log levels for standard error and the log file. Default: `info` for Nova Deck's own crates, `warn` for everything else. env_logger-style directives replace that, e.g. `RUST_LOG=debug`, `RUST_LOG=warn,novadeck_pptx=trace` or `RUST_LOG=info,wgpu_core=warn`; a directive ending in `*` covers every target starting with it (`novadeck*=debug`). |

The logger is `apps/novadeck/src/logging.rs`; the realtime audio callback does not log. The web
app logs to the browser console instead.

## Agents, CLI and MCP

Every action in Nova Deck is a command with a stable id, so people, scripts and AI agents use the
same verbs:

```sh
novadeck-cli commands format.          # list commands
novadeck-cli run --sample --cmd 'slide.new={"layout":"titleOnly","title":"Hello"}' --save hello.novadeck
novadeck-cli mcp                       # MCP server over stdio (headless)
novadeck-cli mcp --connect 7990        # drive the running app (novadeck --control 7990)
```

## Roadmap

Nova Deck is in **alpha**. It covers **79% of PowerPoint's features by breadth** (92% of the core
ones, measured) and is about **55% of the way to replacing PowerPoint for real work** (estimated).
See [ROADMAP.md](ROADMAP.md) for the stage, numbers by dimension and what's next,
[docs/target-app-parity.md](docs/target-app-parity.md) for the full assessment,
[docs/gaps.md](docs/gaps.md) for every known shortfall and
[docs/parity-checklist.md](docs/parity-checklist.md) for the feature-by-feature checklist.

## Downloads

**Download Nova Deck** from GitHub: the [latest release](https://github.com/EuLucaDev/novadeck/releases/latest) has every build listed below, and [all releases](https://github.com/EuLucaDev/novadeck/releases) has earlier versions and their notes. `<ver>` in the file names is the version number, and `SHA256SUMS.txt` lists a checksum for every file.

### Windows

| Build | Installer | Portable |
|---|---|---|
| x64 (64-bit Intel/AMD) | `novadeck-<ver>-windows-x64.msi` | `novadeck-<ver>-windows-x64-portable.zip` |
| arm64 (Snapdragon and other ARM PCs) | `novadeck-<ver>-windows-arm64.msi` | `novadeck-<ver>-windows-arm64-portable.zip` |
| x86 (32-bit) | `novadeck-<ver>-windows-x86.msi` | `novadeck-<ver>-windows-x86-portable.zip` |

Installers and executables are code-signed.

**If the app doesn't open on Windows:** the desktop app initializes only DirectX 12 by default.
Letting wgpu also create an OpenGL instance can crash some graphics drivers (AMD's
`atio6axx.dll`) before the window appears, so the app would flash in Task Manager and quit.
`WGPU_BACKEND` overrides the default for troubleshooting (for example `dx12` or `vulkan`). In
PowerShell, from the folder containing the executable:

```powershell
$env:WGPU_BACKEND = "vulkan"
& .\novadeck.exe
Remove-Item Env:WGPU_BACKEND                     # restore the default for later launches
```

An explicit `gl` override can bring the driver crash back on affected systems. The macOS, Linux
and web backend defaults are unchanged.

### macOS

| Build | File | Notes |
|---|---|---|
| App, universal (Apple silicon + Intel) | `novadeck-<ver>-macos-universal.dmg` | Signed and notarized |
| Command-line tool, universal | `novadeck-cli-<ver>-macos-universal.zip` | Signed and notarized |

### Linux

| Format | x86_64 | aarch64 (ARM64) | Notes |
|---|---|---|---|
| AppImage | `novadeck-<ver>-linux-x86_64.AppImage` | `novadeck-<ver>-linux-aarch64.AppImage` | Runs anywhere; updates itself with [AppImageUpdate](https://github.com/AppImageCommunity/AppImageUpdate) (`.zsync` files) |
| Flatpak | `novadeck-<ver>-linux-x86_64.flatpak` | `novadeck-<ver>-linux-aarch64.flatpak` | Sandboxed; `flatpak install --user <file>` |
| Debian/Ubuntu | `novadeck-<ver>-linux-x86_64.deb` | `novadeck-<ver>-linux-aarch64.deb` | |
| Fedora/RHEL/openSUSE | `novadeck-<ver>-linux-x86_64.rpm` | `novadeck-<ver>-linux-aarch64.rpm` | |
| Tarball | `novadeck-<ver>-linux-x86_64.tar.gz` | `novadeck-<ver>-linux-aarch64.tar.gz` | Unpack anywhere |

RISC-V 64 (riscv64): `novadeck-<ver>-linux-riscv64.tar.gz`, a tarball only (cross-compiled; needs glibc 2.39+, e.g. Ubuntu 24.04+).

### FreeBSD

| Build | File |
|---|---|
| x86_64 | `novadeck-<ver>-freebsd-x86_64.tar.gz` |

### Web (WebAssembly)

| Build | File | Notes |
|---|---|---|
| Static site | `novadeck-web-<ver>.zip` | Runs in a modern browser; host it on any static server |

## The Nova Foods Apps

Nova Deck is one of the **Nova Foods Apps**: free, open-source creative tools from the
[Nova Foods](https://workflowind.agcunae.com/apps/) team, each written from scratch in Rust and each able to
stand on its own.

| | App | What it's for | Code | Learn more |
|:-:|---|---|---|---|
| <img src="https://raw.githubusercontent.com/EuLucaDev/novaphoto/main/assets/app-icon/hicolor/64x64/apps/br.com.novafoods.novaphoto.png" alt="" width="32" height="32"> | **Nova Photo** | Image editing: layers, masks, type and real PSD files | [GitHub](https://github.com/EuLucaDev/novaphoto) | [Website](https://workflowind.agcunae.com/apps/novaphoto) |
| <img src="https://raw.githubusercontent.com/EuLucaDev/novavector/main/assets/app-icon/hicolor/64x64/apps/br.com.novafoods.novavector.png" alt="" width="32" height="32"> | **Nova Vector** | Vector illustration | [GitHub](https://github.com/EuLucaDev/novavector) | [Website](https://workflowind.agcunae.com/apps/novavector) |
| <img src="https://raw.githubusercontent.com/EuLucaDev/novafilm/main/assets/app-icon/hicolor/64x64/apps/br.com.novafoods.novafilm.png" alt="" width="32" height="32"> | **Nova Film** | Video editing, color and sound | [GitHub](https://github.com/EuLucaDev/novafilm) | [Website](https://workflowind.agcunae.com/apps/novafilm) |
| <img src="https://raw.githubusercontent.com/EuLucaDev/novalight/main/assets/app-icon/hicolor/64x64/apps/br.com.novafoods.novalight.png" alt="" width="32" height="32"> | **Nova Light** | Photo library and raw development | [GitHub](https://github.com/EuLucaDev/novalight) | [Website](https://workflowind.agcunae.com/apps/novalight) |
| <img src="https://raw.githubusercontent.com/EuLucaDev/novapdf/main/assets/app-icon/hicolor/64x64/apps/br.com.novafoods.novapdf.png" alt="" width="32" height="32"> | **Nova PDF** | Reading, organizing and protecting PDFs | [GitHub](https://github.com/EuLucaDev/novapdf) | [Website](https://workflowind.agcunae.com/apps/novapdf) |
| <img src="https://raw.githubusercontent.com/EuLucaDev/novaeffect/main/assets/app-icon/hicolor/64x64/apps/br.com.novafoods.novaeffect.png" alt="" width="32" height="32"> | **Nova Effect** | Motion graphics and visual effects | [GitHub](https://github.com/EuLucaDev/novaeffect) | [Website](https://workflowind.agcunae.com/apps/novaeffect) |
| <img src="https://raw.githubusercontent.com/EuLucaDev/novadesign/main/assets/app-icon/hicolor/64x64/apps/br.com.novafoods.novadesign.png" alt="" width="32" height="32"> | **Nova Design** | Page layout and publishing | [GitHub](https://github.com/EuLucaDev/novadesign) | [Website](https://workflowind.agcunae.com/apps/novadesign) |
| <img src="https://raw.githubusercontent.com/EuLucaDev/novadeck/main/assets/app-icon/hicolor/64x64/apps/br.com.novafoods.novadeck.png" alt="" width="32" height="32"> | **Nova Deck** | **Presentations and slide shows · you are here** | [GitHub](https://github.com/EuLucaDev/novadeck) | [Website](https://workflowind.agcunae.com/apps/novadeck) |

And [**Nova Foods**](https://workflowind.agcunae.com/apps/) itself, our AI image and video studio for artists who want real control.

<br>

<p align="center">
  <a href="https://workflowind.agcunae.com/inbox"><img alt="Talk to the Nova Foods IT team" src="https://img.shields.io/badge/Join%20us%20on%20Suporte-5865F2?style=for-the-badge&logo=discord&logoColor=white" height="40"></a>
</p>

<h3 align="center">Come make things with us</h3>

<p align="center">
  Our Suporte is where artists of every kind hang out: people who paint, shoot, draw, cut film,
  set type, and people still figuring out what they like to make. Share what you're working on,
  ask for help, tell us what's broken, or tell us what you wish these tools could do.
  Whatever your medium and however long you've been at it, you're welcome here.
</p>

<p align="center">
  <a href="https://workflowind.agcunae.com/inbox"><b>workflowind.agcunae.com/inbox</b></a> ·
  <a href="https://workflowind.agcunae.com/apps/">workflowind.agcunae.com/apps</a> ·
  <a href="https://workflowind.agcunae.com/apps">The Nova Foods Apps</a> ·
  <a href="https://workflowind.agcunae.com/apps/novadeck">Nova Deck</a>
</p>

## License and credits

Nova Deck is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE), at your option.
Copyright (c) 2026 Nova Foods Team and the Nova Deck contributors. Required notices are in [NOTICE](NOTICE).

Bundled fonts, icons, images and other assets keep their own open licenses; each one is listed
with its author, source and license in [ATTRIBUTION.md](ATTRIBUTION.md).

Nova Deck's themes, layouts, shape geometry, icons and sample decks are original work, drawn or
generated in code; no Microsoft artwork, fonts, themes or templates are used.

The Nova Foods name, wordmark and logos in [`docs/brand/`](docs/brand/) are trademarks of the
Nova Foods Team and are not covered by this license. They may be used only unmodified, and only as
part of this repository and Nova Deck, under [`docs/brand/LICENSE-brand.txt`](docs/brand/LICENSE-brand.txt).
Forks and modified versions must remove them.

<sub>Microsoft and PowerPoint are trademarks of the Microsoft group of companies. Adobe, Photoshop, Illustrator, Premiere Pro, Lightroom, Acrobat, After Effects and InDesign are trademarks or registered trademarks of Adobe Inc. in the United States and/or other countries. Nova Deck is an independent, open-source project and is not affiliated with, sponsored by or endorsed by Microsoft Corporation or Adobe Inc.; these names are used only to describe the workflows it is compatible with.</sub>

<p align="center">
  <a href="https://workflowind.agcunae.com/apps/"><img alt="Nova Foods" src="docs/brand/novafoods-mark.svg" width="28"></a><br>
  <sub>Made by the <a href="https://workflowind.agcunae.com/apps/">Nova Foods</a> team and community.</sub>
</p>
