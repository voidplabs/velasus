<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)"
            srcset="data/logo/velasus_banner.jpg">
    <img src="data/logo/velasus_banner.jpg" height="72" alt="Velasus">
  </picture>
</p>

<h1 align="center">Velasus</h1>

<p align="center">
  Cloud-native proxy server & load balancer in Rust that prioritizes correctness, then performance, then features.
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-Apache%202.0-blue.svg" alt="License: Apache 2.0"></a>
  <a href="https://github.com/voidplabs/velasus"><img src="https://img.shields.io/badge/version-0.1.0-7c3aed" alt="Version 0.1.0"></a>
  <img src="https://img.shields.io/badge/status-research%20%26%20design-blue" alt="Status: research & design">
  <img src="https://img.shields.io/badge/language-Rust-f74c00?logo=rust&logoColor=white" alt="Rust">
  <img src="https://img.shields.io/badge/platform-Linux%20%7C%20macOS-lightgrey" alt="Platform">
</p>

<p align="center">
  <a href="docs/STATE.md">Project State</a>
  ·
  <a href="docs/adr/README.md">Architecture Decisions (ADR)</a>
  ·
  <a href="CONTRIBUTING.md">Contributing</a>
  ·
  <a href="LICENSE">License</a>
</p>

---

## Overview

Velasus is a cloud-native (Docker, Kubernetes) reverse proxy and load balancer written in Rust.

The project is guided by a strict hierarchy of values:

1. **Correctness first**: Protocol invariants and boundary conditions are rigorously modeled. No approximations, undefined behavior, or silent bugs.
2. **Performance second**: Zero-copy I/O, lean async task concurrency, and predictable memory bounds.
3. **Features third**: New capabilities (dynamic routing, TLS, discovery, observability) are added only on top of solid foundations.

The initial focus is deep research into modern systems networking, examining state-of-the-art implementations ([hyper](https://github.com/hyperium/hyper), [tower](https://github.com/tower-rs/tower), [linkerd2-proxy](https://github.com/linkerd/linkerd2-proxy)), and formalizing architectural decisions through [ADRs](./docs/adr/README.md) before locking down code.

---

## Build & Run

### Prerequisites

- [Rust](https://www.rust-lang.org/) (latest stable toolchain with `cargo`)

### Building

```bash
cargo check
cargo build --release
```

### Running Tests

```bash
cargo test
```

---

## Recommended Reading

Curated foundational texts and references studying the mechanics of networking, operating systems, and production proxies:

### Systems & Operating System Internals

- **TCP/IP Illustrated, Volume 1: The Protocols (2nd Edition)** - Kevin R. Fall, W. Richard Stevens _(The definitive guide on socket states, packet lifecycles, half-close, and congestion)._
- **The Linux Programming Interface (TLPI)** - Michael Kerrisk _(Specifically Chapters 56–61: non-blocking sockets, event polling models, and network IPC)._
- **Systems Performance: Enterprise and the Cloud (2nd Edition)** - Brendan Gregg _(Profiling I/O latency, epoll efficiency, and kernel tracing)._

### Protocol Specifications

- **[RFC 9110](https://www.rfc-editor.org/rfc/rfc9110.html)** - HTTP Semantics
- **[RFC 9112](https://www.rfc-editor.org/rfc/rfc9112.html)** - HTTP/1.1 (Syntax, Framing & Connection Management)
- **[RFC 9113](https://www.rfc-editor.org/rfc/rfc9113.html)** - HTTP/2
- **[RFC 9000](https://www.rfc-editor.org/rfc/rfc9000.html) / [RFC 9114](https://www.rfc-editor.org/rfc/rfc9114.html)** - QUIC & HTTP/3

### Reference Implementations & Architecture

- **[Linkerd2-proxy](https://github.com/linkerd/linkerd2-proxy)** - Production-grade Rust network proxy design, async task lifecycles, and cancellation patterns.
- **[Hyper](https://github.com/hyperium/hyper) & [H2](https://github.com/hyperium/h2)** - Low-level HTTP state machine implementations and framing guards in Rust.
- **[Tower](https://github.com/tower-rs/tower)** - Robust client/server middleware abstraction model.

---

## License

This project is licensed under the [Apache License 2.0](./LICENSE).
