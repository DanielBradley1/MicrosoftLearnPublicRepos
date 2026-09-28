<!-- Source: https://learn.microsoft.com/en-us/entra/msal/android/common-token-and-sigin-parameters -->
<!-- Sitemap-Last-Modified: 2024-02-07 -->

# Commonly used sign-in and tokens parameters

In an effort to increase usability and consistency throughout the MSAL API, we're prioritizing method overrides that use `TokenParameters` Subclasses as the only parameter. We've deprecated other overrides that use individual parameters for `SCOPE`, `PROMPT`, `account`, and other fields. Below is a guide to using the `TokenParameters` Subclasses as well as the `SignInParameters` class for `SignIn()` in `SingleAccountPublicAccountApplication`.

## `SignInParameters`

The `builder()` class for the new `SignInParameters` allows user to add 5 parameters to be used for `signIn` flow: activity, loginHint, scope, prompt, and callback. Note that scopes can be supplied either individually as String objects through `withScope()`, or all at once as a List `<String>` object through `withScopes()`.

Non-null: Scopes, Activity, Callback

Nullable: Login Hint, Prompt

```java
final SignInParameters signInParameters = SignInParameters.builder()
        .withScope(SCOPE)
        .withScopes(SCOPES)
        .withActivity(ACTIVITY)
        .withLoginHint(LOGINHINT)
        .withPrompt(PROMPT)
        .withCallback(new AuthenticationCallback() {
            @Override
            public void onCancel() {
                // Handle the signIn flow being cancelled
            }
            @Override
            public void onSuccess(IAuthenticationResult authenticationResult) {
                // Handle successful signIn flow with authenticationResult returned
            }
            @Override
            public void onError(MsalException exception) {
                // Handle an exception being thrown during the signIn flow
            }
        }).build();
```

## `AcquireTokenParameters`

Non-null: Scopes, Activity, Callback

Nullable: Account, Authority, Authentication Scheme, Claims Request, Correlation Id, Fragment, Login Hint, Prompt, OtherScopesToAuthorize

```java
final AcquireTokenParameters parameters = new AcquireTokenParameters.Builder()
        .withScopes(SCOPES)
        .startAuthorizationFromActivity(ACTIVITY)
        .forAccount(ACCOUNT)
        .fromAuthority(AUTHORITY)
        .withAuthenticationScheme(SCHEME)
        .withClaims(CLAIMS)
        .withCorrelationId(CORRELATION_ID)
        .withFragment(FRAGMENT)
        .withLoginHint(LOGINHINT)
        .withPrompt(PROMPT)
        .withOtherScopesToAuthorize(OTHER_SCOPES)
        .withCallback(new AuthenticationCallback() {
            @Override
            public void onCancel() {
                // Handle the acquireToken flow being cancelled
            }
            @Override
            public void onSuccess(IAuthenticationResult authenticationResult) {
                // Handle successful acquireToken flow with authenticationResult returned
            }
            @Override
            public void onError(MsalException exception) {
                // Handle an exception being thrown during the acquireToken flow
            }
        }).build();
```

## `AcquireTokenSilentParameters`

Non-null: Scopes, Callback, Account

Nullable: Authority, Authentication Scheme, Claims Request, Correlation Id, Force Refresh

```java
final AcquireTokenSilentParameters silentParameters = new AcquireTokenSilentParameters.Builder()
        .withScopes(SCOPES)
        .forAccount(ACCOUNT)
        .fromAuthority(AUTHORITY)
        .withAuthenticationScheme(SCHEME)
        .withClaims(CLAIMS)
        .withCorrelationId(CORRELATION_ID)
        .forceRefresh(false)
        .withCallback(new SilentAuthenticationCallback() {
            @Override
            public void onSuccess(IAuthenticationResult authenticationResult) {
                // Handle successful acquireTokenSilent flow with authenticationResult returned
            }

            @Override
            public void onError(MsalException exception) {
                // Handle an exception being thrown during the acquireTokenSilent flow
            }
        }).build();
```

## Preferred Overrides in `PublicClientApplication` classes

Below are the preferred `PublicClientApplication` method overrides moving forward, notice that other overrides of the same methods have been marked as deprecated.

### `ISingleAccountPublicClientApplication`

