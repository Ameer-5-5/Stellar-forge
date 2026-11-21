# Smart Contract Examples

This folder contains standalone Soroban contract examples that demonstrate storage, fee-oracle integration, and contract state-lifetime patterns for Stellar-K8s.

| Folder | Purpose |
| --- | --- |
| [`optimized-sample/`](optimized-sample/) | Demonstrates gas and storage optimizations, comparing counter sharding and compact key usage with an unoptimized monolithic state pattern and bounded iterative logic. |
| [`oracle-client/`](oracle-client/) | Provides Rust and TypeScript clients for querying the gas fee oracle contract, including a fixed-point EMA reference and mock-oracle integration tests. |
| [`ttl-extension/`](ttl-extension/) | Demonstrates the in-contract TTL-extension strategy for keeping instance and persistent token-state entries live on each public call. |
