# rust-lib{core, collections, alloc, rustc_unicode}

This crate provides `libcore`, `liballoc`, `libcollections`, and
`librustc_unicode` from the Rust source tree as Cargo packages. `libcore` has no
dependencies; the rest depend on this version of libcore.

## Versioning

Before compiling, each package runs `rustc --version` to determine the version
of `rustc` that your project is using. It then downloads the corresponding
source code. This means that the appropriate version of each library is used.

## Usage

Simply add the dependencies you need to your `Cargo.toml`:

    [dependencies]
    rust-libcore = { git = "https://github.com/SergioBenitez/rust-libcore" }
    rust-liballoc = { git = "https://github.com/SergioBenitez/rust-libcore" }
    rust-libcollections = { git = "https://github.com/SergioBenitez/rust-libcore" }
    rust-librustc_unicode = { git = "https://github.com/SergioBenitez/rust-libcore" }

Ensure that all of your libraries are using `rust-libcore` as the `core`
library. Otherwise, you may find yourself with a slew of duplicate `lang_item`
definitions. Note: it's unlikely that you need to depend on
`rust-librustc_unicode` directly. If you're using `rust-libcollections`, the
crate will pull in `librustc_unicode` automatically.
