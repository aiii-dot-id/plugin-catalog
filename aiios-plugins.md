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
  "generated": "2026-09-17T19:08:28Z",
  "plugins": [
    {
      "id": "id.aeon.memory",
      "version": "0.6.3",
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
          "url": "https://github.com/aiii-dot-id/aeon-memory/releases/download/v0.6.3/id.aeon.memory-0.6.3.aiiospkg",
          "sha256": "sha256:4e55ba2a2d966280107ad8bf4f4d06a2e1838aa90528454b0808bbc5cd301c9c",
          "size": 526077
        }
      ]
    },
    {
      "id": "id.aiii.voice",
      "version": "0.1.0-beta.3",
      "tier": "T3",
      "summary": "AII Voice: a native speech engine \u2014 streaming recognition and synthesis, voice activity and turn detection, guided speaker enrollment, and full-duplex interruption with recovery.",
      "packages": [
        {
          "platform": "macos",
          "arch": "arm64",
          "url": "https://github.com/aiii-dot-id/aiios-voice-plugin/releases/download/v0.1.0-beta.3/id.aiii.voice-0.1.0-beta.3.aiiospkg",
          "sha256": "sha256:6bee4d769e0b1d44e7f4cf8431fe6195ecdc179057835b583ca215bf9819a822",
          "size": 9470191
        },
        {
          "platform": "linux",
          "arch": "x86_64",
          "url": "https://github.com/aiii-dot-id/aiios-voice-plugin/releases/download/v0.1.0-beta.3/id.aiii.voice-0.1.0-beta.3.aiiospkg",
          "sha256": "sha256:6bee4d769e0b1d44e7f4cf8431fe6195ecdc179057835b583ca215bf9819a822",
          "size": 9470191
        },
        {
          "platform": "windows",
          "arch": "x86_64",
          "url": "https://github.com/aiii-dot-id/aiios-voice-plugin/releases/download/v0.1.0-beta.3/id.aiii.voice-0.1.0-beta.3.aiiospkg",
          "sha256": "sha256:6bee4d769e0b1d44e7f4cf8431fe6195ecdc179057835b583ca215bf9819a822",
          "size": 9470191
        }
      ],
      "aiios_min_version": "0.1.7",
      "description": "A native T3 voice plugin for AII OS. English speech recognition and synthesis with ten selectable voices, active voice-activity and turn detection, an adjustable reply pause, interruption that keeps the opening words, recovery, and durable guided speaker enrollment and identification. One signed package selects a native runtime for macOS Apple Silicon, Ubuntu x86-64 or Windows x86-64 and its model data through the Plugin SDK; the host owns download, verification, installation, grants, audio, updates and rollback. Desktop beta: English only. Requires AII OS 0.1.7 or newer. Ubuntu 24.04 requires the documented bubblewrap AppArmor profile; see the release notes. Windows generation retirement can exceed the 250 ms target while browser playback stops immediately. Bundled third-party model and runtime components carry their own licenses, noted with the release.",
      "publisher": "AIII",
      "homepage": "https://github.com/aiii-dot-id/aiios-voice-plugin",
      "license": "Apache-2.0"
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
