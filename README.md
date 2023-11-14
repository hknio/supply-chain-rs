# Hacken's Rust Crate Audits

Hacken uses [cargo-vet](https://mozilla.github.io/cargo-vet/) to ensure
third-party Rust dependencies have been audited by Hacken or another trusted
entity.

This repository automatically
[aggregates](https://mozilla.github.io/cargo-vet/multiple-repositories.html)
audits from various repositories to make them easily reusable by
others.

## Usage

To import Hacken's audit list into another cargo-vet instance, add the following
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

