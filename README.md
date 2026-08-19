# McProtoNet.Native

Native binaries for [McProtoNet](https://github.com/Titlehhhh/McProtoNet). Today: [libdeflate](https://github.com/ebiggers/libdeflate). The package id is `McProtoNet.Native`; more native libraries can be added later under the same package.
Fork of [steviegt6/LibDeflate.Native](https://github.com/steviegt6/LibDeflate.Native) (itself a fork of [jzebedee/LibDeflate.Native](https://github.com/jzebedee/LibDeflate.Native)).

## How a release is made

1. Open Actions → **Release** → Run workflow. Enter the upstream tag (for example `v1.25`).
2. The workflow builds the shared library from that tag for every RID below, packs `McProtoNet.Native.<version>.nupkg`, and creates a GitHub release `v<version>` with one zip per RID, the nupkg, and `SHA256SUMS.txt`.

The package is not pushed to nuget.org. Consume it from the release assets or a local feed.

## Platforms

| RID | Notes |
| --- | --- |
| `win-x64`, `win-x86` | MinGW cross build |
| `win-arm64` | MSVC |
| `linux-x64` | glibc (Ubuntu 22.04 toolchain) |
| `linux-arm64`, `linux-arm`, `linux-armv6` | glibc (Debian bullseye) |
| `linux-musl-x64`, `linux-musl-arm64` | Alpine |
| `osx` | universal binary: arm64 + x86_64, deployment target 11.0 |
