# box releases

Linux arm64 builds of the box CLI with Box Core, for running agents in a box on Amazon Bedrock
AgentCore Runtime. The AgentCore CLI (`agentcore`) downloads them when it builds and deploys a
boxed agent.

Each release has:

- `box-v<version>-aarch64-unknown-linux-gnu.tar.gz`: `box`, its two helpers
  (`strands-box-sock-alias`, `strands-box-contain-trampoline`), its packs in `resources/`, and
  `release.json`, which names the source commits. Built on Amazon Linux 2023 (glibc 2.34).
- `box-ffi-python3.14-aarch64-unknown-linux-gnu.tar.gz`: CPython 3.14's `_ctypes` linked to
  libffi 3.5.2 with static trampolines, which Box Core's W^X filter allows. A CodeZip agent puts it
  first on `PYTHONPATH`.
- `SHA256SUMS.txt`: the SHA-256 of each archive.

## Install

```sh
version=0.1.11-linux-preview.2
asset=box-v$version-aarch64-unknown-linux-gnu.tar.gz
curl -fsSLO https://github.com/mquang-amazon/box-releases/releases/download/v$version/$asset
curl -fsSLO https://github.com/mquang-amazon/box-releases/releases/download/v$version/SHA256SUMS.txt
grep " $asset\$" SHA256SUMS.txt | sha256sum -c -
mkdir -p box && tar -C box -xzf "$asset"
./box/box --version
```

## Licenses

box and Box Core: Apache-2.0 (this repository's LICENSE). libffi: MIT. CPython's `_ctypes`: PSF
License Version 2.
