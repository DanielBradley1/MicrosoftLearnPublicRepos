<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-ios-swift-custom-headers -->
<!-- Sitemap-Last-Modified: 2026-05-04 -->

# Tutorial: Add custom headers to native authentication network requests in iOS \(Swift\)

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

This tutorial demonstrates how to attach custom `x-*` headers to native authentication network requests in your iOS \(Swift\) app using the `MSALNativeAuthRequestInterceptor` protocol, enabling integration with third-party fraud and bot-detection SDKs.

In this tutorial, you:

- Understand the header naming rules enforced by MSAL.
- Implement the `MSALNativeAuthRequestInterceptor` protocol.
- Register the interceptor with your app configuration.

## Prerequisites

- An iOS \(Swift\) app that uses MSAL native authentication. If you don't have one, complete [Tutorial: Prepare your iOS/macOS mobile app for native authentication](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-prepare-ios-macos-app).
- Your app is initialized with an `MSALNativeAuthPublicClientApplication` instance. The steps in this tutorial show you how to update your existing app initialization code to register the interceptor.

## Understand header naming rules

MSAL applies the following rules when evaluating the headers you provide:

- Headers **must** start with `x-` \(case-insensitive\). Headers that don't start with `x-` are ignored.
- Headers that start with any of the following reserved prefixes are ignored:

  - `x-client-`
  - `x-ms-`
  - `x-broker-`
  - `x-app-`

- MSAL adds headers that pass both rules to the network request. If a header you provide has the same name as one of MSAL's own internal headers, your value takes precedence.

Use these rules to verify your vendor-required header names before implementing the interceptor.

## Implement the request interceptor

The `MSALNativeAuthRequestInterceptor` protocol declares a single method that MSAL calls before it sends each network request. Your implementation receives the request URL and a completion block, and then calls the completion block with a dictionary of headers to add, or `nil` if no headers are needed for that request.

Make your view controller \(or another class in your app\) conform to `MSALNativeAuthRequestInterceptor`:

```swift
extension EmailAndPasswordViewController: MSALNativeAuthRequestInterceptor {

    func addAdditionalHeaderFields(
        _ requestUrl: URL?,
        completionBlock: @escaping MSALNativeAuthRequestInterceptorAddHeaderCompletionBlock
    ) {
        // Scope headers to specific endpoints only.
        if requestUrl?.absoluteString.contains("oauth2/v2.0/initiate") == true {
            completionBlock([
                "value_1": "customer_header_1",          // Ignored: doesn't start with "x-"
                "x-client-header": "customer_header_2",  // Ignored: starts with reserved prefix "x-client-"
                "X-my-custom-header": "my data"          // Added to the network request.
            ])
            return
        }

        // Return nil for all other requests to avoid over-sending signals.
        completionBlock(nil)
    }
}
```

The method receives the full URL of the outgoing request in `requestUrl`. Use this to scope your headers to the specific endpoints your fraud or bot-detection vendor requires. For example, sign-in or sign-up initiation endpoints. Sending headers to unrelated endpoints can degrade signal quality and increase false positives.

Note

Always call `completionBlock` exactly once per invocation. Pass `nil` if no extra headers are needed for that request.

## Register the interceptor

After implementing the protocol, assign your interceptor to the `requestInterceptor` property on your `MSALNativeAuthPublicClientApplicationConfig` instance before creating the `MSALNativeAuthPublicClientApplication`:

```swift
do {
    let config = try MSALNativeAuthPublicClientApplicationConfig(
        clientId: Configuration.clientId,
        tenantSubdomain: Configuration.tenantSubdomain,
        challengeTypes: [.OOB, .password]
    )

    config.requestInterceptor = self

    nativeAuth = try MSALNativeAuthPublicClientApplication(nativeAuthConfiguration: config)
} catch {
    print("Unable to initialize MSAL \(error)")
}
```

## Verify headers are applied

To confirm that your headers reach the intended endpoints, inspect the outgoing network traffic using a network proxy tool such as Fiddler or Charles Proxy. Check that:

- Headers starting with `x-` and without reserved prefixes appear in the request.
- Headers with reserved prefixes \(`x-client-`, `x-ms-`, `x-broker-`, `x-app-`\) don't appear in the request.
- Headers are sent only to the endpoints you scoped them to.

Note

Logging inside the interceptor callback won't show you the final request headers. The callback is invoked before MSAL evaluates and applies the naming rules, so it reflects only the headers you provide, not what is ultimately sent.

## Related content

- [Native authentication overview](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication)
- [Tutorial: Add sign-in and sign-out in native iOS/macOS app](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-ios-macos-sign-in-sign-out)
- [Tutorial: Prepare your iOS/macOS mobile app for native authentication](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-prepare-ios-macos-app)
