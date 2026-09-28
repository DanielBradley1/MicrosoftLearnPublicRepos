<!-- Source: https://learn.microsoft.com/en-us/entra/msal/javascript/node/regional-authorities -->
<!-- Sitemap-Last-Modified: 2026-03-15 -->

# Enabling regional authorities

Important

Regional authorities is a legacy feature that is only available for internal Microsoft services and the client credential flow. It is recommended to use [Managed Identity](https://learn.microsoft.com/en-us/entra/msal/javascript/node/managed-identity) instead.

To increase the reliability, availability and performance of Azure, regionalization aims to keep all traffic inside a geographical area. For example, if an app needs to fetch data from Key Vault in WestUs2, all the traffic this entails - including MSAL generated traffic - should stay in WestUs2.

A few important notes about regional authorities:

- Access tokens are the same, irrespective of the region they came from
- A token obtained for one region is valid for the non-regional endpoint \(tokens for "westus2.login.microsoft.com " are the same as tokens for "login.microsoftonline.com "\). And vice-versa. It's the same token, minus one claim called rh

Note

This legacy feature is only available for internal Microsoft services and the client credential flow.

## Configuration

To configure your application to use regional authorities, you a required to provide a region in the `azureRegion` field in the client credential request body.

### Using secrets securely

Secrets should never be hardcoded. The dotenv npm package can be used to store secrets in a .env file \(located in project's root directory\) that should be included in .gitignore to prevent accidental uploads of the secrets.

```js
var msal = require('@azure/msal-node');
require('dotenv').config(); // process.env now has the values defined in a .env file

const config = {
    auth: {
        clientId: "<CLIENT_ID>",
        authority: "https://login.microsoftonline.com/<TENANT_ID>",
        clientSecret: process.env.clientSecret,
    }
};

// Create msal application object
const cca = new msal.ConfidentialClientApplication(config);

const clientCredentialRequest = {
    scopes: ["<SCOPE_1>, <SCOPE_2>"],
    azureRegion: "REGION_NAME" // Specify the region you will deploy your application to here. E.g. "westus2"
};

cca
    .acquireTokenByClientCredential(clientCredentialRequest)
    .then((response) => {
        // Handle a successful authentication 
    })
    .catch((error) => {
        // Handle a failed authentication 
    });
```

Note

If you provide the value `"TryAutoDetect"` in the `azureRegion` field, the MSAL library will try to discover the region the application has been deployed to and use that region. This auto-detection is unreliable and should be avoided. Specify the region explicitly instead.

## See also

- You can find a working sample of this feature in the client-credentials [sample](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/samples/msal-node-samples/client-credentials)
