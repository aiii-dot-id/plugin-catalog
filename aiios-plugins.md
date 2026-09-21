# AII OS Plugin Catalog

The platform's signed index of installable plugins. The host reads the
single fenced JSON block below and ignores the surrounding prose. The
detached signature `aiios-plugins.md.sig` covers this file's exact
bytes, so nothing written here can disagree with what was signed.

Each plugin lists one or more packages. A **portable** package
(`"platform": "*", "arch": "*"`) is a single WASM build that runs on
every host; a **native** package names a specific `platform`/`arch`. The
host downloads the portable package, or the native package matching its
own platform and arch, verifies the sha256, and installs it beside any
running release.

Each plugin lives in its own repository (or wherever its author publishes
it); the package `url` points there — for example a GitHub release asset.
This repository holds only the index and its signature, nothing else.

```json
{
  "catalog_version": 1,
  "generated": "2026-09-21T16:18:33Z",
  "plugins": [
    {
      "id": "id.aeon.memory",
      "version": "0.6.4",
      "tier": "T3",
      "summary": "A bounded working memory for an identity: notes it is holding in attention, stored through the host's own memory record, distinct from the ledger.",
      "description": "A bounded working memory for an AII OS identity over the plugin key-value store, with durable acts routed through the host memory record: store and search delegate to the host's remember and recall (host-stamped provenance, host-decided similarity and meaning), while recent, get, update, evict, stats and health stay plugin-local working-set acts. Reports coverage, eviction state, migration counts and the store's own persistence verdict. Complements the ledger's permanent record.",
      "publisher": "AIII",
      "homepage": "https://github.com/aiii-dot-id/aeon-memory",
      "license": "Apache-2.0",
      "packages": [
        {
          "platform": "*",
          "arch": "*",
          "url": "https://github.com/aiii-dot-id/aeon-memory/releases/download/v0.6.4/id.aeon.memory-0.6.4.aiiospkg",
          "sha256": "sha256:e2d133407c9c35efd13bb41beaeb7792b08daedd79924a3b9bf80640c0d4a253",
          "size": 528993
        }
      ]
    },
    {
      "id": "id.aiii.voice",
      "version": "0.1.0-beta.5",
      "tier": "T3",
      "summary": "AII Voice",
      "aiios_min_version": "0.1.8",
      "packages": [
        {
          "platform": "macos",
          "arch": "arm64",
          "url": "https://github.com/aiii-dot-id/aiios-voice-plugin/releases/download/v0.1.0-beta.5/id.aiii.voice-0.1.0-beta.5.aiiospkg",
          "sha256": "sha256:2b852d0d00a3a97ff8136688fe71544508cfa373ebc9e58532c0b685437eea70",
          "size": 9586705
        },
        {
          "platform": "linux",
          "arch": "x86_64",
          "url": "https://github.com/aiii-dot-id/aiios-voice-plugin/releases/download/v0.1.0-beta.5/id.aiii.voice-0.1.0-beta.5.aiiospkg",
          "sha256": "sha256:2b852d0d00a3a97ff8136688fe71544508cfa373ebc9e58532c0b685437eea70",
          "size": 9586705
        },
        {
          "platform": "windows",
          "arch": "x86_64",
          "url": "https://github.com/aiii-dot-id/aiios-voice-plugin/releases/download/v0.1.0-beta.5/id.aiii.voice-0.1.0-beta.5.aiiospkg",
          "sha256": "sha256:2b852d0d00a3a97ff8136688fe71544508cfa373ebc9e58532c0b685437eea70",
          "size": 9586705
        }
      ],
      "title": "AII Voice",
      "description": "Native speaker-conditioned speech recognition and synthesis, persistent anonymous speaker UUIDs with post-session naming, ten selectable English voices, active voice-activity detection with adjustable pause and capture limit, interruption and recovery, meeting and output-only modes. One signed package selects the runtime and model files for macOS Apple Silicon, Ubuntu x86-64 or Windows x86-64. AII OS owns downloads, integrity verification, installation, audio, permissions and updates; no system Python is required. Compatible AII OS 0.1.8 enforces UUID-only/ignore filters before identity delivery. English desktop beta; speaker attribution is uncertain evidence, not authentication. Third-party models and runtimes retain their own licenses. See release notes for prerequisites and qualification limits.",
      "publisher": "AIII",
      "homepage": "https://github.com/aiii-dot-id/aiios-voice-plugin",
      "license": "Apache-2.0",
      "category": "voice",
      "keywords": [
        "speech",
        "voice",
        "STT",
        "TTS",
        "VAD",
        "speaker identification"
      ]
    }
  ],
  "must_understand": [
    "compat"
  ]
}
```

To add a plugin, append an object to `plugins` — for example:

    {
      "id": "com.aiii.aeon.memory",
      "version": "1.0.0",
      "tier": "T3",
      "summary": "Aeon's memory: semantic recall over the identity's own notes.",
      "packages": [
        {"platform": "*", "arch": "*",
         "url": "https://github.com/aiii-dot-id/aeon-memory/releases/download/v1.0.0/com.aiii.aeon.memory-1.0.0.aiiospkg",
         "sha256": "sha256:<hex>", "size": 123456}
      ]
    }

then recompute the signature payload and re-sign (see `README.md`).
