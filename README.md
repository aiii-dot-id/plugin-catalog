# AII OS Plugin Catalog

The signed index of plugins published by AI Identity Incorporated.

- Each AII OS release line reads its own index: AII OS 0.1 reads
  `aiios-plugins.md`, and each later line reads `aiios-plugins-<major>.<minor>.md`
  (AII OS 0.2 reads `aiios-plugins-0.2.md`). Each holds one JSON catalog block.
- Each index's `.sig` signs its exact bytes; the signature of a later line's
  index names that line, so an index is read only by its own line's hosts.
- Plugin packages and source live in the linked repositories.

Each entry declares a version, supported platforms, download URL, SHA-256,
size and any host compatibility limits. Portable packages use `*` for platform
and architecture. Native packages name each supported platform explicitly.
The host checks compatibility and signatures before installation.

Changes to the index require a new detached signature. Signing inputs and
private keys are not stored in this repository.

Contact: james@aiii.id
