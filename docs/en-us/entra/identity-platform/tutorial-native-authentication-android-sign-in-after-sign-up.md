<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-android-sign-in-after-sign-up -->
<!-- Sitemap-Last-Modified: 2025-04-16 -->

# Tutorial: Sign in user automatically after sign-up in an Android app

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

This tutorial demonstrates how to sign in user automatically after sign-up in an Android app by using native authentication.

In this tutorial, you:

- Sign in after sign-up.
- Handle errors.

## Prerequisites

- Complete the steps [Sign in users in a sample native Android mobile application](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-run-native-authentication-sample-android-app). This article shows you how to run a sample Android that you configure by using your tenant settings.
- [Tutorial: Add sign-up in an Android mobile app using native authentication](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-android-sign-up). The steps in this tutorial should work whether you sign up with email and password or email one-time passcode.

## Sign in after sign-up

After a successful sign-up flow, you can automatically sign in your users without initiating a fresh sign-in flow.

The `SignUpResult.Complete` returns `SignInContinuationState` object. The `SignInContinuationState` object provides access to `signIn(parameters)` method.

To sign up a user with email and password, then automatically sign them in, use the following code snippet:

```kotlin
CoroutineScope(Dispatchers.Main).launch {
    val parameters = NativeAuthSignUpParameters(username = email)
    parameters.password = password
    val actionResult: SignUpResult = authClient.signUp(parameters)

    if (SignUpActionResult is SignUpResult.CodeRequired) { 
        val nextState = signUpActionResult.nextState 
        val submitCodeActionResult = nextState.submitCode( 
            code = code 
        ) 
        if (submitCodeActionResult is SignUpResult.Complete) {
            // Handle sign up success 
            val signInContinuationState = actionResult.nextState 

            val parameters = NativeAuthSignInContinuationParameters()
            val signInActionResult = signInContinuationState.signIn(parameters)

            if (signInActionResult is SignInResult.Complete) { 
                // Handle sign in success
                val accountState = signInActionResult.resultValue

                val getAccessTokenParameters = NativeAuthGetAccessTokenParameters()
                val accessTokenResult = accountState.getAccessToken(getAccessTokenParameters)

                if (accessTokenResult is GetAccessTokenResult.Complete) {
                    val accessToken = accessTokenResult.resultValue.accessToken
                    val idToken = accountState.getIdToken()
                }
            } 
        } 
    } 
}
```

To retrieve ID token claims after sign-in, use the steps in [Read ID token claims](https://learn.microsoft.com/en-us/entra/external-id/customers/tutorial-native-authentication-android-sign-in-user-with-username-password#read-id-token-claims).

## Handle sign-in errors

The `SignInContinuationState.signIn(parameters)` method returns `SignInResult.Complete` after a successful sign-in. It can also return an error.

To handle errors in `SignInContinuationState.signIn(parameters)`, use the following code snippet:

```kotlin
val parameters = NativeAuthSignInContinuationParameters()
val signInActionResult = signInContinuationState.signIn(parameters)

when (signInActionResult) {
    is SignInResult.Complete -> {
        // Handle sign in success
         displayAccount(accountState = actionResult.resultValue)
    }
    is SignInContinuationError -> {
        // Handle unexpected error
    }
    else -> {
        // Handle unexpected error
    }
}

private fun displayAccount(accountState: AccountState) {
    CoroutineScope(Dispatchers.Main).launch {
        val getAccessTokenParameters = NativeAuthGetAccessTokenParameters()
        val accessTokenResult = accountState.getAccessToken(getAccessTokenParameters)
        if (accessTokenResult is GetAccessTokenResult.Complete) {
            val accessToken = accessTokenResult.resultValue.accessToken
            val idToken = accountState.getIdToken()
        }
    }
}
```

## Next steps

- [Tutorial: Self-service password reset](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-android-self-service-password-reset)
