# [ARCHIVE] ParseUI

# ParseUI has moved to [Parse-SDK-iOS-OSX](https://github.com/parse-community/Parse-SDK-iOS-OSX)
 
## Migration

### CocoaPods

Update your `Podfile`:

```ruby
pod 'Parse/UI'
```
### Carthage

Update your `Cartfile`:

```
github "ParsePlatform/Parse-SDK-iOS-OSX"
```
# ParseUI
## Overview

`ParseUI` is a collection of a handy user interface components to be used with Parse iOS SDK,  
which streamline and simplify logging in / signing up `PFUser`s and displaying a list of `PFObject`s.
 
## Getting Started

#### CocoaPods

`ParseUI` is available on CocoaPods.
Add the following to your `Podfile`:

```ruby
pod 'ParseUI'
```

#### Packaged Releases

You can download the latest release in a form of `ParseUI.framework` from our [Releases](https://github.com/ParsePlatform/ParseUI-iOS/releases) page.

#### Build from Source

`ParseUI` can also be built from source and supports Xcode subproject referencing.  
Follow these steps to build and run via source code:
- Download the source code via `git clone` or in an archive
- Run `pod install` in the repo root to download all the dependencies
- Open `ParseUI.xcworkspace`
- Build and Run `ParseUIDemo` target

## Components

#### PFLogInViewController
If you are using Parse to manage users in your mobile app, you are already familiar with the `PFUser` class.  
At some point in your app, you might want to present a screen to log in your `PFUser`.  
`ParseUI` provides a view controller that does exactly this:
```objective-c
PFLogInViewController *logInViewController = [[PFLogInViewController alloc] init];
logInViewController.delegate = self;
[self presentViewController:logInViewController animated:YES completion:nil];
```

#### PFSignUpViewController
If you are using `PFLogInViewController` with the `PFLogInFieldsSignUpButton` option enabled, 
you do not need to do any additional work to enable the sign up functionality.  
When your user taps on the sign up button on the log in screen - a sign up screen will appear.  
However, there are occasions where you might want to use the sign up screen independently of the log in screen.  
This is when the `PFSignUpViewController` comes in handy.
```objective-c
PFSignUpViewController *controller = [[PFSignUpViewController alloc] init];
controller.delegate = self;
[self presentViewController:controller animated:YES completion:nil];
```

#### PFQueryTableViewController
Data oriented iOS applications are mostly a collection of `UITableViewController`s and corresponding `UITableView`s.  
When using Parse, each cell of a `UITableView` typically represents data from a `PFObject`.  
`PFQueryTableViewController` is a sub-class of `UITableViewController` that provides a layer of abstraction that lets you easily display data from one of your Parse classes.
```objective-c
PFQueryTableViewController *controller = [[PFQueryTableViewController alloc] initWithStyle:UITableViewStylePlain className:@"Todo"];
[self presentViewController:controller animated:YES completion:nil];
```

#### PFImageView
Many apps need to display images stored in the Parse Cloud as `PFFile`s.  
However, to load remote images with the built-in `UIImageView` involves writing many lines of boilerplate code.  
`PFImageView` simplifies this task by abstracting away these parts.
```objective-c
PFImageView *imageView = [[PFImageView alloc] init];
imageView.image = [UIImage imageNamed:@"..."]; // placeholder image
imageView.file = (PFFile *)someObject[@"picture"]; // remote image
[imageView loadInBackground];
```

#### PFProductTableViewController
`PFProductTableViewController` is a subclass of `PFQueryTableViewController` that displays all IAP products in a table view. Some content apps, such as an app that sells comic books or video tutorials, may find it handy to use `PFProductTableViewController` to sell the products. By default, each cell is a product, and tapping on a cell initiates the purchase for the product. If the product has associated downloadable content, the download will start when the cell is selected and a progress bar is displayed to indicate the progress of the download.

## Learn More
- Check out [ParseUIDemo](https://github.com/ParsePlatform/ParseUI-iOS/tree/master/ParseUIDemo) project
- Read the [iOS Guides](https://parse.com/docs/ios_guide#ui/iOS)
- Browse official [API Reference](https://parse.com/docs/ios/api/)
- Follow few [tutorials](https://parse.com/tutorials/)

## Contributing
See the CONTRIBUTING file for how to help out.
