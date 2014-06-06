## Salesforce Wearable Pack for Samsung Gear 2
<p align='center'>  <img src="https://raw.githubusercontent.com/developerforce/WearablePack-SamsungGear2/master/images/samsung-watch-and-phone.png?token=626337__eyJzY29wZSI6IlJhd0Jsb2I6ZGV2ZWxvcGVyZm9yY2UvV2VhcmFibGVQYWNrLVNhbXN1bmdHZWFyMi9tYXN0ZXIvaW1hZ2VzL3NhbXN1bmctd2F0Y2gtYW5kLXBob25lLnBuZyIsImV4cGlyZXMiOjE0MDI2OTc5Nzl9--03a97ec125422574dd1bf6998b61a9c6be1b2920" width="75%" />        </p>
This Wearable Pack is for <a href="http://developer.samsung.com/samsung-gear" target="_blank"> Samsung Gear 2</a> Wearable and includes an architecture overview article along with a sample application to get you started building applications which integrate Salesforce with Samsung Gear 2.
Samsung Gear <a href="http://www.samsung.com/global/microsite/gear/gear2_design.html" target="_blank">wearables</a> like Gear 2, Gear 2 neo etc all need a 'host' android app through which they communicate with the external World. 
One caveat is that these android apps must be running in a compitable Samsung phones or tablets and won't work on devices from other manufacturers like Nexus or LG.

Below shows the list of compatible devices. ```

Samsung Gear is compatible with 17 types of device models :
Samsung Galaxy S5 / Galaxy Grand 2 / Galaxy Note 3 / Galaxy Note 3 Neo / Galaxy Note 2 / Galaxy S4 / Galaxy S3 / Galaxy S4 Zoom / Galaxy S4 Active / Galaxy S4 mini /
Galaxy Mega 6.3 / Galaxy Mega 5.8 / Galaxy Note 10.1 (2014 Edition) / Galaxy NotePRO (12.2) / Galaxy TabPRO (12.2/10.1/8.4)
* Compatible device models to be further expanded
* Device compatibility may vary by country.

Source: http://www.samsung.com/global/microsite/gear/gear2_features.html

``` 
##Samsung Gear 2 And Tizen OS
<p align='center'>
<a href="http://tizen.org" target="_blank"> 
  <img src="https://raw.githubusercontent.com/developerforce/WearablePack-SamsungGear2/master/images/tizen-logo.png?token=626337__eyJzY29wZSI6IlJhd0Jsb2I6ZGV2ZWxvcGVyZm9yY2UvV2VhcmFibGVQYWNrLVNhbXN1bmdHZWFyMi9tYXN0ZXIvaW1hZ2VzL3RpemVuLWxvZ28ucG5nIiwiZXhwaXJlcyI6MTQwMjY5OTUwMH0%3D--07da3d5e3a69067179645a9dd66eaa3d3c1d44dc" height="200px"/>  
  </img>
  </a>
  </p>
Samsung Gear 2 watch itself doesn't run Android Operating System. Instead it runs on Samsung's open-source <a href="http://tizen.org" target="_blank">Tizen OS</a> that's built in C++. Tizen OS allows people to build apps in either HTML5 or C++ (native). However Samsung Gear 2 only allows us to build HTML5 apps.

##Getting Started
Because of the way Samsung Gear 2 works, you will be building: 

1. An Android App that talks to Salesforce and authenticates user. 
2. A Tizen web app that communicates with the android app and displays info on the watch.




##Today App

<p align='center'>
  <img src="https://raw.githubusercontent.com/developerforce/WearablePack-SamsungGear2/master/images/tizen-gif2.gif?token=626337__eyJzY29wZSI6IlJhd0Jsb2I6ZGV2ZWxvcGVyZm9yY2UvV2VhcmFibGVQYWNrLVNhbXN1bmdHZWFyMi9tYXN0ZXIvaW1hZ2VzL3RpemVuLWdpZjIuZ2lmIiwiZXhwaXJlcyI6MTQwMjcwMTMwMn0%3D--a6836c43ba95027eb793aaf8cccf7f5e263c39a4""/>  
  </img>
</p>
To help you get started this repo comes with a sample app called "Today". It has a simple android app that does authentication and sends Salesforce user's "Today's meetings" to the watch from Salesforce Calendar. To get started, go through the instructions on the readme inside the sample app.


