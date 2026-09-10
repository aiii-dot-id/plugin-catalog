# plugin-catalog

The AII OS plugin catalog (ruling R100): a signed, human-readable index
of installable plugins. It holds ONLY the index and its signature — each
plugin is hosted in its own repository, and the index points at it.

## Layout

    aiios-plugins.md               the catalog index (prose + one fenced json block the host parses)
    aiios-plugins.md.sig           detached PQ signature over aiios-plugins.md's exact bytes
    aiios-plugins.sig-payload.json the payload to sign (regenerate on every edit)

## Index format

`aiios-plugins.md` carries one fenced ```json block:

- `catalog_version` (int), `generated` (RFC3339), `plugins` (array).
- each plugin: `id`, `version`, `tier`, `summary`, `packages`.
- optional on each plugin, shown by the host's plugin store: `description`
  (a paragraph), `publisher`, `homepage` (https), `license` (an SPDX
  identifier). Nothing else: the host refuses an index with a field it
  does not know, so a new field waits for a host that reads it.
- each package: `platform`, `arch`, `url`, `sha256` ("sha256:<hex>"), `size`.

A **portable** WASM package sets `"platform": "*", "arch": "*"` and runs
on every host; a **native** package names a concrete `platform` and
`arch`; list one per supported host. The host prefers an exact
platform/arch match and falls back to the portable package.

`url` is wherever the plugin's author hosts the `.aiiospkg` — its own
GitHub repository's release asset, or any public URL. The catalog does
not host packages; it points at them.

## Signing (platform_release — the same ceremony as a release)

The catalog is signed with the platform_release key exactly as a release
is; only the artifact kind and the payload differ. That key is ONE
envelope carrying both PQ algorithms (ML-DSA-87 and SLH-DSA-SHA2-256s),
so `--priv` is given ONCE — a second `--priv` for the same algorithms is
rejected.

1. Edit `aiios-plugins.md`.
2. Regenerate the payload — its `catalog_sha256` must equal the file's hash:

       printf 'sha256:%s\n' "$(sha256sum aiios-plugins.md | cut -d' ' -f1)"

   and write `aiios-plugins.sig-payload.json`:
   `{ "catalog_version": N, "generated": "...", "catalog_sha256": "sha256:..." }`.
3. Sign, artifact kind `plugin.catalog`:

       ai3-bundle create \
         --artifact-kind plugin.catalog \
         --profile AIII-PQ-SIGNATURE-V1-ROOT \
         --payload aiios-plugins.sig-payload.json \
         --priv <the platform_release private envelope> \
         --output aiios-plugins.md.sig

4. Commit `aiios-plugins.md` and `aiios-plugins.md.sig` together.

The host verifies the signature against the pinned platform_release root,
checks the file hash matches the signed `catalog_sha256`, then parses the
index. A tampered file, or one the signature does not cover, is refused.
