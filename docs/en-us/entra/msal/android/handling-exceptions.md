<!-- Source: https://learn.microsoft.com/en-us/entra/msal/android/handling-exceptions -->
<!-- Sitemap-Last-Modified: 2024-02-07 -->

# Handle errors and exceptions in MSAL for Android

Exceptions in the Microsoft Authentication Library \(MSAL\) are intended to help app developers troubleshoot their application. Exception messages aren't localized.

When processing exceptions and errors, you can use the exception type itself and the error code to distinguish between exceptions. For a list of error codes, see [Microsoft Entra authentication and authorization error codes](https://learn.microsoft.com/en-us/entra/identity-platform/reference-error-codes).

During the sign-in experience, you can encounter errors about consents, Conditional Access \(MFA, Device Management, Location-based restrictions\), token issuance and redemption, and user properties.

| Error class | Cause/error string | How to handle |
| --- | --- | --- |
| `MsalUiRequiredException` | - `INVALID_GRANT`: The refresh token used to redeem access token is invalid, expired, or revoked. This exception may be because of a password change.<br>- `NO_TOKENS_FOUND`: Access token doesn't exist and no refresh token can be found to redeem access token.<br>- Step-up required<br><br>  - MFA<br>  - Missing claims<br><br>- Blocked by Conditional Access \(for example, [authentication broker](https://learn.microsoft.com/en-us/entra/msal/android/single-sign-on) installation required\)<br>- `NO_ACCOUNT_FOUND`: No account available in the cache for silent authentication. | Call `acquireToken()` to prompt the user to enter their username and password, and possibly consent and perform multifactor authentication. |
| `MsalDeclinedScopeException` | - `DECLINED_SCOPE`: User or server hasn't accepted all scopes. The server may decline a scope if the requested scope isn't supported, not recognized, or not supported for a particular account. | The developer should decide whether to continue authentication with the granted scopes or end the authentication process. Option to resubmit the acquire token request only for the granted scopes and provide hints for which permissions have been granted by passing `silentParametersForGrantedScopes` and calling `acquireTokenSilent`. |
| `MsalServiceException` | - `INVALID_REQUEST`: This request is missing a required parameter, includes an invalid parameter, includes a parameter more than once, or is otherwise malformed.<br>- `SERVICE_NOT_AVAILABLE`: Represents 500/503/506 error codes due to the service being down.<br>- `UNAUTHORIZED_REQUEST`: The client isn't authorized to request an authorization code.<br>- `ACCESS_DENIED`: The resource owner or authorization server denied the request.<br>- `INVALID_INSTANCE`: `AuthorityMetadata` validation failed<br>- `UNKNOWN_ERROR`: Request to server failed, but no error and `error_description` are returned back from the service. | This exception class represents errors when communicating to the service, can be from the authorize or token endpoints. MSAL reads the error and error\_description from the server response. Generally, these errors are resolved by fixing app configurations either in code or in the app registration portal. Rarely a service outage can trigger this warning, which can only be mitigated by waiting for the service to recover. |
| `MsalClientException` | - `MULTIPLE_MATCHING_TOKENS_DETECTED`: There are multiple cache entries found and the SDK can't identify the correct access or refresh token from the cache. This exception usually indicates a bug in the SDK for storing tokens or that the authority isn't provided in the silent request and multiple matching tokens are found.<br>- `DEVICE_NETWORK_NOT_AVAILABLE`: No active network is available on the device.<br>- `NO_NETWORK_CONNECTION_POWER_OPTIMIZATION`: No active network available due to power optimization is enabled. The device is in doze mode or the app is standby.<br>- `JSON_PARSE_FAILURE`: The SDK failed to parse the JSON format.<br>- `IO_ERROR`: `IOException` happened, could be a device or network error.<br>- `MALFORMED_URL`: The URL is malformed. Likely caused when constructing the auth request, authority, or redirect URI.<br>- `UNSUPPORTED_ENCODING`: The encoding isn't supported by the device.<br>- `NO_SUCH_ALGORITHM`: The algorithm used to generate [PKCE](https://tools.ietf.org/html/rfc7636) challenge isn't supported.<br>- `INVALID_JWT`: `JWT` returned by the server isn't valid or is empty or malformed.<br>- `STATE_MISMATCH`: State from authorization response didn't match the state in the authorization request. For authorization requests, the SDK will verify the state returned from redirect and the one sent in the request.<br>- `UNSUPPORTED_URL`: Unsupported URL can't perform ADFS authority validation.<br>- `AUTHORITY_VALIDATION_NOT_SUPPORTED`: The authority isn't supported for authority validation. The SDK supports B2C authorities, but doesn't support B2C authority validation. Only well-known host is supported.<br>- `CHROME_NOT_INSTALLED`: Chrome isn't installed on the device. The SDK uses chrome custom tab for authorization requests if available, and will fall back to chrome browser.<br>- `REQUEST_THROTTLED_AT_ESTS_GATEWAY`: The request is currently throttled at the ESTS gateway due to a high volume of requests from the client. Please retry after some time.<br>- `USER_MISMATCH`: The user provided in the acquire token request doesn't match the user returned from server. | This exception class represents general errors that are local to the library. These exceptions can be handled by correcting the request. |
| `MsalUserCancelException` | - `USER_CANCELED`: The user initiated interactive flow and prior to receiving tokens back they canceled the request. |  |
| `MsalArgumentException` | - `ILLEGAL_ARGUMENT_ERROR_CODE`<br>- `AUTHORITY_REQUIRED_FOR_SILENT`: Authority must be specified for `acquireTokenSilent`. | These errors can be mitigated by the developer correcting arguments and ensuring activity for interactive auth, completion callback, scopes, and an account with a valid ID have been provided. |

## Catching errors

The following code snippet shows an example of catching errors for the silent `acquireToken` calls.

```java
/**
 * Callback used in for silent acquireToken calls.
 */
private SilentAuthenticationCallback getAuthSilentCallback() {
    return new SilentAuthenticationCallback() {

        @Override
        public void onSuccess(IAuthenticationResult authenticationResult) {
            Log.d(TAG, "Successfully authenticated");

            /* Successfully got a token, use it to call a protected resource - MSGraph */
            callGraphAPI(authenticationResult);
        }

        @Override
        public void onError(MsalException exception) {
            /* Failed to acquireToken */
            Log.d(TAG, "Authentication failed: " + exception.toString());
            displayError(exception);

            if (exception instanceof MsalClientException) {
                /* Exception inside MSAL, more info inside MsalError.java */
            } else if (exception instanceof MsalServiceException) {
                /* Exception when communicating with the STS, likely config issue */
            } else if (exception instanceof MsalUiRequiredException) {
                /* Tokens expired or no session, retry with interactive */
            }
        }
    };
}
```

## Next steps

Learn more about [Logging in MSAL for Android](https://learn.microsoft.com/en-us/entra/msal/android/logging).
