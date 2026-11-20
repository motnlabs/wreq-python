# RUNNING_LOG — wreq-python

## 2026-11-15 — Chrome157 exposed in the Python wheel

- Exposed `Chrome157` in `src/emulate.rs` and `python/wreq/emulation.py`
  (also filled in the missing `Chrome155` stub entries).
- Built `wreq-0.13.0-cp311-abi3-win_amd64.whl` against the local `wreq-util`
  and `btls` path patches. Verified `Emulation.Chrome157` and
  `Profile.Chrome157` import, and the wire headers/UA match Chrome 157.
- Build prerequisites: pip `cmake` + `libclang`, and
  `LIBCLANG_PATH=<buildvenv>\Lib\site-packages\clang\native`. BoringSSL is
  rebuilt by btls-sys, so the first build is ~10 min; incremental ~4 min.
- The working tree still carries pre-existing local changes in `Cargo.toml`,
  `Cargo.lock`, `src/tls.rs`, `python/wreq/tls.py`, and untracked `vendor/`
  from the local btls build; the Chrome157 edits are separate.
