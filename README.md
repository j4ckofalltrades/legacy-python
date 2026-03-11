# Legacy Python

Base images for end-of-life Python versions (0.9.1, 1.x, 2.x, and select 3.x releases). More recent versions of Python 3 are readily available through the official [Docker Python image](https://hub.docker.com/_/python) and version management tools like [pyenv](https://github.com/pyenv/pyenv) or [uv](https://github.com/astral-sh/uv).

## Usage

### Build and run locally

```sh
docker build -t legacy-python:2.0 ./2.0
docker run -it legacy-python:2.0
```

### Pulling from Docker Hub or GitHub Container Registry

```sh
# from Docker Hub
docker pull j4ckofalltrades/legacy-python:2.0
docker run -it j4ckofalltrades/legacy-python:2.0
```

```sh
# from GitHub Container Registry
docker pull ghcr.io/j4ckofalltrades/legacy-python:2.0
docker run -it ghcr.io/j4ckofalltrades/legacy-python:2.0
```

## Versions

Images are available on [Docker Hub](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags) and [GitHub Container Registry](https://github.com/j4ckofalltrades/legacy-python/pkgs/container/legacy-python/versions?filters%5Bversion_type%5D=tagged).

| Version | Dockerfile                           | Release Date   |
|---------|--------------------------------------|----------------|
| 0.9.1   | [0.9.1/Dockerfile](0.9.1/Dockerfile) | February 1991  |
| 1.0.1   | [1.0.1/Dockerfile](1.0.1/Dockerfile) | February 1994  |
| 1.1     | [1.1/Dockerfile](1.1/Dockerfile)     | October 1994   |
| 1.2     | [1.2/Dockerfile](1.2/Dockerfile)     | April 1995     |
| 1.3     | [1.3/Dockerfile](1.3/Dockerfile)     | October 1995   |
| 1.4     | [1.4/Dockerfile](1.4/Dockerfile)     | October 1996   |
| 1.5     | [1.5/Dockerfile](1.5/Dockerfile)     | December 1997  |
| 1.6     | [1.6/Dockerfile](1.6/Dockerfile)     | September 2000 |
| 2.0     | [2.0/Dockerfile](2.0/Dockerfile)     | October 2000   |
| 2.1.3   | [2.1.3/Dockerfile](2.1.3/Dockerfile) | April 2002     |
| 2.2     | [2.2/Dockerfile](2.2/Dockerfile)     | December 2001  |
| 2.3     | [2.3/Dockerfile](2.3/Dockerfile)     | July 2003      |
| 2.4     | [2.4/Dockerfile](2.4/Dockerfile)     | November 2004  |
| 2.5     | [2.5/Dockerfile](2.5/Dockerfile)     | September 2006 |
| 2.6     | [2.6/Dockerfile](2.6/Dockerfile)     | October 2008   |
| 2.7     | [2.7/Dockerfile](2.7/Dockerfile)     | July 2010      |
| 3.0     | [3.0/Dockerfile](3.0/Dockerfile)     | December 2008  |
| 3.1     | [3.1/Dockerfile](3.1/Dockerfile)     | June 2009      |
| 3.2     | [3.2/Dockerfile](3.2/Dockerfile)     | February 2011  |
| 3.3     | [3.3/Dockerfile](3.3/Dockerfile)     | September 2012 |
| 3.4     | [3.4/Dockerfile](3.4/Dockerfile)     | March 2014     |
| 3.5     | [3.5/Dockerfile](3.5/Dockerfile)     | September 2015 |
| 3.6     | [3.6/Dockerfile](3.6/Dockerfile)     | December 2016  |
| 3.7     | [3.7/Dockerfile](3.7/Dockerfile)     | June 2018      |
| 3.8     | [3.8/Dockerfile](3.8/Dockerfile)     | October 2019   |
| 3.9     | [3.9/Dockerfile](3.9/Dockerfile)     | October 2020   |

## Patches

Some versions require patches to compile on modern systems. All images are built on `debian:bullseye` using the following toolchain:

| Tool | Version | Notes |
|------|---------|-------|
| GCC | 10.2.1 | Via `build-essential` |
| GNU ld (binutils) | 2.35.2 | |
| GNU Make | 4.3 | |
| glibc | 2.31 | Source of the `getline` symbol conflict (added in glibc 2.9) |
| libxcrypt | 4.4.18 | `crypt()` split out of libc; requires explicit `-lcrypt` |

### [1.0.1](1.0.1/diff.patch)

Renames Python's internal `getline()` to `mygetline()` to avoid a duplicate symbol conflict with the POSIX `getline()` added to glibc.

### [1.1](1.1/diff.patch)

Renames Python's internal `getline()` to `mygetline()` to avoid a duplicate symbol conflict with the POSIX `getline()` added to glibc. Also enables the `-lcrypt` linker flag required by the crypt module on modern Linux (where `crypt()` is no longer part of libc), and fixes unsafe `va_list` handling. On x86-64, `va_list` is an array type that decays to a pointer when passed by value, so `va_arg` calls inside `vmkvalue` and `vgetargs1` were silently consuming the original argument list at the call site rather than a local copy. The fix uses `memcpy` to create a local `va_list` copy inside each function and changes `vgetargs1` to take `va_list *` instead of `va_list`.

### [1.2](1.2/diff.patch)

Renames Python's internal `getline()` to `mygetline()` to avoid a duplicate symbol conflict with the POSIX `getline()` added to glibc. Also enables the `-lcrypt` linker flag required by the crypt module on modern Linux (where `crypt()` is no longer part of libc).

### [1.3](1.3/diff.patch)

Renames Python's internal `getline()` to `mygetline()` to avoid a duplicate symbol conflict with the POSIX `getline()` added to glibc. Also enables the `-lcrypt` linker flag required by the crypt module on modern Linux (where `crypt()` is no longer part of libc).

### [1.4](1.4/diff.patch)

Renames Python's internal `getline()` to `mygetline()` to avoid a duplicate symbol conflict with the POSIX `getline()` added to glibc. Also enables the `-lcrypt` linker flag required by the crypt module on modern Linux (where `crypt()` is no longer part of libc).

### [1.5](1.5/diff.patch)

Renames Python's internal `getline()` to `mygetline()` to avoid a duplicate symbol conflict with the POSIX `getline()` added to glibc.

### [3.0](3.0/diff.patch)

Changes the shebang in `Parser/asdl_c.py` from `/usr/bin/env python` to `/usr/bin/python2`. This build script requires Python 2, but on modern systems `python` resolves to Python 3, aborting the AST C-code generation step.

### [3.1](3.1/diff.patch)

Fixes the `asdl_c.py` shebang to use `python2`, removes a stray `% name` format argument that caused a `TypeError` crash during C code generation, and changes `output()` to accept variadic arguments to match the multiple-argument call sites.

### [3.2](3.2/diff.patch)

Fixes Python 2/3 shebang issues in `asdl_c.py`, `typeslots.py`, `makeopcodetargets.py`, and `Makefile.pre.in` so build scripts use `python2` explicitly. Also refactors the garbage collector's self-referential static initializer into a runtime function, fixing a crash under PIE/LTO builds on modern toolchains.

### [3.3](3.3/diff.patch)

Updates `obmalloc.c` to use 16-byte alignment on 64-bit systems instead of the hardcoded 8-byte value. Without this, the small-object allocator can return insufficiently aligned pointers for types that require stricter alignment, causing bus errors or silent data corruption.

## Attribution

- [python-0.9.1](https://github.com/smontanaro/python-0.9.1): Python 0.9.1 source release
- [vintage-python](https://github.com/di/vintage-python):  Base images for vintage Python distributions (used as a reference for this repository) 
- [Legacy Python Source Releases](https://legacy.python.org/download/releases/src/): Source releases for Python 1.x, 2.0 
- [Python Source Releases](https://www.python.org/downloads/source/): Source releases for Python 2.0.1+
