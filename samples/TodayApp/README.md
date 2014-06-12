
##Today Example App

 This Gear app authenticates the user and sends user's Today's meetings to the watch from Salesforce Calendar. 

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

Also there are several "<b>Gotchas</b>" along the way that you need to be aware of before doing anything.

So here are the steps:
####STEP 0
If something doesn't work, please go through the 'gotchas' section below.

####STEP 1

Watch the following videos from Samsung to learn about how to setup your environment and also learn how the whole architecture work. Also follow the steps in the video to setup your environment.

1.  <a href="http://www.youtube.com/watch?v=gYwu4PihSCU" target="_blank">Hello, Gear! - Gear Pre-development Preparation 01</a>
2.   <a href="http://www.youtube.com/watch?v=VzoUeBS71jQ&index=5&list=PL7PfK8Mp1rLGhuYZMUfJv25zLaCtjx3VC" target="_blank">How to create integrated Gear Application Part01</a>
3.    <a href="http://www.youtube.com/watch?v=QDqhvbDEO-I&list=PL7PfK8Mp1rLGhuYZMUfJv25zLaCtjx3VC&index=5" target="_blank">How to create integrated Gear Application Part02</a>
4.     <a href="http://www.youtube.com/watch?v=SFz3n49QUCs&index=6&list=PL7PfK8Mp1rLGhuYZMUfJv25zLaCtjx3VC" target="_blank">How to create integrated Gear Application Part03</a>

####STEP 2 (Android App)
The above videos shows you how to setup the environment. Once that's done, clone this github project and go to `samples` directory. (Jump to step 5 if the connection b/w Tizen emulator and Android device is working based on the steps in the video)

1. Import `TodayAnrdoidApp` into ADT (Android Development Toolkit).
	- `File > Import > Android > Existing Android Code Into Workspace > TodayAnrdoidApp folder`
2. Also Import `SalesforceSDK` into ADT
	-  `TodayAndroidApp` depends on `SalesforceSDK`, so we need to add it as a dependency. To do that `Right click on "TodayAndroidApp" in Project Explorer > Properties > Android > "Library"- section > Click on Add and Add `SalesforceSDK` as dependency.
	
3. Connect a compitable Samsung phone/tablet. (note: Android emulator won't work)
4. Install three .apk files that were mentioned in the videos using `adb` tool. This  installs a test app on the Samsung device to test connection between Samsung device and Tizen emulator.
   - `adb` tool comes with Android SDK.  It is located in `path-to-your-android-sdk-folder/build-tools/adb`
   - Run the following from the terminal(in the same order):
   -  `adb -d install path-to-downloaded-Applications_for_Emulator-folder/SAccessoryService_Emul.apk ` 
   - `adb -d install path-to-downloaded-Applications_for_Emulator-folder/SAFTCore_Emul.apk` 
   -  `adb -d install path-to-downloaded-Applications_for_Emulator-folder/HostManagerForEmul.apk` 
5. Run `adb -d forward tcp:8230 tcp:8230` from the terminal  (assumes adb is in your PATH). This starts the connection to actually work.
6.  Right click on the `TodayAnrdoidApp` project > Run As > Run As Android Application. 
7.  You should see the app open on real Samsung device and see Salesforce login screen.
8.  Go ahead and login to Salesforce.
9.  You should now see a sample app with few buttons to test Salesforce connection from Android.
10.  At this point your android app has started and also started Samsung service to talk to Tizen watch in the background.


###STEP 3 (Tizen App)
1. Import `TodayTizenApp` into Tizen editor.
 	- `File > Import > General > Existing Projects To Workspace > TodayTizenApp folder`
2. Create an emulator (Be sure to watch the video to know how to do that).
	 - Note that emulator takes a long time to startup.
 	 - You need to have adb port forwarding `adb -d forward tcp:8230 tcp:8230` done BEFORE emulator startups.
3.  Test the connection by opening 'HostManagerForEmul' app. It should show `Connected`. If it is still showing `disconnected`, you will need to restart the emulator.
4.  If you are seeing 'Connected' in the 'HostManagerForEmul' example app, you are ready to try out hte `TodayTizenApp` app. 
  	- Right click on the `TodayTizenApp` project > Run As > Run As Tizen Web Application. 
  	


  
###STEP 4 (Running the app on a watch emulator + real Samsung Phone")


1. Transport property in the protocol file needs to be "Wifi" for development / testing in both Android and Tizen projects. So set  `transport` value is `TRANSPORT_WIFI` in both `TodayTizenApp > res > xml > accessory.xml` and 'TodayAndroidApp > res > xml > accessory.xml` files as below.

