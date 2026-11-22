# Contract Examples

This folder contains focused Soroban contract examples that demonstrate implementation patterns for gas, oracle integration, and state archival. The examples are reference code for the corresponding architecture and performance guides rather than a single deployable application.

## Directory overview

- [`optimized-sample/`](optimized-sample/) - Compares storage layouts and loop implementations to demonstrate WASM gas and storage optimization techniques.
- [`oracle-client/`](oracle-client/) - Provides Rust and TypeScript clients for the Stellar-K8s gas fee oracle contract.
- [`ttl-extension/`](ttl-extension/) - Demonstrates the In-Contract Extension strategy for extending instance and persistent storage TTLs.

## `optimized-sample/`

- [`Cargo.toml`](optimized-sample/Cargo.toml) - Defines the standalone Rust package, Soroban SDK dependency, and optimized release build profiles.
- [`Cargo.lock`](optimized-sample/Cargo.lock) - Pins dependency versions for reproducible builds of the sample.
- [`src/`](optimized-sample/src/) - Contains the sample contract source.
- [`src/lib.rs`](optimized-sample/src/lib.rs) - Implements compact and monolithic storage paths, bounded iterative arithmetic, metadata reads, and unit tests for the gas-tuning example.

## `oracle-client/`

- [`.gitignore`](oracle-client/.gitignore) - Excludes Rust build artifacts and snapshots plus TypeScript dependencies, build output, and package metadata.
- [`README.md`](oracle-client/README.md) - Documents how to run and use the Rust and TypeScript oracle client examples.
- [`rust/`](oracle-client/rust/) - Contains the Rust client crate and its tests.
- [`rust/Cargo.toml`](oracle-client/rust/Cargo.toml) - Defines the `no_std` Rust client package and Soroban SDK dependencies.
- [`rust/src/`](oracle-client/rust/src/) - Contains the Rust client and reference arithmetic modules.
- [`rust/src/lib.rs`](oracle-client/rust/src/lib.rs) - Defines the oracle ABI types, generated-style `GasOracleClient`, contract errors, and `quote_fee` helper.
- [`rust/src/ema.rs`](oracle-client/rust/src/ema.rs) - Implements and tests the fixed-point exponential moving average specified for the oracle.
- [`rust/tests/`](oracle-client/rust/tests/) - Contains integration-style Soroban host tests.
- [`rust/tests/client.rs`](oracle-client/rust/tests/client.rs) - Exercises the Rust client against a mock oracle implementation and verifies fees, errors, authorization, configuration, and overflow behavior.
- [`typescript/`](oracle-client/typescript/) - Contains the TypeScript client, runnable example, and tests.
- [`typescript/package.json`](oracle-client/typescript/package.json) - Defines Node dependencies and scripts for building, testing, and running the TypeScript example.
- [`typescript/tsconfig.json`](oracle-client/typescript/tsconfig.json) - Configures strict NodeNext TypeScript compilation into `dist/`.
- [`typescript/src/`](oracle-client/typescript/src/) - Contains the TypeScript implementation and tests.
- [`typescript/src/client.ts`](oracle-client/typescript/src/client.ts) - Implements read-only Soroban RPC calls for oracle fees, estimates, state, configuration, and contract errors.
- [`typescript/src/example.ts`](oracle-client/typescript/src/example.ts) - Prints the oracle state and fee quotes, with a fallback for stale or missing data.
- [`typescript/src/client.test.ts`](oracle-client/typescript/src/client.test.ts) - Tests simulation error-code parsing and oracle error exception messages.

## `ttl-extension/`

- [`src/`](ttl-extension/src/) - Contains the TTL extension contract source.
- [`src/lib.rs`](ttl-extension/src/lib.rs) - Demonstrates instance and persistent entry TTL renewal in a token-style contract, while leaving temporary nonce storage unextended.
