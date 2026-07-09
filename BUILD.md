# Build Notes

These are the commands used to build the published Intel macOS artifact.

```sh
git clone https://github.com/NousResearch/hermes-agent.git
cd hermes-agent
git checkout 4d611ba0c3b1f09b8092674a2227254ce8e9d89c

npm install --workspace apps/desktop
GITHUB_SHA=$(git rev-parse HEAD) GITHUB_REF_NAME=main npm run build --workspace apps/desktop
npm_config_arch=x64 npm run builder --workspace apps/desktop -- --mac --x64 --publish=never

xattr -cr apps/desktop/release/mac/Hermes.app || true

# Repair the macOS app icon before signing:
# - convert the upstream PNG-backed icon into a real .icns file
# - crop the runtime Dock PNG transparent border to avoid the black-ring Dock artifact
codesign --force --deep --sign - apps/desktop/release/mac/Hermes.app
COPYFILE_DISABLE=1 ditto -c -k --keepParent \
  apps/desktop/release/mac/Hermes.app \
  apps/desktop/release/Hermes-0.17.0-mac-x64-official-source-build-4d611ba-iconfix.zip
```

Verification commands:

```sh
unzip -q Hermes-0.17.0-mac-x64-official-source-build-4d611ba-iconfix.zip -d audit
file audit/Hermes.app/Contents/MacOS/Hermes
file audit/Hermes.app/Contents/Resources/icon.icns
codesign --verify --deep --strict --verbose=2 audit/Hermes.app
codesign -dv --verbose=2 audit/Hermes.app
shasum -a 256 Hermes-0.17.0-mac-x64-official-source-build-4d611ba-iconfix.zip
```

Expected architecture:

```text
Mach-O 64-bit executable x86_64
```

Expected signature type:

```text
Signature=adhoc
TeamIdentifier=not set
```

Expected icon format:

```text
Mac OS X icon
```