```
       <supportedTransports>
                <transport type="TRANSPORT_WIFI" />
            </supportedTransports>

```

2. Build Tizen app from: `Project > Build Project` or `cmd + shift + b`. This will generate a new `Tizen.wgt`
3.  Copy `Tizen.wgt` from Tizen IDE into Android project under `TodayAndroidApp > assets` folder.

PS: Make sure you have few meetings created for the day with few attendees, location etc. 
 	
 	

##Step 5 (Running the app on "REAL" watch + REAL Samsung Phone)
#### 5.1 Get Samsung signed certificates and install it into Tizen IDE. 
1. Watch this Samsung video <a href="http://www.youtube.com/watch?v=1olrFCyjyaM&index=2&list=PL7PfK8Mp1rLGhuYZMUfJv25zLaCtjx3VC" target="_blank">"Generating Certification" - Gear Pre-development Preparation 02</a>
2. Some steps are missing in the video, so here are the high level steps:
	- Connect your real watch to your laptop via usb.
	- In Tizen editor, you will see the device under `Connection Explorer`
	- Right click on the device > Properties and get `DUID` (Device ID)
	- Click on `Generate Certificate` on the toolbar (red icon)
	- Fill out the form and enter `DUID` (you can add multiple) and generate certificate request xml file.
	-  **Secure PGP Mail: We need to send the certificate request to gear2.sec@samsung.com that's PGP encrypted**
	    - We need a Mail.app plugin called <a href="https://gpgtools.org/" target="_blank">https://gpgtools.org/</a> 
	    - Note - PGP mail can't be sent via web emails.
	    - Once you install gpgtool, create a public + private key.
	    - gpgtool will ask for an email. **Make sure to use the SAME EMAIL that you will be using to send mail to Samsung in Mail.app**. 
	    - Export your public key to some folder
	    - Download Samsung's public key from <a href="https://keyserver.pgp.com" target="_blank">https://keyserver.pgp.com</a> by entering `gear2.sec@samsung.com` email.
	    - Import Samsung's public key to PGP tool.
	    - Restart Mail.app
	    - Open Mail.app, Enter email: gear2.sec@samsung.com, and attach request.xml and your publickey. Click Encrypt.
	    - Send Mail
	    - After several hours you will get an email from Samsung w/ registration.xml file.
	    - Import that to Tizen IDE.
	    - **Test** :You can test by trying to run any demo or this app directly on the watch. This simply shows that you can now install apps on the watch.
	    
	    
