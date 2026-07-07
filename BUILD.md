# Build Notes

These are the commands used to build the published Intel macOS artifact.

```sh
git clone https://github.com/NousResearch/hermes-agent.git
cd hermes-agent
git checkout 586aae4bf13c20c3f2966cad590b27946b227bbb

npm install --workspace apps/desktop
GITHUB_SHA=$(git rev-parse HEAD) GITHUB_REF_NAME=main npm run build --workspace apps/desktop
npm_config_arch=x64 npm run builder --workspace apps/desktop -- --mac --x64 --publish=never

xattr -cr apps/desktop/release/mac/Hermes.app || true
codesign --force --deep --sign - apps/desktop/release/mac/Hermes.app
COPYFILE_DISABLE=1 ditto -c -k --keepParent \
  apps/desktop/release/mac/Hermes.app \
  apps/desktop/release/Hermes-0.17.0-mac-x64-unofficial-586aae4.zip
```

Verification commands:

```sh
unzip -q Hermes-0.17.0-mac-x64-unofficial-586aae4.zip -d audit
file audit/Hermes.app/Contents/MacOS/Hermes
codesign --verify --deep --strict --verbose=2 audit/Hermes.app
codesign -dv --verbose=2 audit/Hermes.app
shasum -a 256 Hermes-0.17.0-mac-x64-unofficial-586aae4.zip
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
