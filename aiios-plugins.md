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
  "generated": "2026-10-09T18:10:21Z",
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
      "version": "0.1.0-beta.11",
      "tier": "T3",
      "summary": "AII Voice",
      "aiios_min_version": "0.1.15",
      "packages": [
        {
          "platform": "macos",
          "arch": "arm64",
          "os_min_version": "26.5",
          "url": "https://github.com/aiii-dot-id/aiios-voice-plugin/releases/download/v0.1.0-beta.11/id.aiii.voice-0.1.0-beta.11.aiiospkg",
          "sha256": "sha256:105ed642773a35bd41bc3a5e8151171162ff6644437840864cad8f885543394a",
          "size": 25064898
        },
        {
          "platform": "linux",
          "arch": "x86_64",
          "url": "https://github.com/aiii-dot-id/aiios-voice-plugin/releases/download/v0.1.0-beta.11/id.aiii.voice-0.1.0-beta.11.aiiospkg",
          "sha256": "sha256:105ed642773a35bd41bc3a5e8151171162ff6644437840864cad8f885543394a",
          "size": 25064898
        },
        {
          "platform": "windows",
          "arch": "x86_64",
          "url": "https://github.com/aiii-dot-id/aiios-voice-plugin/releases/download/v0.1.0-beta.11/id.aiii.voice-0.1.0-beta.11.aiiospkg",
          "sha256": "sha256:105ed642773a35bd41bc3a5e8151171162ff6644437840864cad8f885543394a",
          "size": 25064898
        }
      ],
      "title": "AII Voice",
      "description": "Native speech recognition and synthesis: English recognition with a correction list the identity can teach, twenty selectable voices, seven speaking languages (a language other than English is downloaded when it is chosen), active voice-activity detection with an adjustable pause, interruption and recovery, and guided speaker enrollment and identification. One signed package selects the companion runtime and model data for macOS Apple Silicon, Ubuntu x86-64 or Windows x86-64. AII OS owns downloads, integrity verification, installation, audio, permissions and updates; no system Python is required. Desktop beta: recognition is English only. Speaker identification is probabilistic evidence, not authentication. Read the release notes for prerequisites, settings and qualification limits. Third-party model and runtime components retain their own licenses.",
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
    },
    {
      "id": "id.aiii.codequality",
      "version": "0.1.10",
      "tier": "T3",
      "summary": "Measures source code quality with TypeSafe's Jev as the judge: findings and leads, located to their function where Jev is sure, dimension scores, an index and a band for each file.",
      "description": "Measures source code quality with TypeSafe's Jev as the judge: a fixed catalogue of fault statements asked about each file's code and, separately, its comments; answers scored into findings, six dimension scores, an index and a band. Judges texts passed in, or scans a folder in the identity's sandbox a few files per call.",
      "publisher": "AIII",
      "homepage": "https://github.com/aiii-dot-id/aii-codequality-plugin",
      "license": "Apache-2.0",
      "category": "code quality",
      "keywords": [
        "code quality",
        "code review",
        "maintainability",
        "Jev",
        "scan"
      ],
      "packages": [
        {
          "platform": "*",
          "arch": "*",
          "url": "https://github.com/aiii-dot-id/aii-codequality-plugin/releases/download/v0.1.10/id.aiii.codequality-0.1.10.aiiospkg",
          "sha256": "sha256:975861971767e6bb01bca4b95e1fd3397f8f413849f295446aaaad2c3dd77684",
          "size": 1633924
        }
      ],
      "aiios_min_version": "0.1.10"
    },
    {
      "id": "id.aiii.meaning",
      "version": "0.0.1-beta.5",
      "tier": "T3",
      "summary": "AII Meaning",
      "aiios_min_version": "0.1.15",
      "packages": [
        {
          "platform": "macos",
          "arch": "arm64",
          "os_min_version": "26.5",
          "url": "https://github.com/aiii-dot-id/aiios-meaning-plugin/releases/download/v0.0.1-beta.5/id.aiii.meaning-0.0.1-beta.5.aiiospkg",
          "sha256": "sha256:7bae0c8a13fbb977a3318fa33953d05b0dd61a13c346ca503e5d30b6f6950e9c",
          "size": 5525683
        },
        {
          "platform": "linux",
          "arch": "x86_64",
          "url": "https://github.com/aiii-dot-id/aiios-meaning-plugin/releases/download/v0.0.1-beta.5/id.aiii.meaning-0.0.1-beta.5.aiiospkg",
          "sha256": "sha256:7bae0c8a13fbb977a3318fa33953d05b0dd61a13c346ca503e5d30b6f6950e9c",
          "size": 5525683
        },
        {
          "platform": "linux",
          "arch": "arm64",
          "url": "https://github.com/aiii-dot-id/aiios-meaning-plugin/releases/download/v0.0.1-beta.5/id.aiii.meaning-0.0.1-beta.5.aiiospkg",
          "sha256": "sha256:7bae0c8a13fbb977a3318fa33953d05b0dd61a13c346ca503e5d30b6f6950e9c",
          "size": 5525683
        },
        {
          "platform": "windows",
          "arch": "x86_64",
          "url": "https://github.com/aiii-dot-id/aiios-meaning-plugin/releases/download/v0.0.1-beta.5/id.aiii.meaning-0.0.1-beta.5.aiiospkg",
          "sha256": "sha256:7bae0c8a13fbb977a3318fa33953d05b0dd61a13c346ca503e5d30b6f6950e9c",
          "size": 5525683
        }
      ],
      "title": "AII Meaning",
      "description": "Recall by meaning, computed on this machine. Turns a memory or a cue into a vector with a multilingual embedding model, so that the identity's recall finds what is near in sense as well as what shares words. Only AII OS asks it: it has no network, no tools, no settings and no storage, and keeps nothing it is handed. AII OS downloads the model and its tokenizer (328 MB) and the runtime for its own platform and verifies each. It computes on the processor, on at most four threads, and lets the model go from memory a minute after the last recall. A memory is read to its first 2,048 tokens: the whole of an 8,000-character entry in English, German or Spanish, and about the first 3,900 characters of Korean, 3,450 of Japanese and 2,900 of Chinese; what lies after that in a long entry is not read. Beta: Linux x86-64 and Linux arm64 (glibc 2.34 or later, as in Debian 12 and Ubuntu 22.04), macOS Apple Silicon (macOS 26.5 or later) and Windows x86-64.",
      "publisher": "AIII",
      "homepage": "https://github.com/aiii-dot-id/aiios-meaning-plugin",
      "license": "Apache-2.0",
      "category": "memory",
      "keywords": [
        "memory",
        "recall",
        "embeddings",
        "meaning",
        "semantic search"
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
