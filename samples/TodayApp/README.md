
##Today Example App

 This Gear app authenticates the user and sends  user's Today's meetings to the watch from Salesforce Calendar. 

  <img src="https://raw.githubusercontent.com/developerforce/WearablePack-SamsungGear2/master/images/tizen-gif2.gif?token=626337__eyJzY29wZSI6IlJhd0Jsb2I6ZGV2ZWxvcGVyZm9yY2UvV2VhcmFibGVQYWNrLVNhbXN1bmdHZWFyMi9tYXN0ZXIvaW1hZ2VzL3RpemVuLWdpZjIuZ2lmIiwiZXhwaXJlcyI6MTQwMjcwMTMwMn0%3D--a6836c43ba95027eb793aaf8cccf7f5e263c39a4"/>  
  </img>

##Architecture

Because of the way Samsung Gear 2 works, you will be working with two apps: 

1. An Android App that helps user authenticate with Salesforce and then acts like a middle man between Gear Watch and Salesforce. 
2. A Tizen <b>web</b> app that communicates with the android app and displays Salesforce info (in this case meeting details) on the watch.

<p align="center">

  <img src="https://raw.githubusercontent.com/developerforce/WearablePack-SamsungGear2/master/images/high-level-architecture.png?token=626337__eyJzY29wZSI6IlJhd0Jsb2I6ZGV2ZWxvcGVyZm9yY2UvV2VhcmFibGVQYWNrLVNhbXN1bmdHZWFyMi9tYXN0ZXIvaW1hZ2VzL2hpZ2gtbGV2ZWwtYXJjaGl0ZWN0dXJlLnBuZyIsImV4cGlyZXMiOjE0MDI3MDc5OTd9--3c7597a4a523059428f1b7478b0dddf0358e59cc"/>  
  </img>
</p>

##Getting Started With Gear 2 Development
Developing Gear 2 app involves lots of moving parts. There will be two Eclipse editors, one for Android and another, a Tizen version of Eclipse for Tizen app.

<img src="http://img-developer.samsung.com/contents/sd2/images/develop/post/20140224_gearsdk/sms_gear_03.jpg" />

Further there is a Tizen emulator, a real Samsung phone and several libraries that needs to be imported to get started.

Also there are several "Gotchas" along the way that you need to be aware of before doing anything.

So here are the steps:
####STEP 1

Watch the following videos from Samsung to learn about how to setup your environment and also learn how the whole architecture work. Also follow the steps in the video to setup your environment.

1.  <a href="http://www.youtube.com/watch?v=gYwu4PihSCU" target="_blank">Hello, Gear!" - Gear Pre-development Preparation 01</a>
2.   <a href="http://www.youtube.com/watch?v=VzoUeBS71jQ&index=5&list=PL7PfK8Mp1rLGhuYZMUfJv25zLaCtjx3VC" target="_blank">How to create integrated Gear Application Part01</a>
3.    <a href="http://www.youtube.com/watch?v=QDqhvbDEO-I&list=PL7PfK8Mp1rLGhuYZMUfJv25zLaCtjx3VC&index=5" target="_blank">How to create integrated Gear Application Part02</a>
4.     <a href="http://www.youtube.com/watch?v=SFz3n49QUCs&index=6&list=PL7PfK8Mp1rLGhuYZMUfJv25zLaCtjx3VC" target="_blank">How to create integrated Gear Application Part03</a>

####STEP 2 (Android App)
The above videos shows you how to setup the environment. Once that's done, clone this github project and go to `samples` directory.

1. Import `TodayAnrdoidApp` into ADT (Android Development Toolkit).
	- `File > Import > Android > Existing Android Code Into Workspace > TodayAnrdoidApp folder`
2. Connect a compitable Samsung phone/tablet. (note: Android emulator won't work)
3. Install 3 .apk files that were mentioned in the videos using `adb` tool. This  installs a test app on the Samsung device to test connection between Samsung device and Tizen emulator.
   - `adb` tool comes with Android SDK.  It is located in `path-to-your-android-sdk-folder/build-tools/adb`
   - Run the following from the terminal(in the same order):
   -  `adb -d install path-to-downloaded-Applications_for_Emulator-folder/SAccessoryService_Emul.apk ` 
   - `adb -d install path-to-downloaded-Applications_for_Emulator-folder/SAFTCore_Emul.apk` 
   -  `adb -d install path-to-downloaded-Applications_for_Emulator-folder/HostManagerForEmul.apk` 
4. Run `adb -d forward tcp:8230 tcp:8230` from the terminal  (assumes adb is in your PATH). This starts the connection to actually work.
5.  Right click on the `TodayAnrdoidApp` project > Run As > Run As Android Application. 
6.  You should see the app open on real Samsung device and see Salesforce login screen.
7.  Go ahead and login to Salesforce.
8.  You should now see a sample app with few buttons to test Salesforce connection from Android.
9.  At this point your android app has started and also started Samsung service to talk to Tizen watch in the background.


###STEP 3 (Tizen App)
1. Import `TodayTizenApp` into Tizen editor.
 	- `File > Import > General > Existing Projects To Workspace > TodayTizenApp folder`
2. Create an emulator (Be sure to watch the video to know how to do that).
	 - Note that emulator takes a long time to startup.
 	 - You need to have adb port forwarding `adb -d forward tcp:8230 tcp:8230` done BEFORE emulator startups.
3.  Test the connection by opening 'HostManagerForEmul' app. It should show `Connected`. If it is still showing `disconnected`, you will need to restart the emulator.
4.  If you are seeing 'Connected' in the 'HostManagerForEmul' example app, you are ready to try out hte `TodayTizenApp` app. 
  	- Right click on the `TodayTizenApp` project > Run As > Run As Tizen Web Application. 
  	
###Gotchas
1. Make sure to UNINSTALL `Samsung Gear Manager` app if you have already downloaded it from Samsung store. The 3 apk files you installed actually installs an emulator version of `Samsung Gear Manager` <b>which will conflict with the real</b> `Samsung Gear Manager`
2. Make sure you done have adb port forwarding `adb -d forward tcp:8230 tcp:8230` done BEFORE emulator startups.
3. You will need to kill the emulator and restart it every time you disconnect your Samsung device.
4. It is good to have the latest Samsung device and Android SDK.
5. If you are unable to unzip 'Applications For Emulator' zip file on mac(that contains 3 .apk files), see <a href="http://developer.samsung.com/forum/board/thread/view.do?boardName=SDK&messageId=264778&startId=zzzzz~&searchType=ALL&searchText=zip" target="_blank">this forum post</a> 
6. Android Emulator wont work - so please use real Samsung device.

  
###STEP 4 (Running the app)
At this point you should have both Tizen and Andriod app running. And you should see all your meeting details in the watch.

PS: Make sure you have few meetings created for the day with few attendees, location etc. 
 	 



