# Multi-Party RTC Web App using C# and Web Toolkit

The Sample Web App demonstrates the use of APIs to develop basic Multi-Party RTC (Real Time Communication) Application. The main motivation behind this application is to demonstrate usage of APIs and allow developers to ramp up on app by hosting on their own devices instead of directly using servers.

RTC Applications run natively on supported set of web browsers without any additional plugin downloads.

This basic Multi-Party RTC Application is generated using HTML, CSS, Bootstrap, JavaScript, jQuery, C# and EnxRtc (Web Toolkit).

>The details of the supported set of web browsers can be found here:
https://doc.smartflomeet.ttns.in/developer/video/browser-compatibility-video/


## 1. Important!

When developing a Client Application with EnxRtc.js make sure to include the updated EnxRtc.js polyfills for RTCPeerConnection and getUserMedia. Otherwise your application will not work in web browsers.


## 2. Installation

### 2.1 Pre-Requisites

#### 2.1.1 App Id and App Key 

* Create your Application
* Get your App ID and App Key
* Clone this Repository `git clone https://github.com/smartflomeet/Multiparty-Video-Calling-C-Sharp-Application --recursive`
### Please note `--recursive` option. Repo should be cloned recursively to download `client` app. 

#### 2.1.2 SSL Certificates

The Application needs to run on https. So, you need to use a valid SSL Certificate for your Domain and point your application to use them.

However you may use self-signed Certificate to run this application locally. There are many Web Sites to get a Self-Signed Certificate generated for you, Google it. Few among them are:

* https://letsencrypt.org/
* https://www.sslchecker.com/csr/self_signed
* https://www.akadia.com/services/ssh_test_certificate.html  

As you have Certificate or created a Self-Signed Certificate, create a directory "certs" under your Sample Web App Directory. Copy your Certificate files (.key and .crt files)  to this directory. 

#### 2.1.3 Configure

Before you can run this application, configure the Service by editing `appsettings.json` file to use your app ID and app key:
``` 
"App": {
    "API_URL": "https://api.smartflomeet.ttns.in/v1/",
    "APP_ID": "YOUR_APP_ID",
    "APP_KEY": "YOUR_APP_KEY"
}
```


### 3 List of API endpoints exposed by the application

* POST https://yourdomain.com:{PORT}/api/create-room                 - It creates Room for Video Communication
* GET  https://yourdomain.com:{PORT}/api/get-room/?roomId={roomId}   - Get details of the room {roomId} created by calling /api/create-room 
* POST https://yourdomain.com:{PORT}/api/create-token                - Create token for Video Communication
    Params -
    ```
    {
        "name": "XXXX",      // Name of the user who is creating token to join session
        "role": "XXXX",      // Role of User. Values: moderator, participant (All in lowercase)
        "user_ref": "XXXX",  // User ID or Reference. You may use it from your Information System. Post Call Reports include this data for your reference/reporting
        "roomId": "XXXX"     // room id created by calling /api/create-room 
    }
    ```


## 4. Server API

Server API is a Rest API service meant to be called from Partners' Application Server to provision video enabled
meeting rooms. API Access is given to each Application through the assigned App ID and App Key. So, the App ID and App Key
are to be used as Username and Password respectively to pass as HTTP Basic Authentication header to access Server API.

For this application, the following Server API calls are used:
- https://doc.smartflomeet.ttns.in/developer/video-api/server-api/rooms-route/#create-room - To create a room
- https://doc.smartflomeet.ttns.in/developer/video-api/server-api/rooms-route/#get-rooms - To get list of Rooms
- https://doc.smartflomeet.ttns.in/developer/video-api/server-api/rooms-route/#get-room-info - To get information of the given Room
- https://doc.smartflomeet.ttns.in/developer/video-api/server-api/rooms-route/#create-token - To create Token for the given Room

To know more about Server API, go to:
https://doc.smartflomeet.ttns.in/developer/video-api/server-api/


## 6. Client API

Client End Point Application uses Web Toolkit EnxRtc.js to communicate with Servers to initiate and manage RTC Communications.

To know more about Client API, go to:
https://doc.smartflomeet.ttns.in/developer/video-api/client-api/
