# LOOM Release Channel

This repository hosts the public release-channel metadata for the LOOM / 麓鸣 online portable installer.

It is intentionally small. Large binaries and component archives should live in GitHub Releases, Gitee Releases, OSS, or CDN storage. This repo should only contain manifests, public keys, version indexes, and small metadata files.

## Layout

```text
stable/
  release-manifest.json
  release-public-key.txt

rc/
  release-manifest.json
  release-public-key.txt

versions/
  2.1.19-rc.20260628.json
```

## Channel URLs

```text
https://raw.githubusercontent.com/rfdiosuao/loom-release-channel/main/stable/release-manifest.json
https://raw.githubusercontent.com/rfdiosuao/loom-release-channel/main/rc/release-manifest.json
```

## Rules

- Do not commit private keys, API keys, passwords, or user tokens.
- Do not commit downloaded agent packages or extracted runtime folders.
- Every manifest must be signed and verifiable with the matching public key.
- Every downloadable component must include size, sha256, platform, arch, version, and fallback URLs.
- `stable/` is for user-facing releases. Use `rc/` for test builds.

