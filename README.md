# libavl implementation from illumos

This repo is a standalone copy of the libavl library found on illumos systems.
libavl is a library for working with AVL trees.

The original (and canonical) source for this implementation is at:

    https://github.com/illumos/illumos-gate/tree/master/usr/src/lib/libavl

libavl is largely baked, and is not expected to undergo much change.  However,
the copy in this repository should be considered strictly downstream of the one
in illumos.  **There should be no local changes here.**


## Why does this repository exist?

In [recent illumos
versions](https://github.com/illumos/illumos-gate/commit/fa9922c2be34868be01989cef133828185b5c0bc),
libavl is a public interface, meaning you can use it when building software.
However, software using that interface will not work on illumos versions prior
to that change.  The copy in this repository exists for software that wants to
use libavl without worrying about platform version dependencies.  For this use
case, it may make sense for consumers to statically link against this library.


## How to use this repository

It's not common to need to use this repository.  In case you decide that
statically linking libavl is appropriate for your program, this repository
includes Makefiles intended for easy incorporation into other repositories, as
via "git submodule".  The easiest way to use this is run:

    $ git submodule add https://github.com/joyent/illumos-libavl deps/illumos-libavl

You can build the submodule by changing directories to it and typing "make".
The default target builds a static library for libavl.  It's fully supported to
customize two pieces of the build:

* `CFLAGS`: customize this to configure a 32-bit or 64-bit build
* `BUILD_DIR`: the directory in which to build object files and the static
  library file

You can customize these by setting these environment variables and invoking
`make -e`.

There's a full example of this in the [mdb_v8
project](https://github.com/joyent/mdb_v8).
