[![Crate](https://img.shields.io/crates/v/sevenz-rust.svg)](https://crates.io/crates/sevenz-rust)
 [![Documentation](https://docs.rs/sevenz-rust/badge.svg)](https://docs.rs/sevenz-rust)
 
This project is a 7z compressor/decompressor written in pure rust.<br/>
And it's very much inspired by the [apache commons-compress](https://commons.apache.org/proper/commons-compress/) project.<br/>

The LZMA/LZMA2 decoder and all filters code was ported from [tukaani xz for java](https://tukaani.org/xz/java.html)

## Decompression

Supported codecs:
 - [x] COPY
 - [x] LZMA
 - [x] LZMA2


Supported filters:
 - [x] BCJ X86
 - [x] BCJ PPC
 - [x] BCJ IA64
 - [x] BCJ ARM
 - [x] BCJ ARM_THUMB
 - [x] BCJ SPARC
 - [x] DELTA




### Usage

```
[dependencies]
sevenz-rust={version="0.1.5"}
```

Decompress source file "data/sample.7z" to dest path "data/sample"
```rust
sevenz_rust::decompress_file("data/sample.7z", "data/sample").expect("complete");
```

Decompress a encrypted 7z file

Add 'aes256' feature
```
[dependencies]
sevenz-rust={version="0.1.5", features=["aes256"]}
```

```rust
sevenz_rust::decompress_file_with_password("path/to/encrypted.7z", "path/to/output", "password".into()).expect("complete");
```

## Compression
Currently only support LZMA2 method.

```
[dependencies]
sevenz-rust={version="0.2", features=["compress"]}
```

Use the helper function to create a 7z file with source path.
```rust
sevenz_rust::compress_to_path("examples/data/sample", "examples/data/sample.7z").expect("compress ok");
```
