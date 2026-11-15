# Contributing to selkie

Selkie implements Mermaid parsing and rendering in Rust. Contributions should improve documented diagram support, rendering fidelity, diagnostics and the evaluation system that compares results with the reference implementation.

## Before you start

Read [README.md](README.md), [AGENTS.md](AGENTS.md) and [EVAL.md](EVAL.md). Check existing issues and pull requests before starting. For a rendering defect, review the relevant reference implementation and first add or adjust evaluation coverage so that it detects the problem.

For bugs, provide the affected version or commit, environment, minimal reproduction, expected result and observed result. For a substantial proposal, describe the use case and compatibility impact before expanding implementation scope. Use existing issue templates when offered.

## Development and validation

Use the repository's Cargo configuration and optional feature requirements. The established checks in AGENTS.md include:

```sh
cargo fmt
cargo clippy --features all-formats -- -D warnings
cargo test --features all-formats
```

Formatting modifies source; inspect the diff before committing. For a specific diagram family, follow the documented evaluation command `cargo run --features eval --bin selkie -- eval --type <diagram_type>`, substituting the affected family. Record before-and-after evidence and ensure improvements do not introduce regressions elsewhere.

Inspect generated SVGs and update the relevant `docs/images` example when resolving a rendering issue. Add focused tests for parsing, invalid inputs and changed output behaviour. Preserve the distinctions between default features, optional output formats and evaluation tooling. Missing image libraries or reference tooling must be reported as unverified capability, not silently replaced with another backend.

## Pull requests

Create a focused branch from the current `main` branch and submit a pull request to this repository. Link the relevant issue or existing project task, explain the resulting behaviour, and update affected examples and documentation. Keep unrelated changes in separate pull requests.

Report executed commands, outcomes and the commit they validate. Identify unavailable checks and remaining limitations explicitly. Follow the repository's existing review and automated-check requirements; retain required gates and current ownership. Address findings and verify the final head before integration. Repository changes do not themselves authorise a release or external operational action.

## Security, rights and conduct

Follow the [security policy](https://github.com/edithatogo/.github/blob/main/SECURITY.md). Use private vulnerability reporting if available; otherwise request a private contact without publishing vulnerability details. Keep credentials, personal information and restricted source material out of issues, fixtures, logs and artifacts.

Read the [existing licence](LICENSE) and preserve attribution and third-party terms. Follow the [code of conduct](https://github.com/edithatogo/.github/blob/main/CODE_OF_CONDUCT.md) and keep technical discussions respectful.

## Basis for this guide

This guide follows [GitHub's contribution-guideline guidance](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/setting-guidelines-for-repository-contributors) and the contribution-process and testing principles in [OpenSSF Best Practices](https://www.bestpractices.dev/en/criteria). It does not assert certification.
