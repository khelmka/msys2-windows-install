## MSYS2 MINGW64 Install

Navigate to https://www.msys2.org/#installation and download and run the **Windows x86-64** installer. Press next on all options. When finished, if the MSYS2 UCRT64 window appears, close it as we won't be using the UCRT64 environment.

After closing all **MSYS2** windows, find the **MSYS2 MINGW64** terminal application (perform a basic Windows app search) and run it.

Within the **MSYS2 MINGW64** terminal, install the base-development toolchain

```bash
pacman -S base-devel
```

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