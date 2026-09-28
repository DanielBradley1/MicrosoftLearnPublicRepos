<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-android-sign-in-call-api -->
<!-- Sitemap-Last-Modified: 2025-03-04 -->

# Tutorial: Call an API in Android app by using native authentication

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

In this tutorial, you learn how to acquire an access token and call an API in your Android mobile app. Microsoft Authentication Library \(MSAL\) native authentication SDK for Android allows you to acquire multiple access tokens with a single sign-in. This capability allows you to acquire one or more access tokens without requiring a user to reauthenticate.

In this tutorial, you:

- Acquire one or multiple access tokens.
- Call an API

## Prerequisites

- Complete the steps in [Tutorial: Add sign-in in Android app by using native authentication](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-android-sign-in-sign-out). This tutorial shows you how to sign in users in your Android app by using native authentication.

## Acquire an access token

Once the user signs in, you acquire an access token by specifying the scopes for which the access token is valid.

MSAL native authentication SDK supports multiple access tokens, so you can specify multiple sets of scopes, then request access token for each set of scopes:

1. Declare and set values for a set of API scopes by using the following code snippet:

   ```kotlin
   companion object {
       // Set values for respective API scopes for their web API resources here, for example: ["api://<Resource_App_ID>/ToDoList.Read", "api://<Resource_App_ID>/ToDoList.ReadWrite"]
       // A list of scope for API 1
       private val scopesForAPI1 = listOf<String>()
       // A list of scope for API 2
       private val scopesForAPI2 = listOf<String>()
   }
   ```

2. Signs in user by using the following code snippet:

   ```kotlin
   CoroutineScope(Dispatchers.Main).launch {
       val parameters = NativeAuthSignInParameters(username = email)
       parameters.password = password
       val actionResult: SignInResult = authClient.signIn(parameters)

       if (actionResult is SignInResult.Complete) -> {
           // Perform operations after successful sign-in
       } else if (actionResult is SignInError) {
           // Handle sign-in errors
       }
   }
   ```

3. Acquire one or multiple access tokens by using the following code snippet:

   ```kotlin
   CoroutineScope(Dispatchers.Main).launch {
       val accountResult = authClient.getCurrentAccount()
       when (accountResult) {
           is GetAccountResult.AccountFound -> {
               try {
                   // Access token for API 1
                   val accessTokenOne = getAccessToken(accountResult.resultValue, scopesForAPI1)
                   // Access token for API 2
                   val accessTokenTwo = getAccessToken(accountResult.resultValue, scopesForAPI2)
                   // Proceed to make a call to an API
               } catch (e: Exception) {
                   // Handle Exception
               }
           }
           is GetAccountResult.NoAccountFound -> {
               // Handle etAccountResult.NoAccountFound
           }
           is GetAccountError -> {
               // Handle GetAccountError 
           }
       }
   }   
   ```


   Define the `getAccessToken()` function as shown in the following code:


   ```kotlin
   private suspend fun getAccessToken(accountState: AccountState, scopes: List<String>): String {
       val parameters = NativeAuthGetAccessTokenParameters()
       parameters.scopes = scopes
       val accessTokenState = accountState.getAccessToken(parameters)

       return if (accessTokenState is GetAccessTokenResult.Complete) {
           accessTokenState.resultValue.accessToken
       } else {
           throw Exception("Failed to get access token")
       }
   }
   ```

## Call an API

To make an API call, use the access token you acquired in [Acquire an access token](#acquire-an-access-token) and an API URL:

1. Declare and set values for the API URLs by using the following code snippet:

   ```kotlin
   companion object {
       // Set values for respective API scopes for web API resources here, for example: ["api://<Resource_App_ID>/ToDoList.Read", "api://<Resource_App_ID>/ToDoList.ReadWrite"]
       // A list of scope for API 1
       private val scopesForAPI1 = listOf<String>()
       // A list of scope for API 2
       private val scopesForAPI2 = listOf<String>()
       // Set the URL of first web API resource here
       private const val WEB_API_URL_1 = "Enter_URL_Of_First_Web_API" 
       // Set the URL of second web API resource here
       private const val WEB_API_URL_2 = "Enter_URL_Of_Second_Web_API" 
   }
   ```


   Replace the:


   - `Enter_URL_Of_First_Web_API` placeholder with the full URL value of your first API.
   - `Enter_URL_Of_Second_Web_API` placeholder with the full URL value of your second API.

2. Use the following code snippets to call an API:

   ```kotlin
   // After you acquire an access token, use it to call an API

   val firstApiResponse = useAccessToken(WEB_API_URL_1, accessTokenOne)
   val secondApiResponse = useAccessToken(WEB_API_URL_2, accessTokenTwo)

   private suspend fun useAccessToken(WEB_API_URL: String, accessToken: String): Response {
       return withContext(Dispatchers.IO) {
           ApiClient.performGetApiRequest(WEB_API_URL, accessToken)
       }
   }
   ```


   Define the `performGetApiRequest()` function as shown in the following code:


   ```kotlin
   object ApiClient {
       private val client = OkHttpClient()

       fun performGetApiRequest(WEB_API_URL: String, accessToken: String): Response {    
           val requestBuilder = Request.Builder()
                   .url(WEB_API_URL)
                   .addHeader("Authorization", "Bearer $accessToken")
                   .get()

           val request = requestBuilder.build()

           client.newCall(request).execute().use { response -> return response }
       }
   }
   ```

## Configure custom claims provider

If you want to add claims from an external system into the token that is issued to your app, use a [custom claims provider](https://learn.microsoft.com/en-us/entra/identity-platform/custom-claims-provider-overview). A custom claims provider is made up of a custom authentication extension that calls an external REST API to fetch claims from external systems.

Follow the steps in [Configure a custom claim provider](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-tokenissuancestart-configuration?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json) to add claims from an external system into your security tokens.

## Related content

- [Explore native authentication API reference](https://learn.microsoft.com/en-us/entra/identity-platform/reference-native-authentication-api?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json).
- [Configure a custom claim provider](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-tokenissuancestart-configuration?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json).
- [Customize the look and feel of the authentication experience for the external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-branding-customers).
