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
- each package: `platform`, `arch`, `url`, `sha256` ("sha256:<hex>"), `size`.

A **portable** WASM package sets `"platform": "*", "arch": "*"` and runs
on every host; a **native** package names a concrete `platform` and
`arch`; list one per supported host. The host prefers an exact
platform/arch match and falls back to the portable package.

`url` is wherever the plugin's author hosts the `.aiiospkg` — its own
GitHub repository's release asset, or any public URL. The catalog does
not host packages; it points at them.

## Signing (platform_release — the same air-gapped ai3-bundle ceremony as a release)

1. Edit `aiios-plugins.md`.
2. Regenerate the payload — its `catalog_sha256` must equal the file's hash:

       printf 'sha256:%s\n' "$(sha256sum aiios-plugins.md | cut -d' ' -f1)"

   and write `aiios-plugins.sig-payload.json`:
   `{ "catalog_version": N, "generated": "...", "catalog_sha256": "sha256:..." }`.
3. Sign with the platform_release key, artifact kind `plugin.catalog`:

       ai3-bundle -artifact-kind plugin.catalog -profile AIII-PQ-SIGNATURE-V1-ROOT \
         -payload aiios-plugins.sig-payload.json \
         -private-key <platform ml> -private-key <platform slh> \
         -out aiios-plugins.md.sig

4. Commit `aiios-plugins.md` and `aiios-plugins.md.sig` together.

The host verifies the signature against the pinned platform_release root,
checks the file hash matches the signed `catalog_sha256`, then parses the
index. A tampered file, or one the signature does not cover, is refused.
