# Cribra for Swift

Cribra is an embeddable, local-first Rust engine for deterministic detection,
validation, review and explicit transformation of secrets and sensitive data.
This repository distributes the official Swift **Fuse** binding for Apple
platforms.

**Fuse 0.7.2 is publicly available.** The package is installed through SwiftPM;
the XCFramework release asset is downloaded automatically and checksum-verified.
Consumers do not need Rust, Cargo, UniFFI generators or a Cribra source checkout.

## Package

- SwiftPM package identity: `cribra-swift`
- Manifest package name: `Cribra`
- Public product and Swift module: `Cribra`
- Native binary target: `CribraFFI`
- Profile: **Fuse**
- Swift tools version: `6.4`
- Published version: `0.7.2`

The Fuse binding exposes the complete supported Swift surface: scanning,
configuration, batch scanning, admitted streaming, incremental snapshots, the
four transformations, Share Bundles and parallel scanning.

## Installation

Add the package to `Package.swift`:

```swift
dependencies: [
    .package(
        url: "https://github.com/Metalymph/cribra-swift",
        exact: "0.7.2"
    )
]
```

Link the `Cribra` product from the application target:

```swift
.product(
    name: "Cribra",
    package: "cribra-swift"
)
```

Then import the module:

```swift
import Cribra
```

SwiftPM downloads:

```text
https://github.com/Metalymph/cribra-swift/releases/download/0.7.2/CribraFFI-fuse-0.7.2.xcframework.zip
```

and verifies the manifest checksum. The archive is a GitHub Release asset and is
never committed to this repository.

## Supported platforms

| Platform | Architecture | Minimum |
| --- | --- | --- |
| macOS | ARM64 | macOS 13 |
| iOS device | ARM64 | iOS 16 |
| iOS Simulator | ARM64 | iOS 16 |

Intel macOS, Intel Simulator, Mac Catalyst, tvOS, watchOS and visionOS slices are
not included. Deployment minimums are declared compatibility floors, not runtime
qualification on every OS release. No signing or notarization qualification was
performed.

## Qualification

- SwiftPM resolved exactly `0.7.2` from the remote repository.
- The published XCFramework was downloaded and checksum-validated.
- An external macOS ARM64 consumer built and executed successfully.
- An external consumer compiled and linked for
  `arm64-apple-ios16.0-simulator`.

iOS Simulator runtime and physical-device runtime were not tested. The package is
not registered in Swift Package Index.

## Relationship to Cribra

The [main Cribra repository](https://github.com/Metalymph/cribra) owns the Rust
Core, adapters, generated bindings and qualification evidence. The Rust Core is
the semantic authority; this package only distributes the matched Swift source
and Fuse native binary.

Core and Flow remain available through source builds in the main repository. They
are not separate packages here. Use exactly one matching profile per application
or process.

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
| Published tag commit | `fa37a32dc04f4574e9972b488637519c602ce671` |
| Build timestamp | `2026-10-29T13:22:50Z` |
| Build command | `just swift-apple-dist fuse` |
| Archive | `CribraFFI-fuse-0.7.2.xcframework.zip` |
| Archive size | `22,944,085` bytes |
| SwiftPM checksum / SHA-256 | `b1a31ca95709efaf8cb4d8dd23ebb498f2a3c8dd65b7a5121ad63e01ad4469e6` |
| `BuildInfo.swift` SHA-256 | `139fa2b4401b3e673ea05fa1c95d15344aaed4ccc657557054abbd4a09618c75` |
| `Cribra.swift` SHA-256 | `6c274eb8833f5fadcad667abfd4875756c63fa9bd6dc2c307182247d32660aa7` |

This README is maintained on `main` after publication. The immutable `0.7.2` tag
contains the initial release tree; later documentation commits do not change the
tag, the manifest, the generated Swift sources or the published archive.

## License

MIT. See [LICENSE](LICENSE).
