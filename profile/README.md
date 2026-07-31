<h1 align="center">Calimero Network</h1>

<p align="center">
  <i>
    Self-hosted, peer-to-peer applications where the operator can't read your data.<br/>
    CRDT state sync, local-first governance, WASM execution.
  </i>
</p>

<p align="center">
  <a href="https://calimero.network" target="_blank"><img src="https://img.shields.io/badge/Website-calimero.network-black?style=flat-square" /></a>
  <a href="https://docs.calimero.network" target="_blank"><img src="https://img.shields.io/badge/Docs-docs.calimero.network-black?style=flat-square" /></a>
  <a href="https://apps.calimero.network" target="_blank"><img src="https://img.shields.io/badge/Apps-apps.calimero.network-black?style=flat-square" /></a>
  <a href="https://discord.gg/urJeMtRRMu" target="_blank"><img src="https://img.shields.io/badge/Discord-Dev_Support-5865F2?style=flat-square&logo=discord&logoColor=white" /></a>
  <a href="https://x.com/CalimeroNetwork" target="_blank"><img src="https://img.shields.io/badge/Twitter-@CalimeroNetwork-black?style=flat-square&logo=x&logoColor=white" /></a>
</p>

---

## What it is

A Calimero app runs on nodes its users control. State is a CRDT set replicated
peer-to-peer over libp2p, encrypted so that whoever operates the infrastructure
sees metadata and nothing else. Application logic is WASM; membership and
permissions are governed by a causal operation log rather than a server.

Practically: shared drives, chat, issue trackers, spreadsheets, design tools —
the collaborative SaaS shape, without the vendor holding the plaintext.

## Quickstart

```bash
brew install calimero-network/tap/merod calimero-network/tap/meroctl
cargo install --git https://github.com/calimero-network/cargo-mero cargo-mero

cargo mero new my-app     # scaffold
cargo mero guide          # the whole path, start to installable bundle
```

