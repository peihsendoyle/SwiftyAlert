# SwiftyAlert

[![CocoaPods](https://img.shields.io/cocoapods/v/SwiftyAlert.svg)]()
[![GitHub release](https://img.shields.io/github/release/simorgh3196/SwiftyAlert.svg)]()
[![Swift version](https://img.shields.io/badge/swift-4.0-blue.svg?style=flat)]()

Simple UIAlertController and UIAlertView wrapper.
Enable to use Swifty.


## Installation and Setup

### Installing with Carthage
```
github "simorgh3196/SwiftyAlert"
```

### Installing with CocoaPods
To integrate SwiftyAlert into your Xcode project using CocoaPods, specify it in your Podfile and run pod install.

```
platform :ios, '8.0'
use_frameworks!
pod "SwiftyAlert", '~>1.1.0'
```

### Manual Installation
To install SwiftyAlert without a dependency manager, please add Alert.swift to your Xcode Project.


## How to use
- Add import
``` swift
import SwiftyAlert
```

- The most simple alert
``` swift
Alert(title: "AlertTitle").addOk().show(self)
```

- Simple Alert
``` swift
Alert(title: "Alert", message: "Simple Alert.")
    .addDefault("OK")
    .show()
```

- Action Sheet
``` swift
Alert(title: "ActionSheet", style: .ActionSheet)
    .addDefault("Take Photo") { print("take phote") }
    .addDefault("Open Library") { print("open library") }
    .addDestructive("Delete") { print("delete") }
    .addCancel()
    .handlePopoverController { [weak self] controller in    //for iPad
        controller?.sourceView = self?.view
        controller?.sourceRect = sender.frame
    }
    .show()
```

- With TextField
``` swift
Alert(title: "Alert", message: "Alert with TextField.")
    .addTextField { textField in
        textField.placeholder = "ID"
    }
    .addTextField { textField in
        textField.placeholder = "Password"
        textField.secureTextEntry = true
    }
    .handleTextFieldDidChange { textField, index in
        print("Index of textFields:", index, "text:", textField.text)
        if textField.text?.count > 5 {
            textField.text = ""
        }
    }
    .addDefaultWithTextField("Login") { textFields in
        textFields?.forEach { print($0.text) }
    }
    .addCancel("Back") { print("Cancelled") }
    .show() { print("Completion") }
```

## Advance

- Change default text of addOk() and addCancel()
``` swift
Alert.okButtonTitle = "Go"
Alert.cancelButtonTitle = "Back"
```


## Message
Please report bug to `@Sim_progra` at Twitter.
