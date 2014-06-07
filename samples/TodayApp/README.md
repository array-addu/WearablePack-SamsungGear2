
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
 Watch the following videos from Samsung about how to setup your environment.
1. 