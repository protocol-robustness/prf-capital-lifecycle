# PRF Capital Lifecycle

Standalone repository for the pure Protected Capital lifecycle transition kernel.

This repository packages the Clojure and Rust implementations, shared transition
vectors, and the reviewed interface specification. It does not perform canonical
hashing, derive allocation or source artifacts, verify proofs, move tokens, or
change the existing NOW-tranche behavior. EVM implementations and adapters remain
in `prf-evm`.

The `0.1.0` crate version is the initial package version, not a claim that the
interface is production-stable. The current PRF integration copy remains in-tree
while consumers transition to an immutable repository revision. Do not use local
path dependencies or copy the authoritative vectors into consumers.

## Layout

- `docs/capital-lifecycle-interface-v1.md`: semantic boundary, interface, and
  extraction invariants.
- `clj/`: Clojure transition implementation and tests.
- `rust/`: Rust transition crate and tests.
- `test-vectors/`: shared accepted/rejected transition cases.

## Validate

From `clj/`:

```sh
clojure -M:test -e "(require 'prf.capital-lifecycle.transition-test)(clojure.test/run-tests 'prf.capital-lifecycle.transition-test)"
```

From `rust/`:

```sh
cargo test --locked
cargo clippy --locked -- -D warnings
```
