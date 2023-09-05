# RTamSDK

[![Version](https://img.shields.io/cocoapods/v/RTamSDK.svg?style=flat)](https://cocoapods.org/pods/RTamSDK)
[![License](https://img.shields.io/cocoapods/l/RTamSDK.svg?style=flat)](https://cocoapods.org/pods/RTamSDK)
[![Platform](https://img.shields.io/cocoapods/p/RTamSDK.svg?style=flat)](https://cocoapods.org/pods/RTamSDK)

Ads & Analytics Framework from RTAM

This is a project adds support for multi-platform XCFramework, Swift Package and CocoaPods to the RTAM Universal SDK.

## Get Started

### CocoadPods

To use this Pod in your Xcode project, follow these steps:

1. Open your Podfile
2. Add the following code to it:

```ruby
pod `RTamSDK`
```

3. Run `pod install` in your terminal.

### Swift Package

To use this Swift Package in your Xcode project, follow these steps:

1. Open your project in Xcode.
2. Go to File > Swift Packages > Add Package Dependency.
3. Enter the URL of this repository https://github.com/RTAMTECH/rtam_sdk_ios.git and click Next.
4. Choose the version rule you want to use (e.g. "Up to Next Major") and click Next.
5. Select the target you want to add the package to and click Finish.
6. Import the RTamSDK module in your Swift files where you want to use the SDK.

```Swift
import RTamSDK
```

7. You're now ready to use the SDK in your app!

## Usage

### Init

Add this code to Info.plist and replace your writeKey

```xml
<key>RTAMSDKConfig</key>
<dict>
    <key>writeKey</key>
    <string>YOUR_WRITE_KEY_HERE</string>
</dict>
```

Import the RTamSDK module in your UIApplicationDelegate

```swift
import RTamSDK
```

Configure a RTamSDK shared instance in your app delegate's application(_:didFinishLaunchingWithOptions:) method

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // Override point for customization after application launch.

    RTAM.start()


    return true
}
```

### Analytics

Analytics will be initialized and collect data and support manually collect event

#### Track Events

```swift
RTAM.track(name: "Event name", properties: [String : Any]?)
```

You can custom properties anything you want

```swift
struct UserLoggedInEventProperties: Codable {
    var username: String
    var mail: String
}

let userLoggedInEventProperties = UserLoggedInEventProperties(
    username: "tester",
    mail: "tester@mail.com"
)

RTAM.track(name: "User LoggedIn", properties: userLoggedInEventProperties)

```

#### Identify Events

```swift
RTAM.identify(userId: "UserID")
```

In case of you need to append more information

```swift
struct UserTraits: Codable {
    var name: String
    var birthday: String
    var phoneNumber: String
}

let traits = UserTraits(
    name: "Tester",
    birthday: "20/12/2022",
    phoneNumber: "+84909090909"
)

RTAM.identify(userId: "UserID", traits: traits)
```

#### Screen Events

```swift
RTAM.screen(title: "LoginScreen")
```

Properties are extra pieces of information that describe the screen. They can be anything you want.

```swift
struct ScreenProperties: Codable {
    var name: String
    var loginMethod: String
}

let properties = ScreenProperties(
    name: "Login",
    loginMethod: "Apple ID"
)

RTAM.screen(title: "LoginScreen", properties: properties)
```


## Author

RTAM TECH, tech@rtam.io

## License

RTamSDK is available under the MIT license. See the LICENSE file for more info.
