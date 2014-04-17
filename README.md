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

```
    $.oauth2({
        auth_url: '',           // required
        response_type: '',      // required  - "code"/"token"
        token_url: '',          // required for "code"
        logout_url: '',         // recommended if available
        client_id: '',          // required
        client_secret: '',      // required
        redirect_uri: '',       // required - any dummy url http://www.yourcompany.com
        scope: ''               // optional
    }, function(token, response){
        // do something with token or response
    }, function(error, response){
        // do something with error object
    }); 
```

Services Tested
-
These Oauth2 services have been tested with this plugin sucessfully:
- __Google__ 
- __Facebook__ 
- __Instagram__ 
- __Foursquare__ 
