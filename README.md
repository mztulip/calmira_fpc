# Calmira II (FPC Port)

**Calmira II** (Online! Release 3.3) — the classic Windows 95-style desktop shell for 16-bit Windows 3.1x — adapted to build with a 100% open-source toolchain using **Free Pascal Compiler (`i8086-win16`)**, [**WUIL**](https://github.com/mztulip/wuil_fpc), and the **Open Watcom** linker (`wlink`), without requiring Borland Delphi 1.0.

![Calmira II Start Menu](docs/screenshots/calmira_start_menu.png)

![Calmira II File Manager](docs/screenshots/calmira_file_manager.png)

*Screenshots captured from the FPC-compiled Calmira II running on [`win16Loader`](https://github.com/mztulip/win16Loader).*

---

## Original Project

This repository is based on the original **Calmira II (Online! Release 3.3)** source code:

- **Original website:** [http://www.calmira.org](http://www.calmira.org)
- **Original authors:**
  - Copyright (C) 1997–1998 Li-Hsin Huang
  - Copyright (C) 1998–2002 Calmira Online!

## Repository Structure

- `SRC/` — Calmira II shell source code (`CALMIRA.DPR` and units)
- `VCL/` — Calmira custom VCL components
- `BMP/`, `HELP/` — Bitmaps and help assets
- `wuil/` *(submodule: [`mztulip/wuil_fpc`](https://github.com/mztulip/wuil_fpc))* — Open-source Delphi 1.0 VCL-compatible GUI library for `i8086-win16`
- `fpc-source/` *(submodule: [`mztulip/FPCSource`](https://github.com/mztulip/FPCSource))* — Free Pascal Compiler fork with `i8086-win16` HUGE memory model (`-WmHUGE`) and Delphi 1.0 compatibility fixes

## Cloning

Clone with submodules included:

```bash
git clone --recursive git@github.com:mztulip/calmira_fpc.git
```

## Building

1. Build the `i8086-win16` cross-compiler from `fpc-source/` (see `wuil/fpc_readme.md` for details).
2. Ensure Open Watcom `wlink` is installed and available in your `PATH`.
3. Compile Calmira II using the helper script in `wuil/`:

```bash
./wuil/fpc16 -Mdelphi -CX -XX \
    -FuSRC -FuVCL -Fuwuil \
    -FiSRC -FiVCL \
    SRC/CALMIRA.DPR
```

## License

- **Calmira II (`SRC/`, `VCL/`, `BMP/`, `HELP/`)** is licensed under the **GNU General Public License v2.0 (or later)** — see [`LICENSE`](LICENSE).
- Submodules [`wuil`](https://github.com/mztulip/wuil_fpc) (MIT) and [`fpc-source`](https://github.com/mztulip/FPCSource) (GPL / modified LGPL) retain their own respective licenses.
