# libsecp256k1-fuzzing-seed-corpus
Fuzzing seed corpus for [libsecp256k1](https://github.com/bitcoin-core/secp256k1).

Usage:

```sh
# check out https://github.com/bitcoin-core/secp256k1/pull/744
$ ./autogen.sh
$ CC=clang CXX=clang++ ./configure --enable-fuzz --with-asm=no --enable-experimental --enable-module-ecdh --enable-module-recovery
$ make
$ git clone https://github.com/practicalswift/libsecp256k1-fuzzing-seed-corpus
$ mkdir -p coverage-increasing-inputs-to-submit-upstream/
$ ./fuzz_public -use_value_profile=1 coverage-increasing-inputs-to-submit-upstream/ libsecp256k1-fuzzing-seed-corpus/seeds/
INFO: Seed: 747237488
INFO: Loaded 2 modules   (717 inline 8-bit counters): 625 [0x7f66c8ed90c0, 0x7f66c8ed9331), 92 [0x6f9120, 0x6f917c),
INFO: Loaded 2 PC tables (717 PCs): 625 [0x7f66c8ed9338,0x7f66c8edba48), 92 [0x4d2bc0,0x4d3180),
INFO:        0 files found in coverage-increasing-inputs-to-submit-upstream/
INFO:     2911 files found in libsecp256k1-fuzzing-seed-corpus/seeds/
INFO: -max_len is not provided; libFuzzer will not generate inputs larger than 8191 bytes
INFO: seed corpus: files: 2911 min: 1b max: 8191b total: 259749b rss: 25Mb
#2048   pulse  cov: 425 ft: 13712 corp: 1712/54Kb exec/s: 682 rss: 26Mb
#2912   INITED cov: 445 ft: 14943 corp: 2533/239Kb exec/s: 582 rss: 27Mb
…
# Please submit any coverage increasing inputs to:
# * https://github.com/practicalswift/libsecp256k1-fuzzing-seed-corpus
```

Happy fuzzing!