```java
/**
 * Acquire token interactively, will pop-up webUI. Interactive flow will skip the cache lookup.
 * Default value for {@link Prompt} is {@link Prompt#SELECT_ACCOUNT}.
 * <p>
 * Convey parameters via the AcquireTokenParameters object
 *
 * @param acquireTokenParameters {@link AcquireTokenParameters} instance containing the necessary fields. Activity, scopes, and callback must be non-null.
 */
 void acquireToken(@NonNull final AcquireTokenParameters acquireTokenParameters);

/**
 * Perform acquire token silent call. If there is a valid access token in the cache, the sdk will return the access token; If
 * no valid access token exists, the sdk will try to find a refresh token and use the refresh token to get a new access token. If refresh token does not exist
 * or it fails the refresh, exception will be sent back via callback.
 *
 * @param acquireTokenSilentParameters the {@link AcquireTokenSilentParameters} containing the needed parameters for acquireTokenSilent flow. Scopes and authority must be non-null.
 */
IAuthenticationResult acquireTokenSilent(@NonNull final AcquireTokenSilentParameters acquireTokenSilentParameters) throws InterruptedException, MsalException;

/**
 * Perform acquire token silent call. If there is a valid access token in the cache, the sdk will return the access token; If
 * no valid access token exists, the sdk will try to find a refresh token and use the refresh token to get a new access token. If refresh token does not exist
 * or it fails the refresh, exception will be sent back via callback.
 *
 * @param acquireTokenSilentParameters the {@link AcquireTokenSilentParameters} containing the needed fields for acquireTokenSilent flow. Scopes, authority, and callback must be non-null.
 */
void acquireTokenSilentAsync(@NonNull final AcquireTokenSilentParameters acquireTokenSilentParameters);

/**
 * Allows a user to sign in to your application with one of their accounts. This method may only
 * be called once: once a user is signed in, they must first be signed out before another user
 * may sign in. If you wish to prompt the existing user for credentials use
 * {@link #signInAgain(SignInParameters)} or
 * {@link #acquireToken(AcquireTokenParameters)}.
 * <p>
 * Note: The authority used to make the sign in request will be either the MSAL default: https://login.microsoftonline.com/common
 * or the default authority specified by you in your configuration.
 *
 * @param signInParameters the {@link SignInParameters} containing the needed fields for signIn flow. Activity, scopes, and callback must be non-null. loginHint and prompt are nullable
 */
void signIn(@NonNull final SignInParameters signInParameters);

/**
 * Reauthorizes the current account according to the supplied scopes and prompt behavior.
 * <p>
 * Note: The authority used to make the sign in request will be either the MSAL default:
 * https://login.microsoftonline.com/common or the default authority specified by you in your
 * configuration. This flow requires activity, scopes, and callback. Prompt is optional.
 *
 * @param signInParameters the {@link SignInParameters} containing the needed fields for signIn flow. Activity, scopes, and callback must be non-null.
 */
void signInAgain(@NonNull final SignInParameters signInParameters);
```

### `IMultipleAccountPublicClientApplication`

```java
/**
 * Acquire token interactively, will pop-up webUI. Interactive flow will skip the cache lookup.
 *
 * @param acquireTokenParameters {@link AcquireTokenParameters} instance containing the necessary fields. Activity, scopes, and callback must be non-null.
 */
void acquireToken(@NonNull final AcquireTokenParameters acquireTokenParameters);

/**
 * Perform acquire token silent call. If there is a valid access token in the cache, the sdk will return the access token; If
 * no valid access token exists, the sdk will try to find a refresh token and use the refresh token to get a new access token. If refresh token does not exist
 * or it fails the refresh, exception will be sent back via callback.
 *
 * @param acquireTokenSilentParameters {@link AcquireTokenSilentParameters} instance containing the necessary fields. Scopes, account, and authority must be non-null.
 */
@WorkerThread
IAuthenticationResult acquireTokenSilent(@NonNull final AcquireTokenSilentParameters acquireTokenSilentParameters) throws MsalException, InterruptedException;

/**
 * Perform acquire token silent call. If there is a valid access token in the cache, the sdk will return the access token; If
 * no valid access token exists, the sdk will try to find a refresh token and use the refresh token to get a new access token. If refresh token does not exist
 * or it fails the refresh, exception will be sent back via callback.
 *
 * @param acquireTokenSilentParameters {@link AcquireTokenSilentParameters} instance containing the necessary fields. Scopes, account, authority, and callback must be non-null.
 */
void acquireTokenSilentAsync(@NonNull final AcquireTokenSilentParameters acquireTokenSilentParameters);
```

### `IPublicClientApplication`

```java
/**
 * Acquire token interactively, will pop-up webUI. Interactive flow will skip the cache lookup.
 * Default value for {@link Prompt} is {@link Prompt#SELECT_ACCOUNT}.
 * <p>
 * Convey parameters via the AcquireTokenParameters object
 *
 * @param acquireTokenParameters AcquireTokenParameters instance containing the necessary fields. Activity, scopes, and callback must be non-null.
 */
void acquireToken(@NonNull final AcquireTokenParameters acquireTokenParameters);
```
