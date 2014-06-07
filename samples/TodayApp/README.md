
##Today Example App

 This Gear app authenticates the user and sends  user's Today's meetings to the watch from Salesforce Calendar. 

  <img src="https://raw.githubusercontent.com/developerforce/WearablePack-SamsungGear2/master/images/tizen-gif2.gif?token=626337__eyJzY29wZSI6IlJhd0Jsb2I6ZGV2ZWxvcGVyZm9yY2UvV2VhcmFibGVQYWNrLVNhbXN1bmdHZWFyMi9tYXN0ZXIvaW1hZ2VzL3RpemVuLWdpZjIuZ2lmIiwiZXhwaXJlcyI6MTQwMjcwMTMwMn0%3D--a6836c43ba95027eb793aaf8cccf7f5e263c39a4"/>  
  </img>

##Architecture

Because of the way Samsung Gear 2 works, you will be working with two apps: 

1. An Android App that helps user authenticate with Salesforce and then acts like a middle man between Gear Watch and Salesforce. 
2. A Tizen web app that communicates with the android app and displays Salesforce info (in this case meeting details) on the watch.

<p align="center">

  <img src="https://raw.githubusercontent.com/developerforce/WearablePack-SamsungGear2/master/images/samsung-watch-and-phone-3.png?token=626337__eyJzY29wZSI6IlJhd0Jsb2I6ZGV2ZWxvcGVyZm9yY2UvV2VhcmFibGVQYWNrLVNhbXN1bmdHZWFyMi9tYXN0ZXIvaW1hZ2VzL3RpemVuLWdpZjIuZ2lmIiwiZXhwaXJlcyI6MTQwMjcwMTMwMn0%3D--a6836c43ba95027eb793aaf8cccf7f5e263c39a4"/>  
  </img>
</p>