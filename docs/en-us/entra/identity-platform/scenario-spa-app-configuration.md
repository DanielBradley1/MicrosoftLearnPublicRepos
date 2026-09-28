<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/scenario-spa-app-configuration -->
<!-- Sitemap-Last-Modified: 2025-05-13 -->

# Single-page application: Code configuration

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

Learn how to configure the code for your single-page application \(SPA\).

## Prerequisites

- Register a new app in the [Microsoft Entra admin center](https://entra.microsoft.com), configured for *Accounts in this organizational directory only*. Refer to [Register an application](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) for more details. Record the following values from the application **Overview** page for later use:

  - Application \(client\) ID
  - Directory \(tenant\) ID

- Add the following redirect URIs using the **Single-page application** platform configuration. Refer to [How to add a redirect URI in your application](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-add-redirect-uri) for more details.

  - **Redirect URI**: `http://localhost:3000/`.

## Microsoft libraries supporting single-page apps

The following Microsoft libraries support single-page apps:

| Language / framework | Project on  <br>GitHub | Package | Getting  <br>started | Sign in users | Access web APIs |
| --- | --- | --- | :---: | :---: | :---: |
| React | [MSAL React](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-react)<sup>2</sup> | [msal-react](https://www.npmjs.com/package/@azure/msal-react) | [Quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) |
| JavaScript | [MSAL.js](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-browser)<sup>2</sup> | [msal-browser](https://www.npmjs.com/package/@azure/msal-browser) | [Quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) |
| Angular | [MSAL Angular](https://github.com/AzureAD/microsoft-authentication-library-for-js/blob/dev/lib/msal-angular)<sup>2</sup> | [msal-angular](https://www.npmjs.com/package/@azure/msal-angular) | [Quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) |

## Application code configuration

In an MSAL library, the application registration information is passed as configuration during the library initialization.

- [React](#tabpanel_1_react)
- [JavaScript](#tabpanel_1_javascript2)
- [Angular](#tabpanel_1_angular2)

```javascript
import { PublicClientApplication } from "@azure/msal-browser";
import { MsalProvider } from "@azure/msal-react";

// Configuration object constructed.
const config = {
    auth: {
        clientId: 'your_client_id'
    }
};

// create PublicClientApplication instance
const publicClientApplication = new PublicClientApplication(config);

// Wrap your app component tree in the MsalProvider component
ReactDOM.render(
    <React.StrictMode>
        <MsalProvider instance={publicClientApplication}>
            <App />
        </ MsalProvider>
    </React.StrictMode>,
    document.getElementById('root')
);
```

```javascript
import * as Msal from "@azure/msal-browser"; // if using CDN, 'Msal' will be available in global scope

// Configuration object constructed.
const config = {
    auth: {
        clientId: 'your_client_id'
    }
};

// create PublicClientApplication instance
const publicClientApplication = new Msal.PublicClientApplication(config);
```

```javascript
// In app.module.ts
import { MsalModule } from '@azure/msal-angular';
import { PublicClientApplication } from '@azure/msal-browser';

@NgModule({
    imports: [
        MsalModule.forRoot( new PublicClientApplication({
            auth: {
                clientId: 'Enter_the_Application_Id_Here',
            }
        }), null, null)
    ]
})
export class AppModule { }
```

For more information on the configurable options, see [Initializing application with MSAL.js](https://learn.microsoft.com/en-us/entra/identity-platform/msal-js-initializing-client-applications).

## Next step

- [Add Sign-in and sign-out code](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-spa-sign-in).
