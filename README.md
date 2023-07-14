# Novika

This is a nightly build of Novika. Novika was never truly stable, so nightlies aren't
much different from the released version(s) in this sense.

## Dependencies

Novika requires the following libraries to be installed on your system.

### Linux

* `libgc`
* `libevent`
* `libffi`
* `libgmp`
* `libpcre2`

Most of these are probably already included in your distribution.

### Windows

Everything should work as-is.

## Installation

You can execute Novika CLI binary `bin/novika` and image assembler `bin/nkas`
*while you're inside this directory*, but I'd recommend to install Novika system-wide
for better UX.

As for NKI, you can run it from anywhere; it does not depend on the Novika environment
set up on your system.

1. Move the folder this README is in anywhere you want. In this section, let's assume you've
   moved it to `~/app/novika` (substitute for your own directory below). When a Novika update
   arrives, you'd just replace the contents of `~/app/novika` with those of the newer
   version's folder.

2. Next, you'll need to add `~/app/novika/bin/` to `$PATH`. This step is entirely optional,
   but running `novika repl` is certainly nicer than `~/app/novika/bin/novika repl`.

3. Create a soft link called `.novika` in your home directory. The link should point to the
   `~/app/novika/env` directory. This is done so Novika can locate its standard library and
   tools (e.g. `repl`) regardless of your current working directory.

The steps on Windows are similar, except that you'd need to do some clicking to get to `$PATH`, and use `C:\Users\...\` instead of `~`.

## Usage

### Novika CLI

Novika CLI is the generic frontend. It is used to prototype and explore the language. Type
`novika help` for more information on this frontend.

```text
$ novika console examples/snake.nk
[runs snake]

$ novika repl
[launches the repl]

$ mkdir my-awesome-novika-project
$ cd my-awesome-novika-project
$ novika new
[creates the project]
$ novika
Hello World
```

### NKAS

Novika image assembler is used to pack and compress Novika source code. Novika images could
be distributed together with NKI (perhaps in a self-extracting archive) to run them on systems
without a (proper) Novika environment.

NKAS has roughly the same interface as Novika CLI, particularly in that it is aware of
the Novika environment and allows you to drop things Novika can find on her own.

```text
$ nkas -cb:b repl repl.nki
[packs and compresses Novika REPL, saves to repl.nki]

$ nki repl.nki
[unpacks and launches Novika REPL]
```

### NKI

Novika image interpreter is independent of the (developer's) Novika environment, and could be
used to run Novika images on user systems, where Novika standard library and/or program
dependencies are not preinstalled.

```text
$ nki path/to/image.nki
[unpacks and launches image.nki]
```

## Credits

Novika is powered by:

* [Crystal](https://crystal-lang.org)
* [bindata](https://github.com/spider-gazelle/bindata)
* [brotli.cr](https://github.com/naqvis/brotli.cr)
* [brotli](https://github.com/google/brotli)
* [termbox2](https://github.com/termbox/termbox2)
* [libffi](https://github.com/libffi/libffi)
* [upx](https://github.com/upx/upx)
* [reply](https://github.com/I3oris/reply)
* [tablo](https://github.com/hutou/tablo)
