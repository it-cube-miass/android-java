Before any work can begin on the development of an Android application, the first step is to configure a computer system to act as the development platform. This involves a number of steps consisting of installing the Android Studio Integrated Development Environment (IDE) which also includes the Android Software Development Kit (SDK) and OpenJDK Java development environment. 

This chapter will cover the steps necessary to install the requisite components for Android application development on Windows, macOS and Linux based systems.

## System Requirements
Android application development may be performed on any of the following system types: 
- Windows 7/8/10 (32-bit or 64-bit though the Android emulator will only run on 64-bit systems) 
- macOS 10.10 or later (Intel based systems only) 
- ChromeOS device with Intel i5 or higher and minimum 8GB of RAM 
- Linux systems with version 2.19 or later of GNU C Library (glibc) 
- Minimum of 4GB of RAM (8GB is preferred) 
- Approximately 4GB of available disk space 
- 1280 x 800 minimum screen resolution

## Downloading the Android Studio Package
Most of the work involved in developing applications for Android will be performed using the Android Studio environment. The content and examples in this book were created based on Android Studio version 3.6 using the Android 10.0 (Q) API 29 SDK which, at the time writing are the current versions. 

Android Studio is, however, subject to frequent updates so a newer version may have been released since this book was published. 

The latest release of Android Studio may be downloaded from the primary download page which can be found at the following URL: [https://developer.android.com/studio/index.html](https://developer.android.com/studio/index.html) 

If this page provides instructions for downloading a newer version of Android Studio it is important to note that there may be some minor differences between this book and the software. A web search for Android Studio 3.6 should provide the option to download the older version in the event that these differences become a problem. Alternatively, visit the [https://developer.android.com/studio/archive](https://developer.android.com/studio/archive) 

## Installing Android Studio 
Once downloaded, the exact steps to install Android Studio differ depending on the operating system on which the installation is being performed.

### Installation on Windows
Locate the downloaded Android Studio installation executable file (named ```android-studio-ide-<version>-windows.exe```) in a Windows Explorer window and double-click on it to start the installation process, clicking the Yes button in the User Account Control dialog if it appears. 

Once the Android Studio setup wizard appears, work through the various screens to configure the installation to meet your requirements in terms of the file system location into which Android Studio should be installed and whether or not it should be made available to other users of the system. When prompted to select the components to install, make sure that the **Android Studio** and **Android Virtual Device** options are all selected.

Although there are no strict rules on where Android Studio should be installed on the system, the remainder of this book will assume that the installation was performed into ```C:\Program Files\Android\Android Studio``` and that the Android SDK packages have been installed into the user’s ```AppData\Local\Android\sdk``` sub-folder. Once the options have been configured, click on the Install button to begin the installation process. 

On versions of Windows with a Start menu, the newly installed Android Studio can be launched from the entry added to that menu during the installation. The executable may be pinned to the task bar for easy access by navigating to the ```Android Studio\bin``` directory, right-clicking on the executable and selecting the Pin to Taskbar menu option. Note that the executable is provided in 32-bit ( studio ) and 64-bit ( studio64 ) executable versions. If you are running a 32-bit system be sure to use the studio executable.

