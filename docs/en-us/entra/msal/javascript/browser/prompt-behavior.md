<!-- Source: https://learn.microsoft.com/en-us/entra/msal/javascript/browser/prompt-behavior -->
<!-- Sitemap-Last-Modified: 2025-08-14 -->

# Prompt behavior with MSAL.js

MSAL.js allows passing a prompt value as part of its login or token request methods. Based on your application scenario, you can customize the Microsoft Entra prompt behavior for a request by setting the **prompt** parameter in the [request object](https://azuread.github.io/microsoft-authentication-library-for-js/ref/modules/_azure_msal_common.html#commonauthorizationurlrequest):

```javascript
import { PublicClientApplication } from "@azure/msal-browser";

const pca = new PublicClientApplication({
    auth: {
        clientId: "YOUR_CLIENT_ID"
    }
});

const loginRequest = {
    scopes: ["user.read"],
    prompt: 'select_account',
}

pca.loginPopup(loginRequest)
    .then(response => {
        // do something with the response
    })
    .catch(error => {
        // handle errors
    });
```

## Supported prompt values

The following prompt values can be used when authenticating with the Microsoft identity platform:

| Parameter | Behavior |
| --- | --- |
| `login` | Forces the user to enter their credentials on that request, negating single-sign on. |
| `none` | Ensures that the user isn't presented with any interactive prompt. If the request can't be completed silently by using single-sign on, the Microsoft identity platform returns a *login\_required* or *interaction\_required* error. |
| `consent` | Triggers the OAuth consent dialog after the user signs in, asking the user to grant permissions to the app. |
| `select_account` | Interrupts single sign-on by providing an account selection experience listing all the accounts in session or an option to choose a different account altogether. |
| `create` | Triggers a sign-up dialog allowing external users to create an account. For more information, see: [Self-service sign-up](https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-overview) |

MSAL.js will throw an `invalid_prompt` error for any unsupported prompt values:

```console
invalid_prompt_value: Supported prompt values are 'login', 'select_account', 'consent', 'create' and 'none'. Please see here for valid configuration options: https://azuread.github.io/microsoft-authentication-library-for-js/ref/modules/_azure_msal_common.html#commonauthorizationurlrequest Given value: my_custom_prompt
```

## Default prompt values

The following shows default prompt values that MSAL.js uses:

| MSAL.js method | Default prompt | Allowed prompts |
| --- | --- | --- |
| `loginPopup` | N/A | Any |
| `loginRedirect` | N/A | Any |
| `ssoSilent` | `none` | N/A \(ignored\) |
| `acquireTokenPopup` | N/A | Any |
| `acquireTokenRedirect` | N/A | Any |
| `acquireTokenSilent` | `none` | N/A \(ignored\) |

Note

Note that **prompt** is a protocol-level parameter and signals the desired authentication behavior to the identity provider. It does not affect MSAL.js behavior and MSAL.js does not have control over how the service will ultimately handle the request. In most circumstances, Microsoft Entra ID will try to honor the request. If this is not possible, it may return an error response, or completely ignore the given prompt value.

## Interactive requests with prompt=none

Generally, when you need to make a silent request, use a silent MSAL.js method \(`ssoSilent`, `acquireTokenSilent`\), and handle any *login\_required* or *interaction\_required* errors with an interactive method \(`loginPopup`, `loginRedirect`, `acquireTokenPopup`, `acquireTokenRedirect`\).

In some cases however, the prompt value `none` can be used together with an interactive MSAL.js method to achieve silent authentication. For instance, due to the third-party cookie restrictions in some browsers, `ssoSilent` requests will fail despite an active user session with Microsoft Entra ID. As a remedy, you can pass the prompt value `none` to an interactive request such as `loginPopup`. MSAL.js will then open a popup window to Microsoft Entra ID and Microsoft Entra ID will honor the prompt value by utilizing the existing session cookie. In this case, the user will see a brief popup window but will not be prompted for a credential entry.

## Next steps

- [Single sign-on with MSAL.js](https://learn.microsoft.com/en-us/entra/msal/javascript/browser/single-sign-on)
- [Handle errors and exceptions in MSAL.js](https://learn.microsoft.com/en-us/entra/msal/javascript/browser/errors)
- [Handle ITP in Safari and other browsers where third-party cookies are blocked](https://learn.microsoft.com/en-us/entra/identity-platform/reference-third-party-cookies-spas)
- [OAuth 2.0 authorization code flow on the Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow)
- [OpenID Connect on the Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/v2-protocols-oidc)
