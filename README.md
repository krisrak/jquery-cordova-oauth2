jquery-cordova-oauth2
=====================

__jQuery plugin for doing Oauth2 login in a Cordova App__

This jquery plugin can be used to perform __Oauth2__ login in __Cordova__ app, it uses __Cordova [In-App-Browser](https://github.com/apache/cordova-plugin-inappbrowser) Plugin__ to perform Oauth2 login flow and returns `access_token` or `error` in callback, along with actual response from the Oauth2 service.

Features
-
- Supports Oauth2 authorization code grant flow (server explicit)
- Supports Oauth2 implicit grant flow (client implicit)

  _[Implicit grant is recomended for Cordova apps since it does not require app to store client_secret]_

Usage
-

```javascript
    $.oauth2({
        auth_url: '',           // required
        response_type: '',      // required  - "code"/"token"
        token_url: '',          // required for response_type ="code"
        logout_url: '',         // recommended if available
        client_id: '',          // required
        client_secret: '',      // required for response_type ="code"
        redirect_uri: '',       // required - any dummy url http://www.yourcompany.com
        other_params: {}         // optional params object for scope, state, ...
    }, function(token, response){
        // do something with token or response
    }, function(error, response){
        // do something with error object
    }); 
```

__Example Oauth2 Calls:__

__1) Facebook Oauth2 (Implicit grant):__
Notice that `token_url` and `client_secret` is not required for Implicit grant and `logout_url` is not specified since facebook does not not have a logout url. Facebook also required a special `display` parameter to be passed in the URL, this is specified in the `other_params`. The first callback function will return the `access_token` which can be passed to another function to save and make other API calls. The second callback function handle any errors.

```javascript
    $.oauth2({
        auth_url: 'https://www.facebook.com/dialog/oauth',
        response_type: 'token',
        client_id: 'CLIENT-ID-FROM-FACEBOOK',
        redirect_uri: 'http://www.yourwebsite.com/redirect',
        other_params: {scope: 'basic_info', display: 'popup'}
    }, function(token, response){
        makeAPICalls(token);
    }, function(error, response){
        alert(error);
    }); 
```

__2) Google Oauth2 (Implicit grant):__
Notice that `token_url` and `client_secret` is not required for Implicit grant and `logout_url` is specified, this will make sure that Google logout is called before showing Google login option.

```javascript
    $.oauth2({
        auth_url: 'https://accounts.google.com/o/oauth2/auth',
        response_type: 'token',
        logout_url: 'https://accounts.google.com/logout',
        client_id: 'CLIENT-ID-FROM-GOOGLE',
        redirect_uri: 'http://www.yourwebsite.com/redirect',
        other_params: {scope: 'profile'}
    }, function(token, response){
        makeAPICalls(token);
    }, function(error, response){
        alert(error);
    }); 
```

__3) LinkedIn Oauth2 (Authorization code grant):__
This example show how to make LinkedIn Oauth2 call, notice the `scope` parameter is sepcified in the `other_params` option as an object, linkedIn also requires `state` parameter, this is also specified in the `other_params`. 

WARNING: Authorization code grant is not recomended for Cordova apps since the `client_secret` is exposed in the code and anyone can unpack an Adroid APK for example and get your `client_secret`. Always check if the service supports Implicit grant type of Oauth2 and use it instead of authorization code grant for your Cordova app.

```javascript
    $.oauth2({
        auth_url: 'https://www.linkedin.com/uas/oauth2/authorization',
        response_type: 'code',
        token_url: 'https://www.linkedin.com/uas/oauth2/accessToken',
        client_id: 'CLIENT-ID-FROM-LINKEDIN',
        client_secret: 'CLIENT-SECRET-FROM-LINKEDIN',
        redirect_uri: 'http://www.yourwebsite.com/redirect',
        other_params: {scope: 'r_basicprofile', state: 'somethingrandom1234'}
    }, function(token, response){
        makeAPICalls(token);
    }, function(error, response){
        alert(error);
    }); 
```


How to build app and test?
-
__1. Build App using [Intel XDK](http://xdk.intel.com):__
- Download this repo.
- Download and install __Intel XDK__.
- Open Intel XDK > New Project > __Import__ and point to this folder.
- Open __index.html__ in editor and update __Oauth2 options__ (`client_id`, `client_secret`, ...) for the service you want to test.
- Add __In-App-Browser__ Cordova plugin from the project settings.
- Test in the Intel XDK __Emulator__.
- Build your Cordova app by going to _Build_ tab in Intel XDK.
- Install App on device.

__2. Build App using [Phonegap build](http://build.phonegap.com):__
- Download this repo.
- Open __index.html__ in any editor and update __Oauth2 options__ (`client_id`, `client_secret`, ...) for the service you want to test.
- __Zip__ files `index.html`, `cordova.oauth2.js` and `config.xml`.
- Upload the zip in __http://build.phonegap.com__ to build Cordova App.
- Install App on device.

__3. Build App using [Cordova CLI](http://cordova.apache.org/docs/en/3.3.0/guide_cli_index.md.html#The%20Command-Line%20Interface):__
- Download this repo. 
- Follow intructions to [build app using Cordova CLI](http://cordova.apache.org/docs/en/3.3.0/guide_cli_index.md.html#The%20Command-Line%20Interface)
- Add __In-App-Browser__ Cordova plugin
- Install App on device.

Services Tested
-
These Oauth2 services have been tested with this plugin sucessfully:
- __Google__ 
- __Facebook__ 
- __Instagram__ 
- __Foursquare__ 
- __LinkedIn__ 

here is [example code](https://github.com/krisrak/jquery-cordova-oauth2/blob/master/EXAMPLE.md)

_* Let me know if any service is not working, feel free to send any pull-request for improvements._
