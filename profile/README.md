<h1 align="center">Calimero</h1>

<p align="center">
  <i>
    A confidential cloud for collaborative apps.<br/>
    Your app runs on attested TEE nodes. Nobody operating them can read its data, including us.
  </i>
</p>

<p align="center">
  <a href="https://calimero.network" target="_blank"><img src="https://img.shields.io/badge/Website-calimero.network-black?style=flat-square" /></a>
  <a href="https://cloud.calimero.network" target="_blank"><img src="https://img.shields.io/badge/Cloud-cloud.calimero.network-black?style=flat-square" /></a>
  <a href="https://calimero-network.github.io/core/" target="_blank"><img src="https://img.shields.io/badge/Docs-calimero--network.github.io%2Fcore-black?style=flat-square" /></a>
  <a href="https://apps.calimero.network" target="_blank"><img src="https://img.shields.io/badge/Apps-apps.calimero.network-black?style=flat-square" /></a>
  <a href="https://discord.gg/urJeMtRRMu" target="_blank"><img src="https://img.shields.io/badge/Discord-Dev_Support-5865F2?style=flat-square&logo=discord&logoColor=white" /></a>
  <a href="https://x.com/CalimeroNetwork" target="_blank"><img src="https://img.shields.io/badge/Twitter-@CalimeroNetwork-black?style=flat-square&logo=x&logoColor=white" /></a>
</p>

---

## What it is

You write an app in Rust or JavaScript, compiled to WASM, and publish it as a
signed package. Calimero runs each app instance on a small cluster of Intel TDX
nodes, replicated by its own Raft log.

- **Clients check the node before they talk to it.** A client reaches a node over
  a sealed channel, which it opens only after verifying the node's hardware
  attestation. People sign in with passkeys.
- **Nobody can quietly swap the code.** New code or a new node image reaches an
  app's data only after the app's approver says so, on a page the node serves
  itself. Every such decision is attested.

Practically: shared documents, chat, issue trackers, spreadsheets, internal
tools. Collaborative SaaS, without a vendor who can read the plaintext.

## Get started

| I want to… | Go to |
| --- | --- |
| Deploy an app without running anything | [Calimero Cloud](https://cloud.calimero.network) |
| Understand how it works | [Cloud overview](https://calimero-network.github.io/core/cloud/overview/) · [Protocol reference](https://calimero-network.github.io/core/protocol/overview/) |
| Write an app | [Build](https://calimero-network.github.io/core/build/): the Rust SDK and `cargo mero`, in [core](https://github.com/calimero-network/core) |
| Call an app from a frontend or a script | [mero-js](https://github.com/calimero-network/mero-js) · [mero-react](https://github.com/calimero-network/mero-react) · [calimero-client-py](https://github.com/calimero-network/calimero-client-py) |
| Run a cluster yourself | [Operate](https://calimero-network.github.io/core/operate/) |
| See real apps | [apps](https://github.com/calimero-network/apps) |
| Coming from the peer-to-peer release | [Coming from v1](https://calimero-network.github.io/core/cloud/coming-from-v1/) |

Try it locally from a checkout of [core](https://github.com/calimero-network/core):

```bash
cargo run -p merod -- local                  # a 3-node development cluster on 127.0.0.1:2501-2503
cargo install --path crates/meroctl
meroctl node add local http://127.0.0.1:2501/ --allow-mock
meroctl login --dev-passkey ./dev-passkey.json --name ada
```

---

## Platform

| Repo | Description |
| --- | --- |
| [core](https://github.com/calimero-network/core) | The node (`merod`), the CLI (`meroctl`), the Rust SDK, `cargo mero`, and the docs. The heart of the stack. |
| [mero-tee](https://github.com/calimero-network/mero-tee) | TDX node images, mero-kms, signed releases, and the public [attestation verifier](https://github.com/calimero-network/mero-tee/tree/master/attestation-verifier). |
| [app-registry](https://github.com/calimero-network/app-registry) | Where apps are published and installed from. Ed25519-signed manifests; published versions are immutable. Live at [apps.calimero.network](https://apps.calimero.network). |

## Building apps

| Repo | Language | Description |
| --- | --- | --- |
| [core/crates/sdk](https://github.com/calimero-network/core/tree/master/crates/sdk) | Rust | The app SDK: macros, CRDT collections, events. |
| [calimero-sdk-js](https://github.com/calimero-network/calimero-sdk-js) | TypeScript | Write app logic in TypeScript, compiled to WASM. |
| [mero-mcp](https://github.com/calimero-network/mero-mcp) | — | MCP server: exposes a cluster and every app method as tools for AI agents. |
| [calimero-skills](https://github.com/calimero-network/calimero-skills) | — | Agent skills for building on Calimero. |

## Connecting to a cluster

| Repo | Language | Description |
| --- | --- | --- |
| [mero-js](https://github.com/calimero-network/mero-js) | TypeScript | Attestation check, sealed channel, passkey sign-in, calls, events, approvals. Browser, Node and edge. |
| [mero-react](https://github.com/calimero-network/mero-react) | TypeScript | React hooks and provider over `mero-js`. |
| [calimero-client-py](https://github.com/calimero-network/calimero-client-py) | Python | Python client for automation and scripting. |
| [swift-sdk](https://github.com/calimero-network/swift-sdk) | Swift | iOS and macOS. |
| [kotlin-sdk](https://github.com/calimero-network/kotlin-sdk) | Kotlin | Android. |

## Apps

| Repo | Description |
| --- | --- |
| [apps](https://github.com/calimero-network/apps) | Every Calimero app in one monorepo: design tools, spreadsheets, chat, calls, document signing, games, and more. Shared toolchain, one CI, one release path to the registry. |
| [workshop-apps](https://github.com/calimero-network/workshop-apps) | Apps built live at workshops, one per branch. |

## Tools & design

| Repo | Description |
| --- | --- |
| [homebrew-tap](https://github.com/calimero-network/homebrew-tap) | macOS install for `meroctl`, `cargo-mero` and `mero-abi`. |
| [install-sh](https://github.com/calimero-network/install-sh) | Install scripts for Calimero binaries. |

> Reference documentation for `core` is built from the repo and published at
> [calimero-network.github.io/core](https://calimero-network.github.io/core/),
> in five tracks: **Cloud**, **Build**, **Operate**, **Protocol Reference** and **Contribute**.

## Contributing

Issues and PRs are welcome across every repo. Questions and developer support:
[Discord](https://discord.gg/urJeMtRRMu).

Licensed MIT OR Apache-2.0.
