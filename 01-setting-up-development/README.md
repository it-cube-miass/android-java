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

### Installation on macOS
*comming soon*

### Installation on Linux
*comming soon*

## The Android Studio Setup Wizard
The first time that Android Studio is launched after being installed, a dialog will appear version. If you have settings from a previous version and would like to import them into the latest installation, select the appropriate option and location. Alternatively, indicate that you do not need to import any previous settings and click on the **OK** button to proceed. Next, the setup wizard may appear as shown in Figure 2-2 though this dialog does not appear on all platforms:

![Figure 2-2](https://i.ytimg.com/vi/3cYBfuphkuE/maxresdefault.jpg)

<!-- Прежде чем можно будет начать работу по разработке приложения для Android, необходимо настроить компьютерную систему, которая будет выступать в качестве платформы разработки. Это включает в себя ряд шагов, состоящих из установки интегрированной среды разработки Android Studio (IDE), которая также включает в себя Android Software Development Kit (SDK) и OpenJDK Java. В этой главе будут рассмотрены шаги, необходимые для установки необходимых компонентов для разработки приложений Android в системах на базе Windows, macOS и Linux.

## Системные требования

## Скачивание Android Studio
Большая часть работы по разработке приложений для Android будет выполняться в среде Android Studio. Содержимое и примеры в этом пособии были созданы на основе Android Studio версии 3.6 с использованием Android 8.0 (Oreo) API 26 SDK. Однако Android Studio часто обновляется, поэтому, когда вы читаете этот текст, могла быть выпущена более новая версия. Последнюю версию Android Studio можно загрузить с основной страницы загрузки, которую можно найти по следующему URL-адресу: [https://developer.android.com/studio/index.html](https://developer.android.com/studio/index.html)

Устанавливая более новую версию Android Studio, чем 3.6, важно отметить, что между этим пособием и программным обеспечением могут быть небольшие различия. Если эти различия станут проблемой, можно перейти по ссылке [https://developer.android.com/studio/archive](https://developer.android.com/studio/archive) и скачать необходимую версию Android Studio.

## Установка Android Studio
После загрузки, точные шаги по установке Android Studio различаются в зависимости от операционной системы, в которой выполняется установка.

### Установка под Windows

Найдите загруженный исполняемый файл установки Android Studio (с именем ```android-studio-ide-<version>-windows.exe```) в окне проводника Windows и дважды щелкните по нему, чтобы начать процесс установки, нажав кнопку **Yes** в диалоговом окне **User Account Control**, если оно появится. Как только появится мастер установки Android Studio, пройдите через различные экраны, чтобы настроить установку в соответствии с вашими требованиями с точки зрения расположения файловой системы, в которую должна быть установлена Android Studio, и того, следует ли сделать ее доступной для других пользователей системы. . Когда будет предложено выбрать компоненты для установки, убедитесь, что выбраны все параметры Android Studio и Android Virtual Device. Хотя нет строгих правил относительно того, гдеВ системе должна быть установлена Android Studio, в оставшейся части этой книги предполагается, что установка была выполнена в C: \ Program Files \ Android \ Android Studio и что пакеты Android SDK были установлены в пользовательский AppData \ Local \ Android \ подпапка sdk. После настройки параметров нажмите кнопку «Установить», чтобы начать процесс установки. В версиях Windows с меню «Пуск» недавно установленную Android Studio можно запустить из записи, добавленной в это меню во время установки. Исполняемый файл можно закрепить на панели задач для легкого доступа, перейдя в каталог Android Studio \ bin, щелкнув правой кнопкой мыши исполняемый файл и выбрав пункт меню «Закрепить на панели задач». Обратите внимание, чтоисполняемый файл предоставляется в 32-битной (studio) и 64-битной (studio64) версиях исполняемого файла. Если вы используете 32-битную систему, обязательно используйте исполняемый файл студии. -->
