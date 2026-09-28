<!-- Source: https://learn.microsoft.com/en-us/entra/msal/android/acquire-tokens -->
<!-- Sitemap-Last-Modified: 2024-02-27 -->

# Acquire tokens using MSAL Android

## Create an MSAL PublicClientApplication

In this example we are creating an instance of MultipleAccountPublicClientApplication, which is designed to work with apps that allow multiple accounts to be used within the same application. If you would like to use SingleAccount mode, refer to the [single vs. multi account documentation](https://learn.microsoft.com/en-us/entra/msal/android/single-multi-account). You can also check out the [MSAL Android quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-v2-android) for examples of how this is used.

1. Create a new MultipleAccountPublicClientApplication instance.

```Java

String[] scopes = {"User.Read"};
IMultipleAccountPublicClientApplication mMultipleAccountApp = null;
IAccount mFirstAccount = null;

PublicClientApplication.createMultipleAccountPublicClientApplication(getContext(),
    R.raw.msal_config,
    new IPublicClientApplication.IMultipleAccountApplicationCreatedListener() {
        @Override
        public void onCreated(IMultipleAccountPublicClientApplication application) {
            mMultipleAccountApp = application;
        }

        @Override
        public void onError(MsalException exception) {
            //Log Exception Here
        }
    });
```

## Acquire a token interactively

```java

final AcquireTokenParameters.Builder builder = new AcquireTokenParameters.Builder();
builder.startAuthorizationFromActivity(activity)
        .withScopes(scopes)
        .withCallback(getAuthInteractiveCallback());
final AcquireTokenParameters parameters = builder.build();
mMultipleAccountApp.acquireToken(parameters);

...

private AuthenticationCallback getAuthInteractiveCallback() {
    return new AuthenticationCallback() {
        @Override
        public void onSuccess(IAuthenticationResult authenticationResult) {
            /* Successfully got a token, use it to call a protected resource */
            String accessToken = authenticationResult.getAccessToken();
            // Record account used to acquire token
            mFirstAccount = authenticationResult.getAccount();
        }
        @Override
        public void onError(MsalException exception) {
            if (exception instanceof MsalClientException) {
                //And exception from the client (MSAL)
            } else if (exception instanceof MsalServiceException) {
                //An exception from the server
            }
        }
        @Override
        public void onCancel() {
            /* User canceled the authentication */
        }
    };
}
```

## Acquire a token silently

```java

/*
    Before getting a token silently for the account used to previously acquire a token interactively, we recommend that you verify that the account is still present in the local cache or on the device in case of brokered auth
    Let's use the synchronous methods here which can only be invoked from a Worker thread
*/

//On a worker thread
IAccount account = mMultipleAccountApp.getAccount(mFirstAccount.getId());

if(account != null){
    //Now that we know the account is still present in the local cache or not the device (broker authentication)

    //Request token silently
    String[] newScopes = {"Calendars.Read"};
    
    String authority = mMultipleAccountApp.getConfiguration().getDefaultAuthority().getAuthorityURL().toString();

    //Use default authority to request token from pass null
    final AcquireTokenSilentParameters.Builder builder = new AcquireTokenSilentParameters.Builder();
    builder.forAccount(account)
            .withScopes(newScopes)
            .fromAuthority(authority);
    final AcquireTokenSilentParameters parameters = builder.build();
    final IAuthenticationResult result = mMultipleAccountApp.acquireTokenSilent(parameters);
}
```
