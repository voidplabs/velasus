# Contributing to Velasus

## Philosophy

Velasus is built for correctness first, performance second, features third.
Every component is grounded in official specifications - RFC 9110, RFC 9112,
RFC 7540, and their successors. If the RFC defines a state machine, the code
implements that state machine. No shortcuts, no approximations.

## On AI-generated code

You may use AI tools for research, to understand a spec, to get feedback on
your approach, or to find relevant RFCs. You may not use AI to write logic,
tests, or any part of the implementation - including "just a small change."

Every line of code in this repository must be understood and owned by the
person who committed it. If you cannot explain why a line exists and what
invariant it enforces, it does not belong here.

## Getting started

```bash
git clone https://github.com/voidplabs/velasus
cd velasus
cargo build
cargo test
```

## Workflow

- Open an issue before a PR for anything non-trivial
- One concern per PR
- Tests required for new behavior
- No `unsafe` unless accompanied by a comment citing the invariant it relies on
  and why safe alternatives were insufficient

## Code standards

- `cargo fmt` before every commit
- `cargo clippy -- -D warnings` must pass clean
- Public items require doc comments
- State machines are encoded as enums with exhaustive match - no boolean flags
  standing in for state

## Commit messages

```
feat: add HTTP/1.1 keep-alive connection state machine
fix: correct CRLF handling in header field parser
perf: eliminate allocation in request line parser
test: add RFC 9112 §3 request-line edge cases
```

## Current focus

See the roadmap in README.md. Contributions outside the current phase will
be noted and deferred - not because they are unwelcome, but because layered
correctness matters more than feature breadth.
