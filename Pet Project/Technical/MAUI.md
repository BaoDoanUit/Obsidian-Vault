#### Overview
<mark style="background: transparent;">.NET for Android, .NET for iOS, .NET for macOS, and Windows UI 3 (WinUI 3) library have access to the same .NET base class library (BCL)  [[MVVM Pattern]]</mark> <mark style="background: transparent;">![[MAUI-1.png]]
![[MAUI-2.png]]</mark>

##### What .NET MAUI provides 
1) .NET MAUI provides a collection of controls:
- An elaborate layout engine for designing pages.
- Multiple page types for creating rich navigation types, like drawers.
- Support for data-binding, for more elegant and maintainable development patterns.
- The ability to customize handlers to enhance the way in which UI elements are presented.
- Cross-platform APIs for accessing native device features. These APIs enable apps to access device features such as the GPS, the accelerometer, and battery and network states. For more information, see Cross-platform APIs for device features.
- Cross-platform graphics functionality, that provides a drawing canvas that supports drawing and painting shapes and images, compositing operations, and graphical object transforms.
- A single project system that uses multi-targeting to target Android, iOS, macOS, and Windows. For more information, see .NET MAUI Single project.
- .NET hot reload, so that you can modify both your XAML and your managed source code while the app is running, then observe the result of your modifications without rebuilding the app. For more information, see .NET hot reload.

2) Cross-platform APIs for device features
- .NET MAUI provides cross-platform APIs for native device features. 
- Access to sensors, such as the accelerometer, compass, and gyroscope on devices.
- Ability to check the device's network connectivity state, and detect changes.
- Provide information about the device the app is running on.
- Copy and paste text to the system clipboard, between apps.
- Pick single or multiple files from the device.
- Store data securely as key/value pairs.
- Utilize built-in text-to-speech engines to read text from the device.
- Initiate browser-based authentication flows that listen for a callback to a specific app registered URL.

##### Customize the app shell
These files help get the .NET MAUI app configured and running. Each file serves a different purpose, described below:
1) MauiProgram.cs
- This is a code file that bootstraps your app. The code in this file serves as the cross-platform entry point of the app, which configures and starts the app. The template startup code points to the App class defined by the App.xaml file.
2) App.xaml and App.xaml.cs
- Just to keep things simple, both of these files are referred to as a single file. There are generally two files with any XAML file, the .xaml file itself, and a corresponding code file that is a child item of it in the Solution Explorer. The .xaml file contains XAML markup and the code file contains code created by the user to interact with the XAML markup.
- The App.xaml file contains app-wide XAML resources, such as colors, styles, or templates. The App.xaml.cs file generally contains code that instantiates the Shell application. In this project, it points to the AppShell class.
3) AppShell.xaml and AppShell.xaml.cs
- This file defines the AppShell class, which is used to define visual hierarchy of the app.
4) MainPage.xaml and MainPage.xaml.cs
- This is the startup page displayed by the app. The MainPage.xaml file defines the UI (user interface) of the page. MainPage.xaml.cs contains the code-behind for the XAML, like code for a button click event.
##### Resources
[Resources for learning .NET MAUI)[https://learn.microsoft.com/en-us/dotnet/maui/get-started/resources?view=net-maui-7.0]

##### Planning for reading document

