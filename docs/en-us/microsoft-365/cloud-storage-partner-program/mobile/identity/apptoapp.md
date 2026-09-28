<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/identity/apptoapp -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# App to app sign in for Microsoft 365 for mobile

The normal flow to sign in to your service from Microsoft 365 for mobile uses the OS WebView, where your web sign-in experience is rendered inside the Microsoft 365 for mobile app. Optionally, you can do an an additional optimization where the user can sign in using your app.

The app-to-app flow involves Microsoft 365 for mobile invoking your app through your app’s URL scheme to sign in to your service, and your app invoking Microsoft 365 for mobile when sign in is complete.

## Sign in using your app

- When signing in to your service is required \(i.e. the first time a file is opened from your app into Microsoft Office, or when the user explicitly adds your service as a place in Microsoft 365 for mobile\), Microsoft 365 for mobile calls your bootstrapper to obtain the `authorization_uri`, which it displays in a UIWebView. In addition to the `authorization_uri`, you should return a set of UrlSchemes that can be used to invoke your app.
- Microsoft 365 for mobile will first attempt to use the UrlSchemes to invoke your app. If none are returned, or if none of them are registered \(i.e. your app is not installed\), Microsoft 365 for mobile will fall back to the UIWebView.
- If the user does have your app installed, your app will be invoked via the UrlSchemes and the user will be sent to your app to complete authentication. If the user declines to open your app, Microsoft 365 for mobile will fall back to the UIWebView.
- Once inside your app, you should do whatever is needed to obtain the user’s auth code \(for example, display a “Grant permission to Office” dialog or ask for additional sign ins\).
- Return the user to the Microsoft 365 for mobile app with the auth code via the Office URL scheme \(see next section\).

## Microsoft 365 for iOS Specific changes

### URL scheme design

The data passed via the URL scheme is essentially the same as would be passed via `authorization_uri`.

