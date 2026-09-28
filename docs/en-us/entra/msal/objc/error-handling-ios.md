<!-- Source: https://learn.microsoft.com/en-us/entra/msal/objc/error-handling-ios -->
<!-- Sitemap-Last-Modified: 2024-02-26 -->

# Handle errors and exceptions in MSAL for iOS/macOS

This article gives an overview of the different types of errors and recommendations for handling common sign-in errors.

## MSAL error handling basics

Exceptions in Microsoft Authentication Library \(MSAL\) are intended for app developers to troubleshoot, not for displaying to end users. Exception messages are not localized.

When processing exceptions and errors, you can use the exception type itself and the error code to distinguish between exceptions. For a list of error codes, see [Microsoft Entra authentication and authorization error codes](https://learn.microsoft.com/en-us/entra/identity-platform/reference-error-codes).

During the sign-in experience, you may encounter errors about consents, Conditional Access \(MFA, Device Management, Location-based restrictions\), token issuance and redemption, and user properties.

The following section provides more details about error handling for your app.

## Error handling in MSAL for iOS/macOS

The complete list of MSAL for iOS and macOS errors is listed in [MSALError enum](https://github.com/AzureAD/microsoft-authentication-library-for-objc/blob/master/MSAL/src/public/MSALError.h#L128).

All MSAL produced errors are returned with `MSALErrorDomain` domain.

For system errors, MSAL returns the original `NSError` from the system API. For example, if token acquisition fails because of a lack of network connectivity, MSAL returns an error with the `NSURLErrorDomain` domain and `NSURLErrorNotConnectedToInternet` code.

We recommend that you handle at least the following two MSAL errors on the client side:

- `MSALErrorInteractionRequired`: The user must do an interactive request. There are many conditions that can lead to this error such as an expired authentication session or the need for additional authentication requirements. Call the MSAL interactive token acquisition API to recover.
- `MSALErrorServerDeclinedScopes`: Some or all scopes were declined. Decide whether to continue with only the granted scopes, or stop the sign-in process.

Note

The `MSALInternalError` enum should only be used for reference and debugging. Do not try to automatically handle these errors at runtime. If your app encounters any of the errors that fall under `MSALInternalError`, you may want to show a generic user facing message explaining what happened.

For example, `MSALInternalErrorBrokerResponseNotReceived` means that user didn't complete authentication and manually returned to the app. In this case, your app should show a generic error message explaining that authentication didn't complete and suggest that they try to authenticate again.

The following Objective-C sample code demonstrates best practices for handling some common error conditions.

```objc
    MSALInteractiveTokenParameters *interactiveParameters = ...;
    MSALSilentTokenParameters *silentParameters = ...;
    
    MSALCompletionBlock completionBlock;
    __block __weak MSALCompletionBlock weakCompletionBlock;
    
    weakCompletionBlock = completionBlock = ^(MSALResult *result, NSError *error)
    {
        if (!error)
        {
            // Use result.accessToken
            NSString *accessToken = result.accessToken;
            return;
        }
        
        if ([error.domain isEqualToString:MSALErrorDomain])
        {
            switch (error.code)
            {
                case MSALErrorInteractionRequired:
                {
                    // Interactive auth will be required
                    [application acquireTokenWithParameters:interactiveParameters
                                            completionBlock:weakCompletionBlock];
                    
                    break;
                }
                    
                case MSALErrorServerDeclinedScopes:
                {
                    // These are list of granted and declined scopes.
                    NSArray *grantedScopes = error.userInfo[MSALGrantedScopesKey];
                    NSArray *declinedScopes = error.userInfo[MSALDeclinedScopesKey];
                    
                    // To continue acquiring token for granted scopes only, do the following
                    silentParameters.scopes = grantedScopes;
                    [application acquireTokenSilentWithParameters:silentParameters
                                                  completionBlock:weakCompletionBlock];
                    
                    // Otherwise, instead, handle error fittingly to the application context
                    break;
                }
                    
                case MSALErrorServerProtectionPoliciesRequired:
                {
                    // Integrate the Intune SDK and call the
                    // remediateComplianceForIdentity:silent: API.
                    // Handle this error only if you integrated Intune SDK.
                    // See more info here: https://aka.ms/intuneMAMSDK
                    
                    break;
                }
                    
                case MSALErrorUserCanceled:
                {
                    // The user cancelled the web auth session.
                    // You may want to ask the user to try again.
                    // Handling of this error is optional.
                    
                    break;
                }
                    
                case MSALErrorInternal:
                {
                    // Log the error, then inspect the MSALInternalErrorCodeKey
                    // in the userInfo dictionary.
                    // Display generic error message to the end user
                    // More detailed information about the specific error
                    // under MSALInternalErrorCodeKey can be found in MSALInternalError enum.
                    NSLog(@"Failed with error %@", error);
                    
                    break;
                }
                    
                default:
                    NSLog(@"Failed with unknown MSAL error %@", error);
                    
                    break;
            }
            
            return;
        }
        
        // Handle no internet connection.
        if ([error.domain isEqualToString:NSURLErrorDomain] && error.code == NSURLErrorNotConnectedToInternet)
        {
            NSLog(@"No internet connection.");
            return;
        }
        
        // Other errors may require trying again later,
        // or reporting authentication problems to the user.
        NSLog(@"Failed with error %@", error);
    };
    
    // Acquire token silently
    [application acquireTokenSilentWithParameters:silentParameters
                                  completionBlock:completionBlock];

     // or acquire it interactively.
     [application acquireTokenWithParameters:interactiveParameters
                             completionBlock:completionBlock];
```

```swift
    let interactiveParameters: MSALInteractiveTokenParameters = ...
    let silentParameters: MSALSilentTokenParameters = ...
            
    var completionBlock: MSALCompletionBlock!
    completionBlock = { (result: MSALResult?, error: Error?) in
                
        if let result = result
        {
            // Use result.accessToken
            let accessToken = result.accessToken
            return
        }

        guard let error = error as NSError? else { return }

        if error.domain == MSALErrorDomain, let errorCode = MSALError(rawValue: error.code)
        {
            switch errorCode
            {
                case .interactionRequired:
                    // Interactive auth will be required
                    application.acquireToken(with: interactiveParameters, completionBlock: completionBlock)

                case .serverDeclinedScopes:
                    let grantedScopes = error.userInfo[MSALGrantedScopesKey]
                    let declinedScopes = error.userInfo[MSALDeclinedScopesKey]

                    if let scopes = grantedScopes as? [String] {
                        silentParameters.scopes = scopes
                        application.acquireTokenSilent(with: silentParameters, completionBlock: completionBlock)
                    }
                        
                    case .serverProtectionPoliciesRequired:
                        // Integrate the Intune SDK and call the
                        // remediateComplianceForIdentity:silent: API.
                        // Handle this error only if you integrated Intune SDK.
                        // See more info here: https://aka.ms/intuneMAMSDK
                        break
                        
                    case .userCanceled:
                       // The user cancelled the web auth session.
                       // You may want to ask the user to try again.
                       // Handling of this error is optional.
                       break
                        
                    case .internal:
                        // Log the error, then inspect the MSALInternalErrorCodeKey
                        // in the userInfo dictionary.
                        // Display generic error message to the end user
                        // More detailed information about the specific error
                        // under MSALInternalErrorCodeKey can be found in MSALInternalError enum.
                        print("Failed with error \(error)");
                        
                    default:
                        print("Failed with unknown MSAL error \(error)")
            }
        }
                
        // Handle no internet connection.
        if error.domain == NSURLErrorDomain && error.code == NSURLErrorNotConnectedToInternet
        {
            print("No internet connection.")
            return
        }
                
        // Other errors may require trying again later,
        // or reporting authentication problems to the user.
        print("Failed with error \(error)");    
    }
   
    // Acquire token silently
    application.acquireToken(with: interactiveParameters, completionBlock: completionBlock)
 
    // or acquire it interactively.
    application.acquireTokenSilent(with: silentParameters, completionBlock: completionBlock)
```

## Conditional Access and claims challenges

When getting tokens silently, your application may receive errors when a [Conditional Access claims challenge](https://learn.microsoft.com/en-us/entra/identity-platform/v2-conditional-access-dev-guide) such as MFA policy is required by an API you're trying to access.

The pattern for handling this error is to interactively acquire a token using MSAL. This prompts the user and gives them the opportunity to satisfy the required Conditional Access policy.

In certain cases when calling an API requiring Conditional Access, you can receive a claims challenge in the error from the API. For instance if the Conditional Access policy is to have a managed device \(Intune\) the error will be something like [AADSTS53000: Your device is required to be managed to access this resource](https://learn.microsoft.com/en-us/entra/identity-platform/reference-error-codes) or something similar. In this case, you can pass the claims in the acquire token call so that the user is prompted to satisfy the appropriate policy.

MSAL for iOS and macOS allows you to request specific claims in both interactive and silent token acquisition scenarios.

To request custom claims, specify `claimsRequest` in `MSALSilentTokenParameters` or `MSALInteractiveTokenParameters`.

See [Request custom claims using MSAL for iOS and macOS](https://learn.microsoft.com/en-us/entra/msal/objc/request-custom-claims) for more info.

## Retrying after errors and exceptions

You're expected to implement your own retry policies when calling MSAL. MSAL makes HTTP calls to the Microsoft Entra service, and occasionally failures can occur. For example the network can go down or the server is overloaded.

### HTTP 429

When the Service Token Server \(STS\) is overloaded with too many requests, it returns HTTP error 429 with a hint about how long until you can try again in the `Retry-After` response field.

## Next steps

Consider enabling [Logging in MSAL for iOS/macOS](https://learn.microsoft.com/en-us/entra/msal/objc/logging-ios) to help you diagnose and debug issues.