#### Check out some of the pics related to getting certificate:
**GPG Mail plugin tool (https://gpgtools.org/)	**  
![image](https://raw.githubusercontent.com/developerforce/WearablePack-SamsungGear2/master/images/gpg-tool.png)	


**GPG repository**
![image](https://raw.githubusercontent.com/developerforce/WearablePack-SamsungGear2/master/images/pgp-server.png)

**Sending Email to Samsung**
![image](https://raw.githubusercontent.com/developerforce/WearablePack-SamsungGear2/master/images/sending-email.png)

**Registration mail back from Samsung**
![image](https://raw.githubusercontent.com/developerforce/WearablePack-SamsungGear2/master/images/registration-from-samsung.png)

#### 5.2 Make the following changes to the code + real device
1.  **Make sure to uninstall all .apk files that you might have installed for testing / development**
1. Transport property in the protocol file needs to be "BT" (bluetooth) in both Android and Tizen projects. So set  `transport` value is `TRANSPORT_BT` in both `TodayTizenApp > res > xml > accessory.xml` and 'TodayAndroidApp > res > xml > accessory.xml` files as below.

```
       <supportedTransports>
                <transport type="TRANSPORT_BT" />
            </supportedTransports>

```

2. Build Tizen app from: `Project > Build Project` or `cmd + shift + b`. This will generate a new `Tizen.wgt`
3.  Copy `Tizen.wgt` from Tizen IDE into Android project under `TodayAndroidApp > assets` folder.
5.  Install real `Samsung Gear Manager` from `Samsung Appstor`.
6.  Pair the Phone with gear and make sure it is ready.





###Gotchas
1. To test with emulator, make sure to UNINSTALL `Samsung Gear Manager` app if you have already downloaded it from Samsung store. The 3 apk files you installed actually installs an emulator version of `Samsung Gear Manager` <b>which will conflict with the real</b> `Samsung Gear Manager`
2. Make sure you done have adb port forwarding `adb -d forward tcp:8230 tcp:8230` done <b>BEFORE the emulator startups</b>.
3. You will need to kill the emulator and restart it every time you disconnect your Samsung device.
4. It is good to have the latest Samsung device and Android SDK.
5. If you are unable to unzip 'Applications For Emulator' zip file on mac(that contains 3 .apk files), see <a href="http://developer.samsung.com/forum/board/thread/view.do?boardName=SDK&messageId=264778&startId=zzzzz~&searchType=ALL&searchText=zip" target="_blank">this forum post</a> 
6. Android Emulator wont work - so please use a real Samsung device.
7. To interact with the emulator using mouse pointer, <b>first press 'command' button</b> then use the mouse.
8. You need to uninstall everything and reinstall real `samsung gear manager` if you are pairing the phone with real gear watch. (you need emulator version if you are pairing w/ Gear emulator - see #1)
9. GPG Mail - Make sure to create your public key using the same email that your Mail.app uses and send email to Samsung using from that email.


 	 
##Code Highlights (Android)

* The code below in MainActivity starts Tizen service.

```
		Intent intent = new Intent(this, HelloAccessoryProviderService.class);
    	startService(intent);
```
*   SOQL - This is the SOQL used to get meeting & attendees information.

```

		private String soql = "SELECT Id, Subject, AccountId, ActivityDateTime, WhatId,What.Name,What.type, WhoId, Who.Id,"
				+ "Who.FirstName,Who.LastName, Description, DurationInMinutes, Location,"
				+ " (SELECT EventId, RelationId, Relation.Name,Relation.Email FROM EventRelations) "
				+ "from Event Where ActivityDateTime = Today";
				
```

* The code below provides a way to perform SOQL directly from Samsung service.

```
		ClientManager cm = new ClientManager(getApplicationContext(),
						SalesforceSDKManager.getInstance().getAccountType(),
						SalesforceSDKManager.getInstance().getLoginOptions(),
						true);
				client = cm.peekRestClient();
```

* SOQL response is sent back to the watch using the following code

```
		public void sendMsgToWatch(String msg) {
			final String message = msg;
			final HelloAccessoryProviderConnection uHandler = mConnectionsMap
					.get(Integer.parseInt(String.valueOf(mConnectionId)));
			if (uHandler == null) {
				Log.e(TAG,
						"Error, can not get HelloAccessoryProviderConnection handler");
				return;
			}
			new Thread(new Runnable() {
				public void run() {
					try {
						uHandler.send(HELLOACCESSORY_CHANNEL_ID,
								message.getBytes());
					} catch (IOException e) {
						e.printStackTrace();
					}
				}
			}).start();
		}
		
```

* When the user opens the app on the watch the following `onReceive` method is called by Samsung SDK.

```
		public void onReceive(int channelId, byte[] data) {
			Log.d(TAG, "onReceive");
			//When Watch asks.. call salesforce and return results
			makeRESTCallToSalesforce();
		}
```

* Channel ID is used to send/receive messages between watch and the android app. So you must have the same channel number on both watch and the android app.

```
	public static final int HELLOACCESSORY_CHANNEL_ID = 104;
```



##Code Highlights (Tizen)
* onconnect is called when the Tizen connects to Android. It also calls `fetch` custom function. 

```
var agentCallback = {
	onconnect : function(socket) {
		SASocket = socket;
		// alert("HelloAccessory Connection established with RemotePeer");
		createHTML("startConnection");

		SASocket.setSocketStatusListener(function(reason) {
			console.log("Service connection lost, Reason : [" + reason + "]");
			disconnect();
		});

		// fetch data..
		fetch(ACTION_FETCH_MEETINGS);
	},
	onerror : onerror
};
```

* `fetch` sends a message to Tizen and asks it to get list of meetings using the same channel Id (104 in this case). And also provides `onreceive` function as a callback function.

```
function fetch(actionName) {
	try {
		SASocket.setDataReceiveListener(onreceive);
		SASocket.sendData(CHANNELID, actionName);
	} catch (err) {
		console.log("exception [" + err.name + "] msg[" + err.message + "]");
	}
}
``` 

* `onreceive` simply updates the html of the app.

```

//Receive data from Android app
function onreceive(channelId, data) {
	updateMeetings(data);
}
```

## TODO
** As mentioned in the video, the example app only has code for the whole interaction b/w Android and the Watch and Salesforce, get list of meetings, get meeting details, list of attendees etc.***
####Things to do
- Add code to get Attendee details
- Send Email
- Log a call