Here is an example of a normal `authorization_uri` with parameters added. The parameters are described in [RFC6749](https://tools.ietf.org/html/rfc6749).

Invoking the sign in screen:

`https://contoso.com/api/oauth2/authorize?client_id=abcdefg&redirect_uri=https%3A%2F%2Flocalhost&response_type=code&scope=&rs=en-US&Build=16.1.1234&Platform=iOS`

Host’s redirect URL that ends the OAuth flow:

`https://localhost?state=&code=abcdefg&tk=https%3A%2F%2Fcontoso.com%2Fapi%2Ftoken%2F%3Fextra%3Dstuff`

The same parameters are passed via the URL Schemes, with the addition of “action”.

Microsoft 365 for iOS invoking your app \(“To” URL\):

`Contoso:client_id=abcdefg&response_type=code&scope=wopi&rs=enUS&build=16.1.1234&platform=iOS&app=word&action=76d173ad-a43f-4e3c-a5e7-0e7276b4c624`

Your app invoking Microsoft 365 for iOS \(“Back” URL\):

`ms-word-tp:code=abcdefg&tk=https%3A%2F%2Fcontoso.com%2Fapi%2Ftoken%2F%3Fextra%3Dstuff&sc=xyz&action=76d173ad-a43f-4e3c-a5e7-0e7276b4c624`

The values of the parameters should be URL encoded.

If authentication fails, the error parameters per [RFC6749](https://tools.ietf.org/html/rfc6749) can also be passed back to Microsoft 365 for iOS via the URL schemes, just as they can be passed back to Microsoft 365 for iOS via the redirect URI in the UIWebView model.

### New URL schemes registered by Microsoft 365 for iOS

- `ms-word-tp`
- `ms-excel-tp`
- `ms-powerpoint-tp`
- `ms-officemobile-tp`

These schemes are for Word, Excel, and PowerPoint respectively. Use these to invoke Microsoft 365 for iOS when the user is done with authentication on your side.

### Action parameter

Action is a string passed to your app that should be passed back to Office unchanged.

## Microsoft 365 for Android Specific changes

### Service-side Changes

#### Adding information to the WWW-Authenticate response header on unauthenticated bootstrap requests

Microsoft 365 for Android will use Intent to invoke your App. The information Microsoft 365 needs is your App’s Package name, Auth activity name, and Version code. Microsoft 365 will consider the provided Version code as the base version, and will assume that your App with this Version and above will support App-to-App authentication.

The information Microsoft 365 needs is passed via the URLScheme parameter in the WWW-Authenticate response header to unauthenticated bootstrap request.

| Parameter | Value | Required | Example |
| --- | --- | --- | --- |
| `Bearer` | n/a | Yes | Bearer |
| `authorization_uri` | The URL of the OAuth2 Authorization Endpoint to begin authentication against as described at: [**RFC 6749#section-3.1**](https://tools.ietf.org/html/rfc6749.html#section-3.1) | Yes | `https://contoso.com/api/oauth2/authorize` |
| `tokenIssuance_uri` | The URL of the OAuth2 Token Endpoint where authentication code can be redeemed for an access and \(optional\) refresh token. See Token EndPoint at: [**RFC 6749#section-3.2**](https://tools.ietf.org/html/rfc6749.html#section-3.2) | Yes | `https://contoso.com/api/oauth2/token` |
| `providerId` | A well-known string \(as registered with with Microsoft 365\) that uniquely identifies the host. Allowed characters: `[a-z,A-Z,0-9]` | No | TP\_CONTOSO |
| `UrlSchemes` | Information used to invoke your app \(despite the name of the parameter, this may not always be URL schemes; e.g. on Android, intent is used\).  <br>  <br>This is an ordered list by platform. Omit any platforms you do not support. Office will attempt to invoke these in order before falling back to the WebView auth. | No | `{`  <br>`"iOS": [`  <br>`"contoso",`  <br>`"contoso-EMM"`  <br>`],`  <br>`"Android": [`  <br>`"Package1VersionCode",`  <br>`"Package1Name",`  <br>`"Package1AuthActivityName",`  <br>`"Package2VersionCode",`  <br>`"Package2Name",`  <br>`"Package2AuthActivityName"`  <br>`],`  <br>`"UWP": [...]`  <br>`}` |

### Client-side Changes

#### Invoking your App on Android

1. Microsoft 365 will create an intent, which will take the package name and auth activity name of your App. We'll set following two extras to intent:

   - `AuthorizeUrlQueryParams`: It is exactly same as used in iOS without the `action` parameter. For example: `client_id=abcdefg&response_type=code&scope=wopi&rs=enUS&build=16.1.1234&platform=android&app=word`
   - `UserId`: It will be an optional parameter and will be set whenever we will have it. The third-party app should use this to verify that the sign in requested is for the User signed in to their App.


   ***Code sample 1 -*** *Sample intent creation code from* [*App2AppSigninIntent.java*](https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation/blob/master/samples/android/App2AppSigninIntent.java)


   ```java
   protected void LaunchIntent()
   {
       Intent authIntent = new Intent();
       authIntent.setComponent(new ComponentName("com.android.thirdparty.packagename", " com.android.thirdparty.packagename.AuthActivityName"));
       authIntent.putExtra(AuthorizeUrlQueryParams, client_id=abcdefg&response_type=code&scope=wopi&rs=enUS&build=16.1.1234&platform =android&app=word);
       authIntent.putExtra(UserId, User123);
       startActivityForResult(authIntent, uniqueRequestCode)
   }
   ```

2. After this, Microsoft 365 will wait for the result and will expect following from the third-party App:

   - `ResponseUrlQueryParams`: Again, this is exactly same as what we are getting in iOS minus the `action` parameter. The following are values of `ResponseUrlQueryParams` in success and failure cases:

     - `code=abcdefg&tk=http://contoso.com&sc=xyz` \[during RESULT\_OK\]
     - `error=invalid_request&error_description="optional human readable message"` \[during RESULT\_CANCELLED or anything else\]

   - `UserId`: The third party should send which user it authenticated. Microsoft 365 will use this to show an error in case the `UserId` in the request and the response don't match.


   ***Code sample 2 -*** *Sample code from* [*App2AppSigninIntent.java*](https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation/blob/master/samples/android/App2AppSigninIntent.java)


   ```java
   protected void onActivityResult(int requestCode, int resultCode, Intent result) 
   {
       // Check which request we're responding to
       if (requestCode == uniqueRequestCode) 
       {
            // Make sure the auth request was successful
            if (resultCode == RESULT_OK) 
            {
              //successfully authed
              // Here we will assume that result will contain ResonponseUrlQueryParams
              // which will look like this code=abcdefg&tk=http://contoso.com&sc=xyz 
             }
             else if (resultCode == RESULT_CANCELED)
             {
             //auth request cancel
             // Here we will assume that result will contain ResonponseUrlQueryParams
             // But this time we will not get tk and session context but may get error and error_description.
             }
        }
        else
        {
            //failed
            // Here we will assume that result will contain ResonponseUrlQueryParams
            // But this time we will not get tk and session context but may get error and error_description.
        } 
    }
   ```

#### Work your App needs to do

1. Add an intent filter to AndroidManifest.xml:

   ***Code sample 3 -*** *Add an intent filter to* [*AndroidManifest.xml*](https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation/blob/master/samples/android/AndroidManifest.xml)

   ```xml
   <activity android:name="AuthActivityName">
       <intent-filter>
           <action android:name="android.intent.action.VIEW"/>
           <category android:name="android.intent.category.DEFAULT"/>
           <category android:name="android.intent.category.br /OWSABLE"/>
       </intent-filter>
   </activity>
   ```

2. Handle the intent in AuthActivity:

   ***Code sample 4 -*** *Handle the intent using sample code from* [*HandleIntent.java*](https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation/blob/master/samples/android/HandleIntent.java)

   ```java
   protected void onCreate(Bundle savedInstanceState)
   {
        super.onCreate(savedInstanceState); 
        // Get the intent that started this activity
        Intent intent = getIntent();
        // Get the bundle of Extras, it will have data set by caller App
        Bundle extras = intent.getExtras();
   }
   ```

3. Return the result:

   ***Code sample 5 -*** *Return the result using sample code from* [*HandleIntent.java*](https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation/blob/master/samples/android/HandleIntent.java)

   ```java
   protected void returnResult()
   {
       // create intent to deliver result data
       Intent result = new Intent();
       resut.putExtra("ResonponseUrlQueryParams", "code=abcdefg&tk=http://contoso.com&sc=xyz");
       setResult(Activity.RESULT_OK, result);
       finish();
   }
   ```

You can find more details [in Return a Result on Android Developers](https://developer.android.com/training/basics/intents/filters.html#ReturnResult).
