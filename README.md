# BATracer Setup Manager Firefox updates

This public repository hosts the Firefox update manifest and signed XPI release assets for BATracer Setup Manager. The extension source remains in the private `batracer-extension` repository.

Firefox reads the update manifest from:

<https://raw.githubusercontent.com/jakub-iglar-dev/batracer-extension-updates/main/update.json>

## First installation with automatic updates

An already-installed version without `browser_specific_settings.gecko.update_url` cannot discover this update service. The first version containing the update URL must be signed by Mozilla and installed manually once.

The extension source is prepared as version `2.0.3`. Before publishing:

1. Submit/build that version through the Firefox add-on signing flow and download the signed XPI.
2. Create a GitHub Release in this repository with tag `v2.0.3`.
3. Upload the signed XPI asset with the exact name `batracer-setup-manager-2.0.3.xpi`.
4. Verify the asset is publicly downloadable at the URL in `update.json`.
5. Publish `update.json` on the repository's `main` branch.
6. Manually install the signed `2.0.3` XPI in Firefox.

Do not publish an update manifest entry until its signed XPI is publicly available; Firefox needs both the manifest and the downloadable package.

## Publishing later updates

For each release:

1. Bump the extension version in the source manifest and submit it for Mozilla signing.
2. Create a matching GitHub Release/tag named `vVERSION` and upload the signed asset as `batracer-setup-manager-VERSION.xpi`.
3. Update `update.json` with the same version and the direct release asset URL.
4. Publish the `update.json` change to `main`.

Keep the add-on ID in `update.json` identical to `browser_specific_settings.gecko.id` in the signed extension. The XPI and manifest must be available over public HTTPS without authentication.
