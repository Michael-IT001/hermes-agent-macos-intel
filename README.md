# Hermes Desktop for Intel macOS (official source build)

This repository provides an Intel macOS build of Hermes Desktop compiled from the official NousResearch open-source code.

It was built from the upstream NousResearch repository:

- Upstream: https://github.com/NousResearch/hermes-agent
- Upstream commit: `586aae4bf13c20c3f2966cad590b27946b227bbb`
- Hermes Desktop version: `0.17.0`
- Artifact: `Hermes-0.17.0-mac-x64-official-source-build-586aae4.zip`

Download from the latest release:

https://github.com/Michael-IT001/hermes-agent-macos-intel/releases/latest

## Integrity

Verify the downloaded zip before opening it:

```sh
shasum -a 256 Hermes-0.17.0-mac-x64-official-source-build-586aae4.zip
```

Expected SHA256:

```text
2779bc16d73252a323de5a81f2669c4b2384b510ee28da19a0012ba492cd4a7e  Hermes-0.17.0-mac-x64-official-source-build-586aae4.zip
```

## Important Notes

- Built from the official upstream source code at the commit listed above.
- This repository is maintained independently by the GitHub account owner; it is not maintained, signed, or notarized by Nous Research.
- This build is for Intel macOS only (`x86_64`), not Apple Silicon.
- The app is ad-hoc signed and not Apple-notarized, so macOS Gatekeeper may show a warning.
- Prefer an official upstream Intel or Universal build if Nous Research publishes one.
- This release intentionally does not include the Tauri bootstrap setup installer.

## Safety Checks

Before publishing, the extracted app bundle was checked for:

- local machine username and local user paths
- GitHub token prefixes
- OpenAI/Anthropic API key environment assignments
- private key material
- Finder metadata such as `__MACOSX`, `.DS_Store`, and AppleDouble files
- `x86_64` Mach-O architecture for the app executable and native dependencies

No user-specific local paths, private keys, or personal credentials were found in the published artifact.

See `BUILD.md` for the reproduction commands.
