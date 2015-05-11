Examples code for common Oauth2 services
=
Below are example code for the jQuery Oauth2 plugin for Cordova apps.

Facebook
-
Facebook supports client implicit grant type of Oauth2, below is example:
```javascript
    $.oauth2({
        auth_url: 'https://www.facebook.com/dialog/oauth',
        response_type: 'token',
        client_id: 'CLIENT-ID-FROM-FACEBOOK',
        redirect_uri: 'http://www.yourwebsite.com/oauth2callback',
        other_params: {scope: 'basic_info', display: 'popup'}
    }, function(token, response){
        makeAPICalls(token);
    }, function(error, response){
        alert(error);
    }); 
```

Google
-
Google supports client implicit grant type of Oauth2, below is example:
```javascript
    $.oauth2({
        auth_url: 'https://accounts.google.com/o/oauth2/auth',
        response_type: 'token',
        logout_url: 'https://accounts.google.com/logout',
        client_id: 'CLIENT-ID-FROM-GOOGLE',
        redirect_uri: 'http://www.yourwebsite.com/oauth2callback',
        other_params: {scope:'profile'}
    }, function(token, response){
        makeAPICalls(token);
    }, function(error, response){
        alert(error);
    }); 
```
Instagram
-
Instagram supports client implicit grant type of Oauth2, below is example:
```javascript
    $.oauth2({
        auth_url: 'https://api.instagram.com/oauth/authorize',
        response_type: 'token',
        logout_url: 'https://instagram.com/accounts/logout',
        client_id: 'CLIENT-ID-FROM-INSTAGRAM',
        redirect_uri: 'http://www.yourwebsite.com/oauth2callback',
        other_params: {scope:'likes'}
    }, function(token, response){
        makeAPICalls(token);
    }, function(error, response){
        alert(error);
    }); 
```
Foursquare
-
Foursquare supports client implicit grant type of Oauth2, below is example:
```javascript
    $.oauth2({
        auth_url: 'https://foursquare.com/oauth2/authorize',
        response_type: 'token',
        client_id: 'CLIENT-ID-FROM-FOURSQUARE',
        redirect_uri: 'http://www.yourwebsite.com/oauth2callback',
        other_params: {scope:'profile'}
    }, function(token, response){
        makeAPICalls(token);
    }, function(error, response){
        alert(error);
    }); 
```
LinkedIn
-
LinkedIn does noe support client implicit grant type of Oauth2, only authorization code grant type is supported, this is not recommended for client side apps, since the `client_secret` will be in the code and anyone can unpack an Android APK for example and get your `client_secret`, below is example:
```javascript
    $.oauth2({
        auth_url: 'https://www.linkedin.com/uas/oauth2/authorization',
        response_type: 'code',
        token_url: 'https://www.linkedin.com/uas/oauth2/accessToken',
        client_id: 'CLIENT-ID-FROM-LINKEDIN',
        client_secret: 'CLIENT-SECRET-FROM-LINKEDIN',
        redirect_uri: 'http://www.yourwebsite.com/oauth2callback',
        other_params: {scope: 'r_basicprofile', state: 'somethingrandom1234'}
    }, function(token, response){
        makeAPICalls(token);
    }, function(error, response){
        alert(error);
    }); 
```
