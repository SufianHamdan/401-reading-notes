# Read: 26 - Android Fundamentals

## Android fundamentals

**Application Fundamentals**
  * Android apps can be written using Kotlin, Java, and C++ languages.
  * Android SDK tools compile your code along with any data and resource files into an APK, an Android package, which is an archive file with an .apk suffix. One APK file contains all the contents of an Android app and is the file that Android-powered devices use to install the app.
  * Each Android app lives in its own security sandbox, protected by the following Android security features:
    - Android operating system - is a multi-user Linux system in which each app is a different user.
    - The system assigns each app a unique Linux user ID.
    - Each process has its own virtual machine.
    - Every app runs in its own Linux process.
  * Android system implements the principle of least privilege, which means that each app has access only to the components that it requires to do its work and no more. 
  * Ways for an app to share data with other apps and for an app to access system services:
    - It's possible to arrange for two apps to share the same Linux user ID, in which case they are able to access each other's files.
    - An app can request permission to access device data such as the device's location, camera, and Bluetooth connection.
  * App components - essential building blocks of an Android app. There are 4 different types:
    - Activities - the entry point for interacting with the user, and represents a single screen with a user interface. 
      * Key interections between system and app: keeping track of what the user currently cares about to ensure that the system keeps running the process that is hosting the activity, knowing that previously used processes contain things the user may return to, helping the app handle having its process killed so the user can return to activities with their previous state restored and providing a way for apps to implement user flows between each other, and for the system to coordinate these flows.
    - Services - a general-purpose entry point for keeping an app running in the background for all kinds of reasons, and does not provide a user interface. Started services tell the system to keep them running until their work is completed. 
      * Bound services - run because some other app has said that it wants to make use of the service, and this is basically the service providing an API to another process.
    - Broadcast receivers - a component that enables the system to deliver events to the app outside of a regular user flow, allowing the app to respond to system-wide broadcast announcements, and does not provide a user interface, but you can create a status bar notification to alert the user when a broadcast event occurs.
    - Content providers - manages a shared set of app data that you can store in the file system, in a SQLite database, on the web, or on any other persistent storage location that your app can access. 
  * Activating components - three of the four components are activated by an asynchronous message called an intent.
    - Intents - bind individual components to each other at runtime, and are created with an Intent object, which defines a message to activate either a specific component or a specific type of component.
    - Content providers are not activated by intents, but instead by a request from a ContentResolver, which handles all direct transactions with the content provider so that the component that's performing transactions with the provider doesn't need to and instead calls methods on the ContentResolver object.
  * Manifest file - before the Android system can start an app component, the system must know that the component exists by reading the app's manifest file, AndroidManifest.xml. 
    - Manifest declares the app's components. Elements used for declaring components: `<activity>`, `<service>`, `<receiver>`, and `<provider>`. 
    - It identifies any user permissions the app requires.
    - It declares the minimum API Level required by the app, based on which APIs the app uses.
    - It declares hardware and software features used or required by the app.
    - It declares API libraries the app needs to be linked against.
    - Can declare an intent filter for your component by adding an `<intent-filter>` element as a child of the component's declaration element.
  * App resources 
    - Android app is composed of more than just code—it requires resources that are separate from the source code, such as images, audio files, and anything relating to the visual presentation of the app. 
    - For every resource that you include, the SDK build tools define a unique integer ID, which you can use to reference the resource from your app code or from other resources defined in XML.
    - One of the most important aspects of providing resources separate from your source code is the ability to provide alternative resources for different device configurations. 
    - Android supports many different qualifiers for your alternative resources. 
      * Qualifier - a short string that you include in the name of your resource directories in order to define the device configuration for which those resources should be used. 