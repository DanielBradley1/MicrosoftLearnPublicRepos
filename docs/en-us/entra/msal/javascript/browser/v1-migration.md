<!-- Source: https://learn.microsoft.com/en-us/entra/msal/javascript/browser/v1-migration -->
<!-- Sitemap-Last-Modified: 2025-08-14 -->

# Migrating from MSAL v1.x to MSAL v2.x

If you are new to MSAL, you should start [here](https://learn.microsoft.com/en-us/entra/msal/javascript/browser/initialization). If you are coming from MSAL v1.x, you can follow this guide to update your code to use MSAL v2.x

## 1. Update application registration

Go to the Microsoft Entra admin center for your tenant and review the App Registrations. You can create a [new registration](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-spa-app-registration#create-the-app-registration) for MSAL 2.x or you can [update your existing registration](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-spa-app-registration#redirect-uri-msaljs-20-with-auth-code-flow) for the registration that you are using for MSAL 1.x.

## 2. Add the `msal-browser` package to your project

Using npm, use the following:

```javascript
npm install @azure/msal-browser
```

## 3. Update your code

In MSAL 1.x, you created an application instance as below:

```javascript
import * as msal from "msal";

const msalInstance = new msal.UserAgentApplication(config);
```

In MSAL 2.x, you can update this to use the new `PublicClientApplication` object.

```javascript
import * as msal from "@azure/msal-browser";

const msalInstance = new msal.PublicClientApplication(config);
```

There may be some small differences in the configuration object that is passed in. If you are passing a more advanced configuration to the `UserAgentApplication` object, see [here](https://learn.microsoft.com/en-us/entra/msal/javascript/browser/configuration) for more information on new app object configuration options.

Request and response object signatures have changed - `acquireTokenSilent` now has a separate object signature from the interactive APIs. Please see [here](https://learn.microsoft.com/en-us/entra/msal/javascript/browser/request-response-object) for more information on configuring the request APIs.

Most APIs from MSAL 1.x have been carried forward to MSAL 2.x without change. Some functions have been removed:

- `handleRedirectCallback`
- `urlContainsHash`
- `getCurrentConfiguration`
- `getLoginInProgress`
- `getAccount`
- `getAccountState`
- `isCallback`

In MSAL 2.x, handling the response from the hash is an asynchronous operation, as MSAL will perform a token exchange as soon as it parses the authorization code from the response. Because of this, when performing redirect calls, MSAL provides the `handleRedirectPromise` function which will return a promise that resolves when the redirect has been fully handled by MSAL. When using a redirect method, the page used as the `redirectUri` must implement `handleRedirectPromise` to ensure the response is handled and tokens are cached when returning from the redirect.

```javascript
const myMSALObj = new msal.PublicClientApplication(msalConfig); 

// Register Callbacks for Redirect flow
myMSALObj.handleRedirectPromise().then((tokenResponse) => {
    let accountObj = null;
    if (tokenResponse !== null) {
        accountObj = tokenResponse.account;
        const id_token = tokenResponse.idToken;
        const access_token = tokenResponse.accessToken;
    } else {
        const currentAccounts = myMSALObj.getAllAccounts();
        if (!currentAccounts || currentAccounts.length === 0) {
            // No user signed in
            return;
        } else if (currentAccounts.length > 1) {
            // More than one user signed in, find desired user with getAccountByUsername(username)
        } else {
            accountObj = currentAccounts[0];
        }
    }
    
    const username = accountObj.username;
   
}).catch((error) => {
    handleError(error);
});

function signIn() {
    myMSALObj.loginRedirect(loginRequest);
}

async function getTokenRedirect(request) {
    return await myMSALObj.acquireTokenSilent(request).catch(error => {
        this.logger.info("silent token acquisition fails. acquiring token using redirect");
        // fallback to interaction when silent call fails
        return myMSALObj.acquireTokenRedirect(request)
    });
}
```

During `loginPopup`, `acquireTokenPopup`, or `acquireTokenSilent` calls, you can wait for the promise to resolve.

```javascript
const myMSALObj = new msal.PublicClientApplication(msalConfig); 

async function signIn(method) {
    try {
        const loginResponse = await myMSALObj.loginPopup(loginRequest);
    } catch (err) {
        handleError(error);
    }

    const currentAccounts = myMSALObj.getAllAccounts();
    if (!currentAccounts || currentAccounts.length === 0) {
        // No user signed in
        return;
    } else if (currentAccounts.length > 1) {
        // More than one user signed in, find desired user with getAccountByUsername(username)
    } else {
        accountObj = currentAccounts[0];
    }
}

async function getTokenPopup(request) {
    return await myMSALObj.acquireTokenSilent(request).catch(async (error) => {
        this.logger.info("silent token acquisition fails. acquiring token using popup");
        // fallback to interaction when silent call fails
        return await myMSALObj.acquireTokenPopup(request).catch(error => {
            handleError(error);
        });
    });
}
```

Please see the [login](https://learn.microsoft.com/en-us/entra/msal/javascript/browser/login-user) and [acquire token](https://learn.microsoft.com/en-us/entra/msal/javascript/browser/acquire-token) docs for more detailed information on usage.

Refresh tokens are now returned as part of the token responses, and are used by the library to renew access tokens without interaction or the use of iframes. See the [token lifetimes docs](https://learn.microsoft.com/en-us/entra/msal/javascript/browser/token-lifetimes) for more information on renewing tokens.

All other APIs should work as before. It is recommended to take a look at the [default sample](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/samples/msal-browser-samples/VanillaJSTestApp2.0) to see a working example of MSAL 2.0.
