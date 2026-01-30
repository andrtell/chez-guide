[Up]() [Next]() [Prev]()

----

__Tools__


```sh
sudo apt update

# ld, gprof, readelf, objdump, etc ...
sudo apt install binutils

# gcc, libc6-dev, make, dpkg-dev, g++
sudo apt install build-essential

# adds detailed man pages for the C library functions (man 3 printf, man 3 malloc, etc ...)
sudo apt install manpages-dev

# Excellent debugger + pretty-printer support
sudo apt install gdb

# Better formatting & static analysis
sudo apt install clang-format clang-tidy

# Popular build system (almost every modern C project uses it)
sudo apt install cmake

# Fast alternative to make (used by many cmake projects)
sudo apt install ninja-build

# valgrind + very useful helpers
sudo apt install valgrind linux-tools-common linux-tools-generic

# git (you'll need it for almost every real project)
sudo apt install git

# documentation system for C/C++ and others
sudo apt install doxygen
```

_all in one_

```sh
sudo apt update

sudo apt install \
  binutils \
  build-essential \
  manpages-dev \
  gdb \
  clang-format \
  clang-tidy \
  cmake \
  ninja-build \
  valgrind \
  linux-tools-common \
  linux-tools-generic \
  git \
  doxygen
```

__Libraries__

```sh
# libcurl: Library for making HTTP/HTTPS/FTP requests.
sudo apt install libcurl4-openssl-dev

# GLib: Core low-level utility library (data structures, strings, file handling, events, main loops)
sudo apt install libglib2.0-dev

# GSL: GNU Scientific Library – wide collection of numerical routines (special functions, linear algebra, statistics, root-finding, FFT, etc.)
sudo apt install libgsl-dev

# SQLite: Lightweight, serverless, embedded SQL database engine.
sudo apt install libsqlite3-dev

# libxml2: Fast and feature-rich XML parsing, validation and manipulation library .
sudo apt install libxml2-dev

# ncurses: Library for creating text-based user interfaces in terminal.
sudo apt install libncurses-dev
```

_all in one_

```sh
sudo apt update

sudo apt install \
    libcurl4-openssl-dev \
    libglib2.0-dev      \
    libgsl-dev          \
    libsqlite3-dev      \
    libxml2-dev         \
    libncurses-dev
```
