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
  "generated": "2026-09-12T21:48:10Z",
  "plugins": [
    {
      "id": "id.aeon.memory",
      "version": "0.6.2",
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
          "url": "https://github.com/aiii-dot-id/aeon-memory/releases/download/v0.6.2/id.aeon.memory-0.6.2.aiiospkg",
          "sha256": "sha256:23d30d03a8162f625e574fbf539b3ab53e3369bc7b17899526454707c1cdc86b",
          "size": 526274
        }
      ]
    }
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
