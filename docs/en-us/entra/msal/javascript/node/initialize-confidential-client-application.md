<!-- Source: https://learn.microsoft.com/en-us/entra/msal/javascript/node/initialize-confidential-client-application -->
<!-- Sitemap-Last-Modified: 2026-03-15 -->

# Initialize confidential client applications in MSAL Node

This article shows you how to initialize the `ConfidentialClientApplication` object in MSAL Node. You'll learn how to use secrets and certificates securely, and how to configure the authority.

## Prerequisites

Before initializing an application, you first need to [register it in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-spa-app-registration), establishing a trust relationship between your application and the Microsoft identity platform.

After registering your app, you'll need some or all of the following values that can be found in the Microsoft Entra admin center.

| Value | Required | Description |
| :--- | :---: | :--- |
| Application \(client\) ID | Required | A GUID that uniquely identifies your application within the Microsoft identity platform. |
| Authority | Optional | The identity provider URL \(the *instance*\) and the *sign-in audience* for your application. The instance and sign-in audience, when concatenated, make up the *authority*. |
| Directory \(tenant\) ID | Optional | Specify Directory \(tenant\) ID if you're building a line-of-business application solely for your organization, often referred to as a *single-tenant application*. |
| Redirect URI | Optional | If you're building a web app, the `redirectUri` specifies where the identity provider \(the Microsoft identity platform\) should return the security tokens it has issued. |

## Initializing the `ConfidentialClientApplication` object

In order to use MSAL Node, you need to instantiate a [ConfidentialClient](https://learn.microsoft.com/en-us/javascript/api/@azure/msal-node/confidentialclientapplication) object.

### Using secrets and certificates securely

Secrets should never be hardcoded. The dotenv npm package can be used to store secrets or certificates in a .env file \(located in project's root directory\) that should be included in *.gitignore* to prevent accidental uploads of the secrets.

Certificates can also be read-in from files via NodeJS's fs module. However, they should never be stored in the project's directory. Production apps should fetch certificates from [Azure KeyVault](https://azure.microsoft.com/products/key-vault), or other secure key vaults.

Please see [certificates and secrets](https://learn.microsoft.com/en-us/entra/identity-platform/security-best-practices-for-app-registration#certificates-and-secrets) for more information.

See the MSAL sample: [auth-code-with-certs](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/master/samples/msal-node-samples/auth-code-with-certs)

```javascript
import * as msal from "@azure/msal-node";
import "dotenv/config"; // process.env now has the values defined in a .env file

const clientAssertionCallback = async (config) => {
    // network request that uses config.clientId and (optionally) config.tokenEndpoint
    const result = await Promise.resolve(
        "network request which gets assertion"
    );
    return result;
};

const clientConfig = {
    auth: {
        clientId: "your_client_id",
        authority: "your_authority",
        clientSecret: process.env.clientSecret, // OR
        clientCertificate: {
            thumbprintSha256: process.env.thumbprint,
            privateKey: process.env.privateKey,
        }, // OR
        clientAssertion: clientAssertionCallback, // or a predetermined clientAssertion string
    },
};
const cca = new msal.ConfidentialClientApplication(clientConfig);
```

Please refer to [Common issues when importing certificates](https://learn.microsoft.com/en-us/entra/msal/javascript/node/certificate-credentials#common-issues).

## Configuration Basics

[Configuration](https://learn.microsoft.com/en-us/javascript/api/@azure/msal-node/configuration) options for node have `common` parameters and `specific` paremeters per authentication flow.

- `clientId` is mandatory to initialize a public client application
- `authority` defaults to `https://login.microsoftonline.com/common/` if the user does not set it during configuration
- A Client credential is mandatory for confidential clients. Client credential can be a:

  - `clientSecret` is secret string generated set on the app registration.
  - `clientCertificate` is a certificate set on the app registration. The `thumbprintSha256` is a X.509 SHA-256 thumbprint of the certificate, and the `privateKey` is the PEM encoded private key. `x5c` is the optional X.509 certificate chain used in [subject name/issuer auth scenarios](https://learn.microsoft.com/en-us/entra/msal/javascript/node/sni).
  - `clientAssertion` is a ClientAssertion object containing an assertion string or a callback function that returns an assertion string that the application uses when requesting a token, as well as the assertion's type \(urn:ietf:params:oauth:client-assertion-type:jwt-bearer\). The callback is invoked every time MSAL needs to acquire a token from the token issuer. App developers should generally use the callback because assertions expire and new assertions need to be created. App developers are responsible for the assertion lifetime. Use [this mechanism](https://learn.microsoft.com/en-us/entra/workload-id/workload-identity-federation-create-trust) to get tokens for a downstream API using a Federated Identity Credential.

For more options on [Configuration](https://learn.microsoft.com/en-us/javascript/api/@azure/msal-node/configuration) refer to [Configuration in MSAL Node](https://learn.microsoft.com/en-us/entra/msal/javascript/node/configuration).

## Configure Authority

By default, MSAL is configured with the `common` tenant, which is used for multi-tenant applications and applications allowing personal accounts \(not B2C\).

```javascript
    authority: 'https://login.microsoftonline.com/common/'
```

If your application audience is a single tenant, you must provide an authority with your tenant ID like below:

```javascript
    authority: 'https://login.microsoftonline.com/{your_tenant_id}'
```

## Next Steps

[Acquire tokens in MSAL Node](https://learn.microsoft.com/en-us/entra/msal/javascript/node/acquire-token-requests)
