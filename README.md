[![Project Status](http://opensource.box.com/badges/active.svg)](http://opensource.box.com/badges)
[![Build Status](https://api.travis-ci.org/box/box-ios-content-sdk.svg)](https://travis-ci.org/box/box-ios-content-sdk)

Box iOS SDK
===================

This SDK makes it easy to use Box's [Content API](https://developers.box.com/docs/) in your iOS projects.

Developer Setup
---------------
* Ensure you have the latest version of [Xcode](https://developer.apple.com/xcode/) installed.
* We encourage you to use [Carthage] (https://github.com/Carthage/Carthage#installing-carthage) to manage dependencies. Minimal supported version for Carthage is 0.22.0.

Quickstart
----------
Step 1: Install Carthage

[First, install Carthage] (https://github.com/Carthage/Carthage#installing-carthage)

After Carthage is installed, run the following command
 
```
carthage update --platform iOS

```
Step 2: Import the built framework from Carthage/Build/iOS to your project. For more detailed instructions please see the official documentation for [Carthage] (https://github.com/Carthage/Carthage#getting-started)

```objectivec
@import BoxContentSDK;
```
Step 3: Set the Box Client ID and Client Secret that you obtain from [creating your app](doc/Setup.md). 
```objectivec
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
  // The UIApplicationDelegate is a good place to do this.
  [BOXContentClient setClientID:@"your-client-id" clientSecret:@"your-client-secret"];
}
```
Step 4: Authenticate a User
```objectivec
// This will present the necessary UI for a user to authenticate into Box
[[BOXContentClient defaultClient] authenticateWithCompletionBlock:^(BOXUser *user, NSError *error) {
  if (error == nil) {
    NSLog(@"Logged in user: %@", user.login);
  }
} cancelBlock:nil];
```

Sample App
----------
A sample app can be found in the [BoxContentSDKSampleApp](../../tree/master/BoxContentSDKSampleApp) folder. The sample app demonstrates how to authenticate a user, and manage the user's files and folders.

To execute the sample app:
Step 1: Install Pods
```
cd BoxContentSDKSampleApp
pod install
```
Step 2: Open Workspace
```
open BoxContentSDKSampleApp.xcworkspace
```

Tests
-----
Tests can be found in the 'BoxContentSDKTests' target. [Use Xcode to execute the tests](https://developer.apple.com/library/ios/recipes/xcode_help-test_navigator/RunningTests/RunningTests.html#//apple_ref/doc/uid/TP40013329-CH4-SW1). Travis CI will also execute tests for pull requests and pushes to the repository.

Documentation
-------------
You can find guides and tutorials in the `doc` directory.

* [App Setup](doc/Setup.md)
* [Authentication](doc/Authentication.md)
* [Developer's Edition (App Users)](doc/AppUsers.md)
* [Files](doc/Files.md)
* [Folders](doc/Folders.md)
* [Metadata](doc/metadata.md)
* [Comments](doc/Comments.md)
* [Collaborations](doc/Collaborations.md)
* [Events](doc/Events.md)
* [Search](doc/Search.md)
* [Users](doc/Users.md)


Contributing
------------
See [CONTRIBUTING](CONTRIBUTING.md) on how to help out.


Copyright and License
---------------------
Copyright 2015 Box, Inc. All rights reserved.

 
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

  http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
