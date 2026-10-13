# Fixed Program Module

**FPM**, or Fixed Program Module, is a lightweight overlay/hook build system that allows for static-program-based code injection for Pokémon Black/White.

## How do I use this?

Because FPM is designed to be lightweight and have a minimal presence, this repository is a bare-bones template with no content on its own.  
Press the "[Use this template](https://github.com/Basics-V/FPM/generate)" button to create a repository based off of this one.  
Then, start writing your code using the following project structure:

```bash
fpm-template/
├── hooks/ # Access your code from the game with hooks
│   ├── overlay/ # Overlay names are in hexadecimal and follow the main_XXXX format
│   │   ├── main_005D.c
│   │   └── main_000A.c
│   ├── arm9.c # ARM9 is always a lowercase filename
│   └── fpm.c # Don't edit this unless you know what you're doing!
├── src/ # Write your own program code and place it in here (this is compiled to overlay 237)
│   ├── fairy-type.c
│   ├── poke-radar.c
│   ├── stat-viewer.c
│   └── util.cpp
├── include/ # Put definitions for functions...
│   ├── overlay/ # ...in their respective overlays...
│   │   ├── main_005D.h
│   │   └── main_000A.h
│   ├── arm9.h # ...or in the ARM9!
│   ├── fairy-type.h
│   ├── poke-radar.h
│   ├── stat-viewer.h
│   ├── util.h
│   └── wbtypes.h
├── esdb/ # External symbol database (from Ghidra/IDA)
│   ├── IRBO.yml # Black 1
│   └── IRAO.yml # White 1
├── IRBO.nds # Your ROM before code injection, such as IRBO, IRAO, etc.
├── data/
├── tools/
└── Makefile
```

### Requirements
(General, OS-specific requirements can be found below)

- [Python (>=3.10)][python]
- [NitroPacker][nitropacker]
- [GNU Make](https://www.gnu.org/software/make/)
- [ARM GNU Toolchain][arm]

### macOS

GNU Make is included on your system already.  
Install [Homebrew](https://brew.sh/) if you haven't already.  
Download [NitroPacker][nitropacker] and add it to your PATH as `nitropacker`.

With Homebrew: `brew install --cask gcc-arm-embedded`

### Windows

Install [Git Bash](https://github.com/git-for-windows/git/releases/latest) and [Chocolatey](https://chocolatey.org/install#install-step2) if you haven't already.  
Download the [Python installer][python] and install it.  
Download the latest `arm-none-eabi` version (mingw) of the [ARM GNU Toolchain][arm] and add it to the PATH.  
Download [NitroPacker][nitropacker] and add it to your PATH.

With Chocolatey: `choco install make`

### Building

In the shell (Git Bash for Windows, Terminal for macOS):
```sh
$ make
```

[python]: https://www.python.org/downloads/
[nitropacker]: https://github.com/haroohie-club/NitroPacker/releases/latest
[arm]: https://gitlab.arm.com/tooling/gnu-toolchains-for-arm
