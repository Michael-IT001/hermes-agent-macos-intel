# Hermes Desktop for Intel macOS

Language: [English](#english) | [中文](#中文)

## English

### Hermes Desktop for Intel macOS (official source build)

This repository provides an Intel macOS build of Hermes Desktop compiled from the official NousResearch open-source code.

It was built from the upstream NousResearch repository:

- Upstream: https://github.com/NousResearch/hermes-agent
- Upstream commit: `586aae4bf13c20c3f2966cad590b27946b227bbb`
- Hermes Desktop version: `0.17.0`
- Artifact: `Hermes-0.17.0-mac-x64-official-source-build-586aae4.zip`

Download from the latest release:

https://github.com/Michael-IT001/hermes-agent-macos-intel/releases/latest

### Integrity

Verify the downloaded zip before opening it:

```sh
shasum -a 256 Hermes-0.17.0-mac-x64-official-source-build-586aae4.zip
```

Expected SHA256:

```text
2779bc16d73252a323de5a81f2669c4b2384b510ee28da19a0012ba492cd4a7e  Hermes-0.17.0-mac-x64-official-source-build-586aae4.zip
```

### Important Notes

- Built from the official upstream source code at the commit listed above.
- This repository is maintained independently by the GitHub account owner; it is not maintained, signed, or notarized by Nous Research.
- This build is for Intel macOS only (`x86_64`), not Apple Silicon.
- The app is ad-hoc signed and not Apple-notarized, so macOS Gatekeeper may show a warning.
- Prefer an official upstream Intel or Universal build if Nous Research publishes one.
- This release intentionally does not include the Tauri bootstrap setup installer.

### Safety Checks

Before publishing, the extracted app bundle was checked for:

- local machine username and local user paths
- GitHub token prefixes
- OpenAI/Anthropic API key environment assignments
- private key material
- Finder metadata such as `__MACOSX`, `.DS_Store`, and AppleDouble files
- `x86_64` Mach-O architecture for the app executable and native dependencies

No user-specific local paths, private keys, or personal credentials were found in the published artifact.

See `BUILD.md` for the reproduction commands.

## 中文

### Hermes Desktop Intel macOS 版本（基于官方源码编译）

这个仓库提供 Hermes Desktop 的 Intel macOS 构建版本，基于 NousResearch 官方开源代码编译。

构建来源：

- 上游仓库：https://github.com/NousResearch/hermes-agent
- 上游 commit：`586aae4bf13c20c3f2966cad590b27946b227bbb`
- Hermes Desktop 版本：`0.17.0`
- 下载文件：`Hermes-0.17.0-mac-x64-official-source-build-586aae4.zip`

从最新 Release 下载：

https://github.com/Michael-IT001/hermes-agent-macos-intel/releases/latest

### 完整性校验

打开前建议先校验下载文件：

```sh
shasum -a 256 Hermes-0.17.0-mac-x64-official-source-build-586aae4.zip
```

预期 SHA256：

```text
2779bc16d73252a323de5a81f2669c4b2384b510ee28da19a0012ba492cd4a7e  Hermes-0.17.0-mac-x64-official-source-build-586aae4.zip
```

### 重要说明

- 该版本基于上面列出的官方上游源码 commit 编译。
- 这个仓库由 GitHub 账号所有者独立维护，不是 Nous Research 维护、签名或 notarize 的发布版本。
- 该版本仅适用于 Intel macOS（`x86_64`），不适用于 Apple Silicon。
- App 使用 ad-hoc 签名，没有经过 Apple notarization，首次打开时 macOS Gatekeeper 可能会提示警告。
- 如果 Nous Research 后续发布官方 Intel 或 Universal macOS 版本，建议优先使用官方发布。
- 这个 Release 有意不包含 Tauri bootstrap setup 安装器。

### 安全检查

发布前已对解压后的 app bundle 做过检查，包括：

- 本机用户名和本地用户路径
- GitHub token 前缀
- OpenAI/Anthropic API key 环境变量赋值
- 私钥材料
- `__MACOSX`、`.DS_Store` 和 AppleDouble 文件等 Finder 元数据
- app 主程序和 native 依赖的 `x86_64` Mach-O 架构

发布文件中未发现用户本机路径、私钥或个人凭据。

复现构建命令见 `BUILD.md`。
