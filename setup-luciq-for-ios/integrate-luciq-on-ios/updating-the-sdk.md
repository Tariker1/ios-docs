# Updating the SDK

You can easily update the Luciq SDK for each platform by following the instructions outlined below. If you wish to update to a specific version (for example, 14.0.0), ensure that your configuration files (Podfile, Cartfile, or Package.swift) reflect this version accordingly.

## CocoaPods

To update to the latest version of Luciq, use the following command:

```
pod update Luciq
```

If you need to update to a specific version (e.g., 14.0.0), specify it in your Podfile like this:

```
pod 'Luciq', '14.0.0'
```

After making the change, run:

```
pod install
```

***

## Carthage

To update to the latest version of Luciq, execute:

```
carthage update
```

For a specific version, indicate it in your Cartfile as follows:

```
github "luciqai/luciq-ios-sdk" == 18.0.0
```

Then, run:

```
carthage update
```

***

## Swift Package Manager (SPM)

### Updating via Xcode Interface:

1. Open your Xcode project.
2. In the Project Navigator on the left, select your project.
3. Navigate to the Package Dependencies tab under your project settings.
4. To update all packages to their latest compatible versions, go to **File > Swift Packages > Update to Latest Package Versions**.
5. To update only Luciq:
   1. Select the Luciq package from the list of dependencies.
   2. Click the gear icon next to it.
   3. Choose **Update Package** to fetch and use the latest version that meets your version requirements.

### Updating via Command Line

#### To Update to the Latest Compatible Version:

1. In your Package.swift, add:

```
.package(url: "<https://github.com/luciqai/luciq-ios-sdk">, from: "18.0.0")
```

2. Then, run:

```
swift package update
```

#### To Update to a Specific Version (e.g., 14.0.0):

1. In your Package.swift, specify:

```
.package(url: "<https://github.com/luciqai/luciq-ios-sdk">, .exact("18.0.0"))
```

2. Finally, execute:

```
swift package update
```
