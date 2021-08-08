# Read: 27 - Intents, Activities, and SharedPreferences

## Android Tasks and the Back Stack
**Understand Tasks and Back Stack**
  * Task - a collection of activities that users interact with when performing a certain job. 
  * Activities are arranged in a the back stack in the order in which each activity is opened. 
  * When apps are running simultaneously in a multi-windowed environment the system manages tasks separately for each window, and each window may have multiple tasks. 
  * The device Home screen is the starting place for most tasks. When the user touches an icon in the app launcher, that app's task comes to the foreground. If no task exists for the app, then a new task is created and the "main" activity for that app opens as the root activity in the stack. 
  * When the current activity starts another, the new activity is pushed on the top of the stack and takes focus. The previous activity remains in the stack, but is stopped. When an activity stops, the system retains the current state of its user interface. 
  * Activities in the stack are never rearranged, only pushed and popped from the stack or pushed onto the stack when started by the current activity and popped off when the user leaves.
  * A task is a cohesive unit that can move to the "background" when users begin a new task or go to the Home screen. 
  * The activities in the back stack are never rearranged,  if your app allows users to start a particular activity from more than one activity, a new instance of that activity is created and pushed onto the stack.
  * Managing Tasks - Android manages tasks and the back stack by placing all activities started in succession in the same task and in a "last in, first out" stack.
  * Launch modes allow you to define how a new instance of an activity is associated with the current task. 
    - Two ways to define different launch modes: Using manifest file or using intent flags.
    - Manifest file - when declaring an activity in your manifest file, you can specify how the activity should associate with a task using the <activity> element's launchMode attribute.
    - Intent flags - when starting an activity, you can modify the default association of an activity to its task by including flags in the intent that you deliver to startActivity().
  * Handling affinities - affinity indicates which task an activity prefers to belong to. Can modify the affinity for any given activity with the taskAffinity attribute of the <activity> element. The taskAffinity attribute takes a string value, which must be unique from the default package name declared in the <manifest> element, because the system uses that name to identify the default task affinity for the app.
  * Clearing the back stack - If the user leaves a task for a long time, the system clears the task of all activities except the root activity. When the user returns to the task again, only the root activity is restored. Activity attributes used to modify behavior: alwaysRetainTaskState, clearTaskOnLaunch, and finishOnTaskLaunch.
  * Starting a task - set up an activity as the entry point for a task by giving it an intent filter with "android.intent.action.MAIN" as the specified action and "android.intent.category.LAUNCHER" as the specified category. 

## Android SharedPreferences
**Save key-value data**
  * Use the SharedPreferences APIs when you have a relatively small collection of key-values that you'd like to save.
  *  SharedPreferences object - points to a file containing key-value pairs and provides simple methods to read and write them. Each SharedPreferences file is managed by the framework and can be private or shared.
  * Can create a new shared preference file or access an existing one by calling one of these methods:
    - getSharedPreferences() — use this if you need multiple shared preference files identified by name, which you specify with the first parameter. You can call this from any Context in your app.
    - getPreferences() — use this from an Activity if you need to use only one shared preference file for the activity. Because this retrieves a default shared preference file that belongs to the activity, you don't need to supply a name.
  * To write to a shared preferences file, create a SharedPreferences.Editor by calling edit() on your SharedPreferences. Pass the keys and values you want to write with methods such as putInt() and putString(). Then call apply() or commit() to save the changes. 
  * To retrieve values from a shared preferences file, call methods such as getInt() and getString(), providing the key for the value you want, and optionally a default value to return if the key isn't present. 