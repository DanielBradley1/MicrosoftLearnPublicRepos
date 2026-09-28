<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-ios-macos-sign-in-user-after-sign-up -->
<!-- Sitemap-Last-Modified: 2025-03-04 -->

# Tutorial: Sign in user automatically after sign-up in an iOS/macOS app

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

This tutorial demonstrates how to sign in user automatically after sign-up in an iOS/macOS app by using native authentication.

In this tutorial, you:

- Sign in after sign-up.
- Handle errors.

## Prerequisites

- If you’re on iOS, follow the steps in [Sign in users in sample iOS \(Swift\) mobile app by using native authentication](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-run-native-authentication-sample-ios-app). If you’re using macOS, follow the steps in [Sign in users in sample macOS \(Swift\) app by using native authentication](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-run-native-authentication-sample-macos-app). These articles show you how to run sample apps that you configure using your tenant settings.
- [Tutorial: Add sign-up in an iOS/macOS app using native authentication](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-ios-macos-sign-up). The steps in this tutorial should work whether you sign up with email and password or email one-time passcode.

## Sign in after sign-up

The `Sign in after sign up` is an enhancement functionality of the sign in user flows, which has the effect of automatically signing in after successfully signing up. The SDK provides developers the ability to sign in a user after signing up, without having to supply the username, or to verify the email address through a one-time passcode.

To sign in a user after successful sign-up use the `signIn(delegate)` method from the new state `SignInAfterSignUpState` returned in the `onSignUpCompleted(newState)`:

```swift
extension ViewController: SignUpVerifyCodeDelegate {
    func onSignUpVerifyCodeError(error: MSAL.VerifyCodeError, newState: MSAL.SignUpCodeRequiredState?) {
        resultTextView.text = "Error verifying code: \(error.errorDescription ?? "no description")"
    }

    func onSignUpCompleted(newState: SignInAfterSignUpState) {
        resultTextView.text = "Signed up successfully!"
        let parameters = MSALNativeAuthSignInAfterSignUpParameters()
        newState.signIn(parameters: parameters, delegate: self)
    }
}
```

The `signIn(parameters:delegate)` accepts a `MSALNativeAuthSignInAfterSignUpParameters` instance and a delegate parameter and we must implement the required methods in the `SignInAfterSignUpDelegate` protocol.

In the most common scenario, we receive a call to `onSignInCompleted(result)` indicating that the user has signed in. The result can be used to retrieve the `access token`.

```swift
extension ViewController: SignInAfterSignUpDelegate {
    func onSignInAfterSignUpError(error: SignInAfterSignUpError) {
        resultTextView.text = "Error signing in after sign up"
    }

    func onSignInCompleted(result: MSAL.MSALNativeAuthUserAccountResult) {
        // User successfully signed in
        let parameters = MSALNativeAuthGetAccessTokenParameters()
        result.getAccessToken(parameters: parameters, delegate: self)
    }
}
```

The `getAccessToken(parameters:delegate)` accepts a `MSALNativeAuthGetAccessTokenParameters` instance and a delegate parameter and we must implement the required methods in the `CredentialsDelegate` protocol.

In the most common scenario, we receive a call to `onAccessTokenRetrieveCompleted(result)` indicating that the user obtained an `access token`.

```swift
extension ViewController: CredentialsDelegate {
    func onAccessTokenRetrieveError(error: MSAL.RetrieveAccessTokenError) {
        resultTextView.text = "Error retrieving access token"
    }

    func onAccessTokenRetrieveCompleted(result: MSALNativeAuthTokenResult) {
        resultTextView.text = "Signed in. Access Token: \(result.accessToken)"
    }
}
```

## Configure custom claims provider

If you want to add claims from an external system into the token that is issued to your app, use a [custom claims provider](https://learn.microsoft.com/en-us/entra/identity-platform/custom-claims-provider-overview). A custom claims provider is made up of a custom authentication extension that calls an external REST API to fetch claims from external systems.

Follow the steps in [Configure a custom claim provider](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-tokenissuancestart-configuration?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json) to add claims from an external system into your security tokens.

## Next step

[Tutorial: Self-service password reset](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-ios-macos-self-service-password-reset)
