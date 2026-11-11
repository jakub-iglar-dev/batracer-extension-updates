# BATracer Setup Manager Firefox updates

This public repository hosts the Firefox update manifest and signed XPI release assets for BATracer Setup Manager. The extension source remains in the private `batracer-extension` repository.

Firefox reads the update manifest from:

<https://raw.githubusercontent.com/jakub-iglar-dev/batracer-extension-updates/main/update.json>

## Publishing version 2.0.4

The extension source is prepared as version `2.0.4`, and `update.json` is configured to point to its signed XPI.

1. In this repository, create a GitHub Release with tag `v2.0.4`.
2. Upload the signed XPI to the release as `batracer-setup-manager-2.0.4.xpi`. The XPI is a release asset; it does not need to be added to the repository files.
3. Verify that the asset is publicly downloadable at the URL in `update.json`.
4. Publish `update.json` on the repository's `main` branch only after the release asset is available.

Do not publish an update manifest entry until its signed XPI is publicly available; Firefox needs both the manifest and the downloadable package.

An already-installed version without `browser_specific_settings.gecko.update_url` cannot discover this update service. Install the signed `2.0.4` XPI manually once; later updates can be delivered through this manifest.

## Publishing later updates

For each release:

1. Bump the extension version in the source manifest and submit it for Mozilla signing.
2. Create a matching GitHub Release/tag named `vVERSION` and upload the signed asset as `batracer-setup-manager-VERSION.xpi`.
3. Verify the asset is publicly downloadable, then update `update.json` with the same version and direct release asset URL.
4. Publish the `update.json` change to `main`.

Keep the add-on ID in `update.json` identical to `browser_specific_settings.gecko.id` in the signed extension. The XPI and manifest must be available over public HTTPS without authentication.