Prefer a GUI? [Calimero Desktop](https://calimero.network/download) runs a node,
manages contexts, and installs apps from the registry.

## Start here

| I want to… | Go to |
| --- | --- |
| Understand the model | [Concepts](https://docs.calimero.network) — contexts, identity, CRDT state, privacy |
| Write an app in Rust | [cargo-mero](https://github.com/calimero-network/cargo-mero) + [SDK](https://github.com/calimero-network/core/tree/master/crates/sdk) |
| Write an app in TypeScript | [calimero-sdk-js](https://github.com/calimero-network/calimero-sdk-js) |
| Call a node from my frontend | [mero-js](https://github.com/calimero-network/mero-js) · [mero-react](https://github.com/calimero-network/mero-react) |
| Run nodes locally / in CI | [merobox](https://github.com/calimero-network/merobox) |
| Operate a node | [Operate docs](https://calimero-network.github.io/core/operate/) |
| Read the protocol spec | [Protocol Reference](https://calimero-network.github.io/core/protocol/overview/) |
| Propose a protocol change | [proposals](https://github.com/calimero-network/proposals) (CIPs) |
| See it working | [Example apps](#example-applications) |

---

## Platform

| Repo | Description |
| --- | --- |
| [core](https://github.com/calimero-network/core) | Node runtime (`merod`), operator CLI (`meroctl`), Rust SDK, CRDT storage engine, libp2p networking, WASM execution. The heart of the stack. |
| [app-registry](https://github.com/calimero-network/app-registry) | Registry for signed app bundles (JCS + Ed25519, SemVer-immutable, WASM by IPFS CID). Live at [apps.calimero.network](https://apps.calimero.network). |
| [mero-tee](https://github.com/calimero-network/mero-tee) | TEE infrastructure — KMS, locked images, attestation. |
| [boot-node](https://github.com/calimero-network/boot-node) | Bootstrap/relay node deployment. |

## Building apps

| Repo | Language | Description |
| --- | --- | --- |
| [cargo-mero](https://github.com/calimero-network/cargo-mero) | Rust | `cargo mero` — scaffold, build to WASM with embedded ABI, node-free tests, signed `.mpk` bundles. Start here. |
| [core/crates/sdk](https://github.com/calimero-network/core/tree/master/crates/sdk) | Rust | Application SDK — proc macros, CRDT collections, events, state helpers. |
| [calimero-sdk-js](https://github.com/calimero-network/calimero-sdk-js) | TypeScript | Write app logic in TS/JS, compiled to WASM via QuickJS. |
| [mero-devtools-js](https://github.com/calimero-network/mero-devtools-js) | TypeScript | ABI parser and typed-client codegen from Rust app ABIs. |
| [mero-mcp](https://github.com/calimero-network/mero-mcp) | — | MCP server — exposes node admin and every app ABI method as tools for AI agents. |
| [calimero-skills](https://github.com/calimero-network/calimero-skills) | — | Agent skills for Calimero development (SDK, clients, registry, CLI). |

## Connecting to nodes

| Repo | Language | Description |
| --- | --- | --- |
| [mero-js](https://github.com/calimero-network/mero-js) | TypeScript | Auth, admin API, JSON-RPC, live event streams. Browser, Node, edge; zero dependencies. |
| [mero-react](https://github.com/calimero-network/mero-react) | TypeScript | React hooks and provider over `mero-js`. |
| [calimero-client-py](https://github.com/calimero-network/calimero-client-py) | Python | Python client — automation and scripting. |
| [swift-sdk](https://github.com/calimero-network/swift-sdk) | Swift | MeroKit — iOS/macOS, incl. SSO and token refresh. |
| [kotlin-sdk](https://github.com/calimero-network/kotlin-sdk) | Kotlin | Android — auth, JSON-RPC, Compose login UI. |

## Running & operating

| Repo | Description |
| --- | --- |
| [merobox](https://github.com/calimero-network/merobox) | Docker-based local multi-node networks with declarative workflow files. The standard way to test and run e2e in CI. |
| [tauri-app](https://github.com/calimero-network/tauri-app) | Calimero Desktop — cross-platform node, context, and app manager. [Download](https://calimero.network/download). |
| [admin-dashboard](https://github.com/calimero-network/admin-dashboard) | Web UI for node administration — contexts, members, apps, metrics. |
| [auth-frontend](https://github.com/calimero-network/auth-frontend) | Login, context selection, and permission-grant UI for apps. |
| [homebrew-tap](https://github.com/calimero-network/homebrew-tap) | macOS install for `merod`, `meroctl`, `cargo-mero`, `mero-abi`, `mero-relayer`. |
| [install-sh](https://github.com/calimero-network/install-sh) | Install scripts for Calimero binaries. |

## Example applications

Real apps, not toy demos — each one is a self-hosted replacement for something you already pay for.

| Repo | Description |
| --- | --- |
| [kv-store](https://github.com/calimero-network/kv-store) | Minimal Rust key-value app. The canonical starter. |
| [kv-store-js](https://github.com/calimero-network/kv-store-js) | Same, in TypeScript, with a React frontend. |
| [mero-chat](https://github.com/calimero-network/mero-chat) | P2P groups and DMs. |
| [mero-meet](https://github.com/calimero-network/mero-meet) | Video calling — WASM signaling, WebRTC media, no server. |
| [mero-design](https://github.com/calimero-network/mero-design) | Collaborative design tool. |
| [mero-pixart](https://github.com/calimero-network/mero-pixart) | Collaborative image editor — layers, masks, curves. |
| [p2p-sheets](https://github.com/calimero-network/p2p-sheets) | Collaborative spreadsheet — CRDT inputs, derive-on-read recalc, live cursors. |
| [mero-calendar](https://github.com/calimero-network/mero-calendar) | Shared team calendars and private events. |
| [MeroSign](https://github.com/calimero-network/MeroSign) | Privacy-first e-signature and document verification. |

<details>
<summary>More examples — games, blobs, workshop builds</summary>

| Repo | Description |
| --- | --- |
| [battleships](https://github.com/calimero-network/battleships) | Turn-based game with private hidden boards — encrypted context state + merobox workflows. |
| [mero-blocks](https://github.com/calimero-network/mero-blocks) | Minecraft-style multiplayer voxel sandbox with no game server; the world is a context. |
| [merraria](https://github.com/calimero-network/merraria) | 45 kB Terraria-style 2D multiplayer mining sandbox. |
| [demo-blob-app](https://github.com/calimero-network/demo-blob-app) | Blob/binary payload handling with a wired frontend. |
| [only-peers-client](https://github.com/calimero-network/only-peers-client) | Minimal P2P forum client. |
| [core/apps](https://github.com/calimero-network/core/tree/master/apps) | In-repo reference apps: `collaborative-editor`, `private-data`, `team-metrics`, and more. |
| [workshop-apps](https://github.com/calimero-network/workshop-apps) | Apps built live at workshops, one per branch. |

</details>

## Documentation & governance

| Repo | Description |
| --- | --- |
| [documentation](https://github.com/calimero-network/documentation) | [docs.calimero.network](https://docs.calimero.network) — concepts, build guides, operations, API reference. Start here for anything conceptual. |
| [proposals](https://github.com/calimero-network/proposals) | Calimero Improvement Proposals (CIPs) — the process for protocol changes. |
| [design-system](https://github.com/calimero-network/design-system) | Shared UI components and design tokens across Calimero frontends. |

> Deep reference for `core` lives in-repo and ships to
> [calimero-network.github.io/core](https://calimero-network.github.io/core/) —
> four tracks: **Build**, **Operate**, **Protocol Reference**, **Contribute**.
> Same pattern for [mero-mcp](https://calimero-network.github.io/mero-mcp/).

## Contributing

Issues and PRs welcome across every repo. Protocol-level changes go through
[CIPs](https://github.com/calimero-network/proposals). Questions and dev support:
[Discord](https://discord.gg/urJeMtRRMu).

Licensed MIT OR Apache-2.0.
