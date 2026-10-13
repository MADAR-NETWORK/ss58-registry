# SS58 Registry — community continuation

> **The original [paritytech/ss58-registry](https://github.com/paritytech/ss58-registry) was archived on 16 April 2026 and no longer accepts new networks.**
> This fork keeps every original entry unchanged and continues accepting requests as a free community service, maintained by [MADAR Network](https://madar-network.com).
>
> - **Search, check a prefix, convert addresses, request a prefix:** https://madar-network.com/ss58/
> - **Current data:** [`community/registry.json`](community/registry.json): `upstream_snapshot` is the date of the inherited data; entries with `"added"` are community additions, all others are inherited unchanged.
> - **Requests:** open an issue here (the page above fills it in). Rules: the first complete request by its public timestamp wins after a 7-day public review; a network already using a prefix on a live chain keeps it; one prefix per network.
>
> A prefix here prevents collisions between networks that use this registry; it does not certify a project. The text below is the original README.

---

# SS58 Registry

[![GitHub license](https://img.shields.io/badge/license-Apache2-green)](#LICENSE) [![GitLab Status](https://gitlab.parity.io/parity/ss58-registry/badges/main/pipeline.svg)](https://gitlab.parity.io/parity/ss58-registry/pipelines)

A list of known [SS58](https://docs.substrate.io/reference/address-formats/) account types as an enum, typically used by the Polkadot, Kusama or Substrate ecosystems.

These are derived from the [json data file](ss58-registry.json) in this repository which contains entries like this:

```js
{
	"prefix": 5,                       // unique u16
	"network": "astar",                // unique no spaces
	"displayName": "Astar Network",    //
	"symbols": ["ASTR"],               // symbol for each instance of the Balances pallet (usually one)
	"decimals": [18],                  // decimals for each symbol listed
	"standardAccount": "*25519",       // Sr25519, Ed25519 or secp256k1
	"website": "https://astar.network" // website or code repository of network
},
```

## Process

1. Fork and clone this repo.

2. Add an additional account type to `ss58-registry.json` (contiguous prefixes are better).

3. Bump the minor (middle) version number of the `Cargo.toml` by running:
```
cargo install cargo-bump && cargo bump minor
```
4. Run git stage, commit, push and then raise a pull request.

5. Once the PR has landed, one of the admins can
[create a new release](https://github.com/paritytech/ss58-registry/releases/new).
This will release the new version to [crates.io](https://crates.io/crates/ss58-registry)

## Licensing

Apache-2.0
