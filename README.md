# QRCodeKit

QRCodeKit is a Swift Package for generating QRCode on both iOS and macOS. The iOS part of this project is mainly from [aschuch/QRCode](https://github.com/aschuch/QRCode). The latter was coded in Swift 3.0 and supported iOS only using Carthage.

I copied the code and upgrade it to Swift 5. Then using Swift Package Manger and added the macOS supporting part.

## How to use
### Xcode
File -> Swift Packages -> Add Package Dependency. Copy and Paste the git repo URL. Both the https or ssh URL will work. 

### Swift Package

```swift
// swift-tools-version:5.3
// The swift-tools-version declares the minimum version of Swift required to build this package.

import PackageDescription

let package = Package(
    name: "MyAppStore",
    platforms: [
        .macOS(.v11)
    ],
    products: [
        // Products define the executables and libraries a package produces, and make them visible to other packages.
        .library(
            name: "MyAppStore",
            targets: ["MyAppStore"]),
    ],
    dependencies: [
        // Dependencies declare other packages that this package depends on.
        // .package(url: /* package url */, from: "1.0.0"),
        .package(url: "git@github.com:owenzhao/QRCodeKit.git", from: "1.0.0")
    ],
    targets: [
        // Targets are the basic building blocks of a package. A target can define a module or a test suite.
        // Targets can depend on other targets in this package, and on products in packages this package depends on.
        .target(
            name: "MyAppStore",
            dependencies: ["QRCodeKit"]),
        .testTarget(
            name: "MyAppStoreTests",
            dependencies: ["MyAppStore", "QRCodeKit"]),
    ]
)
```