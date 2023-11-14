# Hacken's Rust Crate Audits

Hacken uses [cargo-vet](https://mozilla.github.io/cargo-vet/) to ensure
third-party Rust dependencies have been audited by Hacken or another trusted
entity.

This repository automatically
[aggregates](https://mozilla.github.io/cargo-vet/multiple-repositories.html)
audits from various repositories to make them easily reusable by
others.

## Usage

Install and initialize cargo-vet:

```
cargo install cargo-vet
cargo vet init
```

To import Hacken's audit list into another cargo-vet instance (inside the `supply-chain` directory), add the following
lines to your `config.toml`:

```
[imports.hacken]
url = "https://raw.githubusercontent.com/hknio/rust-supply-chain/main/audits.toml"
```

## Contributing

Sources can be effortlessly added to the `sources.list`, triggering automatic updates to `audits.toml`. For manual control, use the `manual-sources.toml` file. Add audits in the following format:

```toml
[[audits.rand_chacha]]
who = "Noah Jelich <n.jelich@hacken.io>"
criteria = ["safe-to-deploy", "crypto-safe"]
version = "0.3.1"
notes = "Hasn't been updated in 2 years."
```

Refer to [manual-sources.toml](manual-sources.toml) and [sources.list](sources.list).

## Audit Standards

Contributors seeking criteria for auditing can refer to the table for guidance. Detailed criteria can be found in the [AUDIT_STANDARDS.md](AUDIT_STANDARDS.md) document.

| **Criteria**                          | **Requires**                                      |
|---------------------------------------|---------------------------------------------------|
| [`crypto-safe`]                       | **Cryptography expertise** and **Rust expertise** |
| [`does-not-implement-crypto`]         | **Generalist SWE**                                |
| [`safe-to-run`]                       | **Generalist SWE**                                |
| [`safe-to-deploy`]                    | **Generalist SWE**                                |
| [`contains-unsafe`]                   | **Rust expertise**                                |

