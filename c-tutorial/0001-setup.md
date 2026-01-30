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
sudo apt install binutils build-essential manpages-dev \
                 gdb clang-format clang-tidy \
                 cmake ninja-build \
                 valgrind linux-tools-common linux-tools-generic \
                 git \
                 doxygen
```

Useful libraries

```
$ apt install libcurl4-openssl-dev libglib2.0-dev libgsl-dev \
              libsqlite3-dev libxml2-dev libcurses-dev
```
