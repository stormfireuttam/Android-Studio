# Android Activity Lifecycle

Activity in Android is one of the most important components of Android. It is the Activity where we put the UI of our application. So, if we are new to Android development then we should learn what an Activity is in Android and what is the lifecycle of an Activity. In this blog, we will learn about,

- What is an Activity in Android?
- What is the Activity Lifecycle?
- Real example use-cases of Activity Lifecycle.

## What is an Activity in Android?
Whenever we open an Android application, then you see some UI drawn over our screen. That screen is called an Activity. It is the basic component of Android and whenever you are opening an application, then we are opening some activity.

For example, when we open our Gmail application, then we see our emails on the screen. Those emails are present in an Activity. If we open some particular email, then that email will be opened in some other Activity.

When we all started with coding, we know about the main method from where the program begins execution. Similarly, in Android, Activity is the one from where the Android Application starts its process. Activity is one screen of the app's user interface. There is a series of methods that run in an activity.

There is a lifecycle associated with every Activity and to make an error-free Android application, we have to understand the lifecycle of Activity and write the code accordingly.

## What is the Activity Lifecycle?
To understand the activity lifecycle, consider an example of a human being. As human beings, we go through certain stages of our life starting from as a kid to a teenager. From an adult and then to an old person. These are the phases or states of life we go through.

Similarly, for Activity in Android, we go through state changes in the total duration of the activity.

An Android activity undergoes through a number of states during its whole lifecycle. The following diagram shows the whole Activity lifecycle:

<img src="https://s3.ap-south-1.amazonaws.com/mindorks-server-uploads/android_activity_lifecycle_mindorks_image.png"/>

The Activity lifecycle consists of 7 methods:

1. onCreate() : When a user first opens an activity than the first method that gets called is called as onCreate. It acts the same as a constructor of a class, then when an activity is instantiated then onCreate gets called.
2. onStart(): This method is called when an activity becomes visible to the user and is called after onCreate.
3. onResume(): It is called just before the user starts interacting with the application.
4. onPause():  It is called when the app is partially visible to the user on the mobile screen.
5. onStop(): It is called when the activity is no longer visible to the user.
6. onRestart(): It is called when the activity in the stopped state is about to start again.
7. onDestroy(): It is  called when the activity is cleared from the application stack.
So, these are the 7 methods that are associated with the lifecycle of an activity.

## Real example use-cases of Activity Lifecycle
Now, let's see real-life use-cases to understand the lifecycle for an activity.

***UseCase 01.***

When we open the activity for the first time, the sequence of state change it goes through is,
```
onCreate -> onStart -> onResume
```
After this point, the activity is ready to be used by the user.

***UseCase 02.***

Now, let's say we are minimizing the app by pressing the home button of the phone. The state changes it will go through is,
```
onPause -> onStop
```
***UseCase 03.***

When we are moving to and from between activities, let's say Activity A and Activity B. So, we will break it down in steps.

First, it opened Activity A, where the following states are called initially,
```
onCreate -> onStart -> onResume
```
Then let's say on a click of a button we opened Activity B. While opening Activity B, first, onPause will be called for Activity A and then,
```
onCreate -> onStart -> onResume
```
will be called for Activity B. Then to finish this off, onStop of Activity A will be called and finally, Activity B would be loaded.

Now, when we press the back button from Activity B to Activity A, then first,onPause of Activity B is called and then,
```
onRestart -> onStart -> onResume
```
gets called for Activity A and it is displayed to the user. Here you can see onRestart gets called rather then onCreate as it is restarting the activity and not creating it.

Then after onResume of Activity A is called then,
```
onStop -> onDestroy  
```
is called for Activity B and hence the activity is destroyed as the user has moved to Activity A.

***UseCase 04.***

Pressing the lock button while activity is on then,
```
onPause -> onStop 
```
gets called and when we reopen the app again,
```
onRestart -> onStart -> onResume
```
gets called.

***UseCase 05.***

When we kill the app from the recent app's tray,
```
onPause -> onStop -> onDestroy 
```
it gets called. Here you can see we are getting the onDestroy state getting called as we are killing the instance of the activity.

When we now reopen the activity, it will call onCreate and not onRestart to start the activity.

***UseCase 06.***

Consider a use-case where we need to ask permission from the user. Majority of the times we do it in onCreate.

Now, an edge case here is let's say we navigate to a phone's Settings app and deny the permission there, and then I came back to the initial app's activity. Here, onCreate would not be called.

So, our permission check could not be satisfied here. To overcome this, onStart is the best place to put your permission check as it will handle the edge cases.

<hr/>

Credits : [Mindorks](https://blog.mindorks.com/android-activity-lifecycle)
