# Cribra for Swift

Cribra is an embeddable, local-first Rust engine for deterministic detection,
validation, review and explicit transformation of secrets and sensitive data.
This repository distributes the official Swift **Fuse** binding.

> **Status: unpublished.** This repository is prepared locally. The remote
> repository, `0.7.2` release, binary asset, tag and Swift Package Index entry do
> not exist yet. The manifest references a planned release URL that is not live.
> Do not add this package as a dependency until publication and the clean-room
> remote-consumer acceptance gate are complete.

## Package

- SwiftPM package identity: `cribra-swift`
- Manifest package name: `Cribra`
- Public product and Swift module: `Cribra`
- Native binary target: `CribraFFI`
- Profile: **Fuse**
- Swift tools version: `6.4`

The Fuse binding exposes the complete supported Swift surface: scanning,
configuration, batch scanning, admitted streaming, incremental snapshots, the
four transformations, Share Bundles and parallel scanning.

Supported platforms:

| Platform | Architecture | Minimum |
| --- | --- | --- |
| macOS | ARM64 | macOS 13 |
| iOS device | ARM64 | iOS 16 |
| iOS Simulator | ARM64 | iOS 16 |

Intel macOS, Intel Simulator, Mac Catalyst, tvOS, watchOS and visionOS slices are
not included. Deployment minimums are declared compatibility floors, not runtime
qualification on every OS release.

## Installation after publication

Once the `0.7.2` release and its XCFramework asset exist and the remote package
passes its acceptance gate, add the package to `Package.swift`:

```swift
dependencies: [
    .package(
        url: "https://github.com/Metalymph/cribra-swift",
        exact: "0.7.2"
    )
]
```

Then link the `Cribra` product and import the module:

```swift
import Cribra
```

This dependency does not resolve today. The manifest intentionally points at:

```text
https://github.com/Metalymph/cribra-swift/releases/download/0.7.2/CribraFFI-fuse-0.7.2.xcframework.zip
```

The archive is a GitHub Release asset and is never committed to this repository.

## Relationship to Cribra

The [main Cribra repository](https://github.com/Metalymph/cribra) owns the Rust
Core, adapters, generated bindings and qualification evidence. The Rust Core is
the semantic authority; this package only distributes the matched Swift source
and Fuse native binary.

Core and Flow remain source-build alternatives in the main repository. They are
not separate packages in this repository. Use exactly one matching profile per
application or process.

Documentation:

- [Getting started](https://github.com/Metalymph/cribra/blob/main/docs/GETTING_STARTED.md)
- [Compatibility and distribution status](https://github.com/Metalymph/cribra/blob/main/docs/COMPATIBILITY.md)
- [Swift consumer guide](https://github.com/Metalymph/cribra/blob/main/bindings/swift/README.md)
- [Ecosystem and binding policy](https://github.com/Metalymph/cribra/blob/main/docs/ECOSYSTEM.md)
- [Roadmap](https://github.com/Metalymph/cribra/blob/main/ROADMAP.md)

## Build provenance

| Item | Value |
| --- | --- |
| Swift distribution version | `0.7.2` |
| Rust Core | `0.7.2` |
| UniFFI adapter | `0.1.0` |
| UniFFI generator | `0.32.2` |
| Rust toolchain | `1.97.0` |
| Swift compiler | `6.4` |
| Cribra source revision | `35cd6801c76b4cd51bf6ad8ff684fa48390b4113` (clean) |
| Build timestamp | `2026-10-29T13:22:50Z` |
| Build command | `just swift-apple-dist fuse` |
| Archive | `CribraFFI-fuse-0.7.2.xcframework.zip` |
| Archive size | `22,944,085` bytes |
| SwiftPM checksum / SHA-256 | `b1a31ca95709efaf8cb4d8dd23ebb498f2a3c8dd65b7a5121ad63e01ad4469e6` |
| `BuildInfo.swift` SHA-256 | `139fa2b4401b3e673ea05fa1c95d15344aaed4ccc657557054abbd4a09618c75` |
| `Cribra.swift` SHA-256 | `6c274eb8833f5fadcad667abfd4875756c63fa9bd6dc2c307182247d32660aa7` |

Local W3.1C qualification ran the Fuse consumer on macOS ARM64 and compiled and
linked the same consumer for `arm64-apple-ios16.0-simulator`. The Simulator result
is compile/link evidence, not Simulator launch or device execution. No remote
SwiftPM resolution or downloaded-asset verification has occurred.

## License

MIT. See [LICENSE](LICENSE).
