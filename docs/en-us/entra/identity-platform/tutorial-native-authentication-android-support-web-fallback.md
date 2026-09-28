<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-android-support-web-fallback -->
<!-- Sitemap-Last-Modified: 2025-11-19 -->

# Tutorial: Support web fallback in Android app

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

This tutorial demonstrates how `isBrowserRequired()` error happens and how you can resolve it. The utility method `isBrowserRequired()` checks the need for a fallback mechanism for various scenarios where native authentication isn't sufficient to complete the authentication flow in functional and safe manner.

In this tutorial, you:

- Check `isBrowserRequired()`
- Handle `isBrowserRequired()`

## Prerequisites

- Complete the steps in [Sign in users in a sample native Android mobile application](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-run-native-authentication-sample-android-app). This article shows you how to run a sample Android that you configure by using your tenant settings.
- Complete the steps in [Tutorial: Add sign in and sign out with email one-time passcode](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-android-sign-in-sign-out).

## Web fallback

Use [web fallback mechanism](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication-web-fallback) for scenarios where native authentication isn't sufficient to complete the user authentication flow.

When you initialize the Android SDK, you specify the challenge types your mobile application supports, such as *oob* and *password*.

If your client app can't support a challenge type that Microsoft Entra requires, Microsoft Entra's response indicates that the client app needs to continue with the authentication flow in the browser. For example, you initialize the SDK with *oob* challenge type, but in the Microsoft Entra admin center you configure the app with an email with password authentication method.

In this case, the utility method `isBrowserRequired()` returns true.

## Sample flow

Let's look at an example flow that returns `isBrowserRequired()`, and how you can handle it:

1. In the JSON configuration file, which you pass to the SDK during initialization, add only the *oob* challenge type as shown the following code snippet:

   ```kotlin
   PublicClientApplication.createNativeAuthPublicClientApplication( 
       requireContext(), 
       R.raw.native_auth_config  // JSON configuration file 
   ) 
   ```


   The `native_auth_config.json` configuration has the following code snippet:


   ```json
   {
     "client_id" : "{Enter_the_Application_Id_Here}",
      "authorities" : [
       {
         "type": "CIAM",
         "authority_url": "https://{Enter_the_Tenant_Subdomain_Here}.ciamlogin.com/{Enter_the_Tenant_Subdomain_Here}.onmicrosoft.com/"
       }
     ],
     "challenge_types" : ["oob"],
     "logging": {
       "pii_enabled": false,
       "log_level": "INFO",
       "logcat_enabled": true
     }
   } 
   ```

2. In the Microsoft Entra admin center, [configure your user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers) to use **Email with password** as the authentication method.
3. Start a sign-up flow by using the SDK's `signUp(parameters)` method. You get a `SignUpError` that passes the `isBrowserRequired()` check as Microsoft Entra expects *password* and *oob* challenge type, but you configured your SDK with only *oob*.
4. To check and handle the `isBrowserRequired()`, use the following code snippet:

   ```kotlin
   val parameters = NativeAuthSignUpParameters(username = email)
   val actionResult: SignUpResult = authClient.signUp(parameters)

   if (actionResult is SignUpError && actionResult.isBrowserRequired()) { 
       // Handle "browser required" error
   } 
   ```


   The code indicates that the authentication flow can't be completed through native authentication, and that a browser has to be used.

## Handle isBrowserRequired\(\) error

To handle this error, the client app need to launch a browser and restart the authentication flow. You can accomplish by using Microsoft Authentication Library \(MSAL\) `acquireToken()` method.

To do so, use the following steps:

1. To add a redirect URI to the app that you registered earlier, use the steps in [Add a platform redirect URL](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-mobile-app-sign-in#add-a-redirect-uri).
2. To update your client app's configuration file, use the steps in [Configure the sample application](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-mobile-app-sign-in#configure-the-sample-application).
3. Use the following code snippet to acquire a token by using the `acquireToken()` method:

   ```kotlin
   val parameters = NativeAuthSignUpParameters(username = email)
   val actionResult: SignUpResult = authClient.signUp(parameters)

   if (actionResult is SignUpError && actionResult.isBrowserRequired()) {
       authClient.acquireToken(
           AcquireTokenParameters(
               AcquireTokenParameters.Builder()
                   .startAuthorizationFromActivity(requireActivity())
                   .withScopes(getScopes())
                   .withCallback(getAuthInteractiveCallback())
           )
           // Result will contain account and tokens retrieved through the browser.
       )
   } 
   ```

Security tokens, that's ID token, access token and refresh token, you get through native authentication flow are same as the token you get via browser-delegated flow.

## Related content

- Learn [How to run the iOS sample app](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-run-native-authentication-sample-ios-app)
- Explore [Native authentication API reference with email one-time passcode](https://learn.microsoft.com/en-us/entra/identity-platform/reference-native-authentication-email-otp?bc=/entra/external-id/customers/breadcrumb/toc.json&toc=/entra/external-id/customers/toc.json).
- Learn about [challenge types](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication-challenge-types).
