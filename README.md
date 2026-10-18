# AII OS Plugin Catalog

The signed index of plugins published by AI Identity Incorporated.

- `aiios-plugins.md` contains one JSON catalog block.
- `aiios-plugins.md.sig` signs the exact index bytes.
- Plugin packages and source live in the linked repositories.

Each entry declares a version, supported platforms, download URL, SHA-256,
size and any host compatibility limits. Portable packages use `*` for platform
and architecture. Native packages name each supported platform explicitly.
The host checks compatibility and signatures before installation.

Changes to the index require a new detached signature. Signing inputs and
private keys are not stored in this repository.

Contact: james@aiii.id
