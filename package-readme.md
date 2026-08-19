# McProtoNet.Native

Prebuilt native libraries for [McProtoNet](https://github.com/Titlehhhh/McProtoNet), a .NET client library for the Minecraft Java Edition protocol.

The package contains no managed code. It carries `runtimes/{rid}/native/` assets; the .NET SDK copies the one that matches the application's runtime identifier, and P/Invoke finds it by name.

## Contents

| Library | Version | Exported name |
| --- | --- | --- |
| [libdeflate](https://github.com/ebiggers/libdeflate) | see release notes | `libdeflate` (`libdeflate.dll` / `libdeflate.so` / `libdeflate.dylib`) |

## Platforms

| RID | Toolchain |
| --- | --- |
| `win-x64`, `win-x86` | MinGW-w64 |
| `win-arm64` | MSVC |
| `linux-x64` | GCC, glibc (Ubuntu 22.04) |
| `linux-arm64`, `linux-arm`, `linux-armv6` | GCC, glibc (Debian bullseye) |
| `linux-musl-x64`, `linux-musl-arm64` | GCC, musl (Alpine) |
| `osx` | Apple clang, universal binary arm64 + x86_64, deployment target 11.0 |

## Usage

Reference the package, then declare the entry points you need:

```csharp
[DllImport("libdeflate", CallingConvention = CallingConvention.Cdecl, ExactSpelling = true)]
static extern IntPtr libdeflate_alloc_decompressor();
```

McProtoNet references this package and keeps its own bindings in `McProtoNet.Net.Zlib`.

## Provenance

Every release is built by the `Release` workflow in the [McProtoNet.Native](https://github.com/Titlehhhh/McProtoNet.Native) repository from the upstream libdeflate tag. The GitHub release holds one zip per RID, the `.nupkg`, and `SHA256SUMS.txt`.

## License

MIT for the package. libdeflate is MIT, Copyright Eric Biggers.
