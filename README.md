jquery-cordova-oauth2
=====================

__jQuery plugin for doing Oauth2 login in a Cordova App__

This jquery plugin can be used to perform __Oauth2__ login in __Cordova__ app, it uses Cordova In-App-Browser to perform Oauth2 login flow and returns `access_token` or `error` in callback, along with actual response from the Oauth2 service.

Features
-
- Supports Oauth2 authorization code grant flow (server explicit)
- Supports Oauth2 implicit grant flow (client implicit)

Usage
-

```javascript
    $.oauth2({
        auth_url: '',           // required
        response_type: '',      // required  - "code"/"token"
        token_url: '',          // required for "code"
        logout_url: '',         // recommended if available
        client_id: '',          // required
        client_secret: '',      // required
        redirect_uri: '',       // required - any dummy url http://www.yourcompany.com
        other_parms: {}         // optional params object for scope, state, ...
    }, function(token, response){
        // do something with token or response
    }, function(error, response){
        // do something with error object
    }); 
```

How to build app and test?
-
__1. Build App using [Intel XDK](http://xdk.intel.com):__
- Download this repo.
- Download and install __Intel XDK__.
- Open Intel XDK > New Project > __Import__ and point to this folder.
- Open __index.html__ in editor and update __Oauth2 options__ (`client_id`, `client_secret`, ...) for the service you want to test.
- Test in the Intel XDK __Emulator__.
- Build your Cordova app by going to _Build_ tab in Intel XDK.
- Install App on device.

__2. Build App using [Phonegap build](http://build.phonegap.com):__
- Download this repo.
- Open __index.html__ in any editor and update __Oauth2 options__ (`client_id`, `client_secret`, ...) for the service you want to test.
- __Zip__ files `index.html`, `cordova.oauth2.js` and `config.xml`.
- Upload the zip in __http://build.phonegap.com__ to build Cordova App.
- Install App on device.
 

Services Tested
-
These Oauth2 services have been tested with this plugin sucessfully:
- __Google__ 
- __Facebook__ 
- __Instagram__ 
- __Foursquare__ 

_* Let me know if any service is not working, feel free to send any pull-request for improvements._
