# Hydra — Multi-System Emulation Core Engine & Library Workbench

Hydra is a high-performance, AGPL-3.0 multi-system emulator and ROM management workbench built with C++20 and Qt 6 / QML (`Hydra.exe`). Designed around a **Vulkan 1.3 & DirectX 12_1** graphics rendering architecture and modular C++ emulation cores (`core/`), Hydra delivers ultra-low-latency emulation, AI-assisted upscaling, headless verification, and precise system rendering.

---

## 🎮 Emulation Cores & System Compatibility

Hydra's architecture is organized into standalone C++ system cores with dedicated Vulkan/DX12 video rendering pipelines, audio synthesis, and hardware bus emulation.

### 🕹️ 8-Bit & 16-Bit Consoles (Stage 1)
- **Sega Master System (SMS) & Game Gear (GG)**: Z80 CPU, VDP Mode 4 graphics rendering with CRAM wrap, PSG audio synthesis.
- **Sega Mega Drive / Genesis (MD)**: Dual Motorola 68000 CPU execution, VDP plane A/B geometry, YM2612 FM audio & PSG synthesis.
- **Nintendo Entertainment System (NES)**: Ricoh 2A03 CPU core, PPU background/sprite rendering with NMI and left-clip support, APU sound channels.
- **Super Nintendo (SNES)**: 65C816 CPU, SPC700 audio DSP kernel, multi-mode PPU background layering, OAM sprite ordering.

### 📱 Portable & Handheld Systems (Stage 2 & Stage 7-8)
- **Game Boy (GB) & Game Boy Color (GBC)**: Sharp LR35902 CPU, VRAM bank switching, palette mappings, APU audio.
- **Game Boy Advance (GBA)**: ARM7TDMI 32-bit RISC CPU core, DMA transfers, Mode 0-5 tile/bitmap VDP rendering.
- **Nintendo DS (NDS) & 3DS**: ARM9/ARM7 dual-processor coordination, dual-screen display compositing, touch input mapping.
- **PlayStation Portable (PSP) & PS Vita**: MIPS/Allegrex HLE syscall dispatch, GPU command buffer rendering, UMD ISO loading.
- **Nintendo Switch**: ARM64 quad-core execution, Maxwell NVN GPU pipeline emulation, and Horizon OS HLE services.

### 🖥️ Microcomputers & Vintage PC Systems (Stage 3-4)
- **MSX / MSX2**: Z80 execution, VDP video chip handling, PSG sound synthesis.
- **PC-8801 / PC-9801**: NEC V30 / x86 micro-architecture execution, Kanji font ROM rendering, `.hdi` / `.d88` image mounting.
- **DOS / MS-DOS Engine**: x86 Real-Mode execution engine and BIOS/DOS system interrupt virtualization.

### 🌀 32-Bit, 3D & Modern Consoles (Stage 5-10)
- **Sega 32X, Sega CD & Saturn**: Dual SH-2 CPU pipelines, Mega-CD sub-CPU, VDP1 texture rendering & VDP2 plane compositor.
- **PC Engine / TurboGrafx-16 & PC-FX**: HuC6280 CPU, VDP tile rendering.
- **PlayStation (PS1) & PlayStation 2 (PS2)**: MIPS R3000A / Emotion Engine (EE) R5900, GS rasterizer, SPU/SPU2 audio.
- **Nintendo 64 (N64) & GameCube**: VR4300 CPU / Flipper GPU, RCP RSP/RDP command handling.
- **Xbox (Original) & Xbox 360**: x86 / Xenon PowerPC CPU execution, NV2A / Xenos GPU Vulkan/DX12 translation layers.
- **PlayStation 3 (PS3)**: Cell Broadband Engine (PPU & 8x SPU) architecture execution, RSX Synthesizer GPU translation layer.

---

## ⚡ Core Systems & Rendering Pipeline

| Subsystem | Features & Capabilities | Status / Roadmap |
|---|---|---|
| **Graphics Engine** | **Vulkan 1.3 & DirectX 12_1** graphics pipeline | Active |
| **AI Upscaling** | **NVIDIA DLSS**, **Intel XeSS**, and **AMD FSR** temporal upscaling integration | Roadmap |
| **Software Upscaling** | **xBRZ**, HQ4x, Bicubic, Integer Scaling, and CRT scanline shader filters | Active / Expanding |
| **Frame Generation** | Motion-interpolation and frame generation pipelines for high-refresh displays | Roadmap |
| **CPU Execution** | Cycle-accurate & HLE execution loops for Z80, 68000, 6502, 65C816, ARM7/ARM64, MIPS, SH-2, PowerPC, Cell | Active / Expanding |
| **Audio Processing** | Low-latency audio buffer mixing, PSG, FM synthesis (YM2612/YM2151), SPC700 DSP | Active |
| **Input & Controls** | Gamepad auto-mapping, low-latency raw input, customizable touch controls | Active |
| **Save States & Rewind** | Deterministic RAM snapshotting, rapid rewind buffer, cheat engine | Active |
| **ROM Management** | Header inspection, hash database verification, automatic cover art caching | Active |

---

## 🏗️ Architecture & Technology Stack

- **Graphics APIs**: Vulkan 1.3 & DirectX 12_1.
- **UI Shell**: Qt 6.12, QML desktop interface, custom dark theme viewport.
- **Emulation Cores**: Pure, zero-dependency C++20 modules co-located under `core/`.
- **Headless Testing**: CTest test suite validating core CPU execution, memory maps, and render targets.
- **Build System**: CMake 3.25+ build matrix (`build.bat` script).

---

## 🛠️ Building & Running

### Prerequisites
- **Visual Studio 2022** (C++20 MSVC compiler)
- **Qt 6.12** (`msvc2022_64`)
- **Vulkan SDK 1.3+**
- **CMake 3.25+**

### Build Commands

```bat
:: Build Release binary (Hydra.exe)
build.bat Release

:: Launch Hydra
run.bat
```

---

## 📜 License

Hydra is licensed under the **GNU Affero General Public License v3.0** (AGPL-3.0). See [`LICENSE`](LICENSE) for details.
