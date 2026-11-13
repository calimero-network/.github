<h1 align="center">Calimero</h1>

<p align="center">
  <b>Your app's whole backend, like Firebase. Except nobody can read your data, not even us.</b><br/>
  <i>Auth, database, functions, realtime, storage and hosting in one deploy, running in verified confidential hardware.</i>
</p>

<p align="center">
  <a href="https://calimero.network" target="_blank"><img src="https://img.shields.io/badge/Website-calimero.network-black?style=flat-square" /></a>
  <a href="https://cloud.calimero.network" target="_blank"><img src="https://img.shields.io/badge/Cloud-cloud.calimero.network-black?style=flat-square" /></a>
  <a href="https://calimero-network.github.io/core/" target="_blank"><img src="https://img.shields.io/badge/Docs-calimero--network.github.io%2Fcore-black?style=flat-square" /></a>
  <a href="https://apps.calimero.network" target="_blank"><img src="https://img.shields.io/badge/Apps-apps.calimero.network-black?style=flat-square" /></a>
  <a href="https://x.com/CalimeroNetwork" target="_blank"><img src="https://img.shields.io/badge/Twitter-@CalimeroNetwork-black?style=flat-square&logo=x&logoColor=white" /></a>
</p>

---

## Everything a backend needs, sealed

Firebase made building an app fast: sign-in, a database, functions and hosting,
all in one place. The catch is that the provider can read everything. Calimero
gives you the same building blocks, but each app runs inside attested Intel TDX
hardware, so the people running the servers, including us, can't see the data.
And your users don't have to take our word for it: their client checks.

| You need | Calimero gives you |
| --- | --- |
| Auth | Passkey sign-in, sessions and scoped API keys, built in |
| Database | Replicated app state: maps, sets, tables with indexes, rich text |
| Functions | App methods in Rust, plus compute jobs, timers and pipelines |
| Realtime | Live events and presence streamed to every client |
| Storage | Sealed file and blob storage |
| Search | Full-text search over your app's data |
| Hosting | Your frontend served from the same verified nodes |
| Typed clients | TypeScript, Python, Swift and Kotlin, generated from your app |

You write the app in Rust, build it to WebAssembly and deploy it as one signed
package. Each instance runs on its own small cluster of attested nodes.

## Why it's different: don't trust us, verify us

- **Private by construction.** Data is sealed inside the enclave and on disk.
  Disk keys are released only to nodes that pass attestation, so nobody who runs
  the machines can read it.
- **Verifiable by every user.** Clients check a node's hardware attestation
  against signed releases before sending a byte. Every answer comes back with a
  signed receipt.
- **Run it anywhere.** Calimero Cloud, a dedicated cluster, or your own TDX
  hosts. Same app, no lock-in to our hardware.
- **Nothing changes without consent.** New code or a new node image reaches an
  app's data only after the app's approver says yes.

**Built for apps where privacy is the point:** AI agents that hold credentials,
password vaults and key management, document signing, e-voting, clean rooms and
data shared between companies, regulated records. Plus everyday tools (chat,
docs, spreadsheets, CRM) whose host can't read them.

## Get started

| I want to… | Go to |
| --- | --- |
| Deploy an app without running anything | [Calimero Cloud](https://cloud.calimero.network): free tier, no minimum |
| Understand how it works | [Cloud overview](https://calimero-network.github.io/core/cloud/overview/) · [Protocol reference](https://calimero-network.github.io/core/protocol/overview/) |
| Write an app | [Build](https://calimero-network.github.io/core/build/): the Rust SDK and `mero-app-build`, in [core](https://github.com/calimero-network/core) |
| Call an app from a frontend or a script | [mero-js](https://github.com/calimero-network/mero-js) · [mero-react](https://github.com/calimero-network/mero-react) · [calimero-client-py](https://github.com/calimero-network/calimero-client-py) |
| Run a cluster yourself | [Operate](https://calimero-network.github.io/core/operate/) |
| See real apps | [apps](https://github.com/calimero-network/apps): 27 apps, from chat to e-voting |
| Coming from the peer-to-peer release | [Coming from v1](https://calimero-network.github.io/core/cloud/coming-from-v1/) |

Try it locally from a checkout of [core](https://github.com/calimero-network/core):

```bash
cargo run -p merod -- local                  # a 3-node development cluster on 127.0.0.1:2501-2503
cargo install --path crates/meroctl
meroctl node add local http://127.0.0.1:2501/ --allow-mock
meroctl login --dev-passkey ./dev-passkey.json --name ada
scripts/install-mero-app-build.sh            # once: puts mero-app-build on PATH
mero-app-build apps/kv-store --out kv_store.wasm
meroctl context create --path kv_store.wasm --name kv --alias kv
meroctl call --context kv set --args '{"key":"a","value":"1"}'
```

The full walk-through, with the JavaScript and Python clients, is the
[Quickstart](https://calimero-network.github.io/core/cloud/quickstart/).

---

## Repositories

**Platform**

| Repo | What it is |
| --- | --- |
| [core](https://github.com/calimero-network/core) | The node (`merod`), the CLI (`meroctl`), the Rust app SDK, `mero-app-build`, and the docs. The heart of the stack. |
| [mero-tee](https://github.com/calimero-network/mero-tee) | TDX node images, mero-kms, signed releases, and the public [attestation verifier](https://github.com/calimero-network/mero-tee/tree/master/attestation-verifier). |
| [app-registry](https://github.com/calimero-network/app-registry) | Where signed apps are published and installed from. Live at [apps.calimero.network](https://apps.calimero.network). |

**Clients**: each one verifies the node's attestation and opens a sealed channel before it sends anything.

| Repo | Platform |
| --- | --- |
| [mero-js](https://github.com/calimero-network/mero-js) | TypeScript: browser, Node and edge |
| [mero-react](https://github.com/calimero-network/mero-react) | React hooks and provider over mero-js |
| [calimero-client-py](https://github.com/calimero-network/calimero-client-py) | Python: automation, scripting, operations |
| [swift-sdk](https://github.com/calimero-network/swift-sdk) | Swift: iOS and macOS |
| [kotlin-sdk](https://github.com/calimero-network/kotlin-sdk) | Kotlin: Android |

**Apps and tools**

| Repo | What it is |
| --- | --- |
| [apps](https://github.com/calimero-network/apps) | 27 apps in one monorepo: chat, docs, spreadsheets, CRM, a password vault, document signing, e-voting, design tools, games. |
| [mero-tag](https://github.com/calimero-network/mero-tag) · [mero-ar](https://github.com/calimero-network/mero-ar) | Live location sharing, and shared AR scene editing, each kept on your organization's attested cluster. |
| [calimero-skills](https://github.com/calimero-network/calimero-skills) | Skills that teach AI coding assistants to build on Calimero. |
| [homebrew-tap](https://github.com/calimero-network/homebrew-tap) | `brew install` for `merod` and `meroctl`. |

> Reference documentation for `core` is built from the repo and published at
> [calimero-network.github.io/core](https://calimero-network.github.io/core/),
> in five tracks: **Cloud**, **Build**, **Operate**, **Protocol Reference** and **Contribute**.

## Contributing

Issues and PRs are welcome across every repo.

Licensed MIT OR Apache-2.0.
