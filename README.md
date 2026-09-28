# MSYS2 MINGW64 Install

Navigate to https://www.msys2.org/#installation and download and run the **Windows x86-64** installer. Press next on all options. When finished, if the MSYS2 UCRT64 window appears, close it as we won't be using the UCRT64 environment.

After closing all **MSYS2** windows, find the **MSYS2 MINGW64** terminal application (perform a basic Windows app search) and run it.

Within the **MSYS2 MINGW64** terminal, install the base-development toolchain

```bash
pacman -S base-devel
```

Install **unzip** for unzipping and installing files (optional)
```
pacman -S unzip
```

## C++ Development

Install the **MinGW** toolchain:

```bash
pacman -S mingw-w64-x86_64-toolchain
```

Ensure you have a version of **GCC** that supports **C++20** (GCC 10+)

```bash
gcc --version
```

Install **CMake** build tool

```bash
pacman -S mingw-w64-x86_64-cmake
```

Install the **Ninja** build system

```bash
pacman -S mingw-w64-x86_64-ninja
```

Install **gdb** for debugging (optional)

```bash
pacman -S mingw-w64-x86_64-gdb
```

To check the list of installed packages, use the following command (optional)

```bash
pacman -Q
```

## Rust Development

Install **cargo-c**
```bash
pacman -S mingw-w64-x86_64-cargo-c
```

Install **cargo-binstall** (optional for installed precompiled binaries)
```bash
cargo install cargo-binstall
```

## Program Profiling via Samply (requires root access)
Install **Samply** via cargo
```bash
cargo binstall samply
```

(or) Install via curl and unzip
```bash
curl -L -o samply.zip https://github.com/mstange/samply/releases/latest/download/samply-x86_64-pc-windows-msvc.zip
unzip samply.zip -d /mingw64/bin/
```

Verify installation
```bash
samply --version
```

> [!NOTE]
> Samply may require xperf to function on Windows, which is part of the **Windows Performance Toolkit** from the **Windows Assessment and Deployment Kit (Windows ADK)**: https://learn.microsoft.com/en-us/windows-hardware/get-started/adk-install

> [!IMPORTANT]
> You must compile your program with the following flags:
> ```cmake
> "CMAKE_CXX_FLAGS": "-gcodeview"
> "CMAKE_EXE_LINKER_FLAGS": "-Wl,--pdb=${sourceDir}/build/my-application.pdb"
> ```
> To be able to use Samply:
> ```bash
> samply record ./build/my-application.exe
> ```

Depending on your program, you may want to compile in Debug or RelWithDebugInfo for different levels of profiling information.