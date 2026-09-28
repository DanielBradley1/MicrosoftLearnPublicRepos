<!-- Source: https://learn.microsoft.com/en-us/entra/msal/android/frequently-asked-questions -->
<!-- Sitemap-Last-Modified: 2024-02-07 -->

# MSAL Android Frequently asked questions

## Redirect URI Issues

MSAL is configured to use brokered authentication by default. In order for this to work you need to construct a redirect URI using the signing keys associated with your application. Then your redirect URI needs to be included in both your application config file as well as in the Android manifest. Unfortunately a different encoding is needed for each. Let's do a quick walk-through:

1. The first thing you need to do is located your signing keys for your application. Typically your debug keys are in your home folder under a hidden folder called ".android" in a java keystore called debug.keystore. The azure portal provides helpful commands for generating the signature of your application as follows:

- MacOS:

```
keytool -exportcert -alias androiddebugkey -keystore ~/.android/debug.keystore | openssl sha1 -binary | openssl base64
```

- Windows:

```
keytool -exportcert -alias androiddebugkey -keystore %HOMEPATH%\.android\debug.keystore | openssl sha1 -binary | openssl base64
```

> WARNING: Piping command input/output is convenient; however potentially hides errors. If the keystore file is not found for example the error message will be piped to openssl and the complete command will still yield a result that looks like what you would expect. If in doubt the first command separately to ensure that it's working.

> WARNING: You will be asked to provide the password for your keystore. The debug keystore password is simply "android". If you were not prompted for a password there's a good chance that you need to run the parts of the command above separately to ensure that the keystore file was found.

> WARNING: If your keystore file is in a different location, you should replace `%HOMEPATH%\.android\debug.keystore` \(Windows\) or `~/.android/debug.keystore` \(MacOS\) with the path to your keystore file.

2. Once you have your base64 encoded signature. You can use it to configure an intent filter for your application so that browsers can correctly return authorization codes to your application. In order to make your intent filter unique on a device a custom scheme "msauth" and your package name are included in addition to your applications signature. Here's an example:

```xml
//NOTE: the slash before your signature value added to the path attribute
//This uses the base64 encoded signature produced above.
<data android:scheme="msauth"
                    android:host="com.microsoft.identity.client.sample.local"
                    android:path="/1wIqXSqBj7w+h11ZifsnqwgyKrY="/>
```

3. You msal configuration file requires something a bit different. It requires that the signature value be url encoded in addition to having already been base64 encoded. Here is an example:

```javascript
//NOTE that the signature part of the uri has been url encoded.  In this example.  The "+" character and the "=" character are affected.
"redirect_uri" : "msauth://com.microsoft.identity.client.sample.local/1wIqXSqBj7w%2Bh11ZifsnqwgyKrY%3D",
```

## View your assembled app's redirect URI configuration

To help you create \(or troubleshoot\) your app registration, we have added a helper function to `PublicClientApplication`, to help you configure and diagnose issues with your redirect URI, as well as redirect `Activity`.

Starting with MSAL 2.0.0, you can invoke the following method to output your application's suggested configuration.

```java
// From any Activity in your app, call this static method
PublicClientApplication.showExpectedMsalRedirectUriInfo(MyActivity.this);
```

![MSAL Redirect URI info](https://user-images.githubusercontent.com/8864677/88484771-e9b64e80-cf25-11ea-98d1-d7876ff8028c.png)
