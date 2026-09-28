<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/configure-authentication-msal -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# Configure authentication in your agent

With your Azure Bot Service resources provisioned, you can configure your agent to authenticate with Azure Bot Service. The Microsoft 365 Agents SDK provides flexible options for authentication configuration, allowing you to choose the method that best fits your application's needs and security requirements.

The .NET Agents SDK Microsoft Authentication Library \(MSAL\) package provides you with tools that help you create access tokens for agent clients and external services from a Microsoft 365 Agents SDK self-hosted agent.

The `Microsoft.Agents.Athentication.Msal` package provides the `MsalAuth` class, which is the core authentication provider. You can configure it for the following types of credentials:

- Single-tenant with client secret and Multitenant with client secret
- Client certificate using thumbprint
- Client certificate using subject name \(including SN+I\)
- User-Assigned Managed Identity
- System-Assigned Managed Identity
- Federated credentials
- Workload identity

## Install the authentication package

Install the MSAL authentication package from NuGet:

```bash
dotnet add package Microsoft.Agents.Authentication.Msal
```

## Single-tenant vs multitenant

Client secret authentication supports both single-tenant and multitenant configurations.

Note

For multitenant, you need to configure the Azure Bot instance as multitenant and the Microsoft Entra ID app registration as *Accounts in any organizational directory \(Any Microsoft Entra ID tenant - Multitenant\)*. To learn more, see [Single and multitenant apps](https://learn.microsoft.com/en-us/entra/identity-platform/single-and-multi-tenant-apps).

## Configure a connection

The MSAL authentication package lets you create and use multiple distinct clients with the Agents Framework hosting engine. With the MSAL authentication package, you can provide multiple connection configurations in the application configuration file. Each connection configuration can be used to create a named authentication client to support communications with external services or other agents.

## Environment variables for each authentication type

The agent obtains MSAL configuration at runtime from environment variables.

The following sections describe the required and optional configuration settings for each of the supported auth types for MSAL authentication, along with example configuration snippets for each type.

## Single-tenant with client secret

Use these settings to configure a single-tenant connection that authenticates with a client secret.

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| ClientId | String | Null | ClientId \(AppId\) to use when creating the Access token. |
| ClientSecret | string | Null | When AuthType is ClientSecret, Is Secret associated with the client, this should only be used for testing and development purposes. |
| AuthorityEndpoint | String | Null | When present, used as the Authority to request a token from. |
| TenantId | String | Null | When present and AuthorityEndpoint is null, used to create an Authority to request a token from |
| Scopes | String list | Null | Default Lists of scopes to request tokens for. Is only used when no scopes are passed from the agent connection request |

Here's an example appsettings for single-tenant `ClientSecret`:

```json
  "Connections": {
    "ServiceConnection": {
      "Settings": {
        "AuthType": "ClientSecret",
        "ClientId": "{{BOT_ID}}",
        "ClientSecret": "{{BOT_SECRET}}",
        "AuthorityEndpoint": "https://login.microsoftonline.com/{{BOT_TENANT_ID}}",
        "Scopes": [
            "https://api.botframework.com/.default"
          ],
      }
    }
  }
```

## Multitenant with client secret

Use these settings to configure a multitenant connection that authenticates with a client secret.

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| ClientId | String | Null | ClientId \(AppId\) to use when creating the Access token. |
| ClientSecret | string | Null | When AuthType is ClientSecret, Is Secret associated with the client, this should only be used for testing and development purposes. |
| AuthorityEndpoint | String | Null | When present, used as the Authority to request a token from. |
| TenantId | String | Null | When present and AuthorityEndpoint is null, used to create an Authority to request a token from |
| Scopes | String list | Null | Default Lists of scopes to request tokens for. Is only used when no scopes are passed from the agent connection request |

Here's an example appsettings for multitenant with client secret:

```json
  "Connections": {
    "ServiceConnection": {
      "Settings": {
        "AuthType": "ClientSecret",
        "ClientId": "{{BOT_ID}}",
        "ClientSecret": "{{BOT_SECRET}}",
        "AuthorityEndpoint": "https://login.microsoftonline.com/botframework.com",
        "Scopes": [
            "https://api.botframework.com/.default"
          ],
      }
    }
  }
```

## User-Assigned Managed Identity

Use these settings to configure token acquisition with a user-assigned managed identity.

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| ClientId | String | Null | Managed Identity ClientId to use when creating the Access token. |

Note

When you want to use the managed identity types in your agent, you need to run your host or client on an Azure service and set up that service with either a System-Assigned Managed identity, or a User-Assigned Managed identity.

Here's an example appsettings for User-Assigned Managed Identity:

```json
  "Connections": {
    "ServiceConnection": {
      "Settings": {
        "AuthType": "UserManagedIdentity",
        "ClientId": "{{BOT_ID}}",
        "Scopes": [
          "https://api.botframework.com/.default"
        ]
      }
    }
  }
```

## System-Assigned Managed Identity

When you use `SystemManagedIdentity`, the agent ignores any provided client ID and uses the system-managed identity.

Note

When you want to use the managed identity types in your agent, you need to run your host or client on an Azure service and set up that service with either a System-Assigned Managed identity, or a User-Assigned Managed identity.

Here's an example appsettings for System-Assigned Managed Identity auth type:

```json
  "Connections": {
    "ServiceConnection": {
      "Settings": {
        "AuthType": "SystemManagedIdentity",
        "Scopes": [
          "https://api.botframework.com/.default"
        ]
      }
    }
  }
```

## Federated credentials

Use these settings to configure a connection that exchanges federated credentials for access tokens.

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| ClientId | String | Null | ClientId \(AppId\) to use when creating the Access token. |
| AuthorityEndpoint | String | Null | When present, used as the Authority to request a token from. |
| TenantId | String | Null | When present and AuthorityEndpoint is null, used to create an Authority to request a token from |
| Scopes | String list | Null | Default Lists of scopes to request tokens for. Is only used when no scopes are passed from the agent connection request |
| FederatedClientId | String | Null | Managed Identity ClientId to use when creating the Access token. |

Here's an example appsettings for `Federated Credentials`:

```json
  "Connections": {
    "ServiceConnection": {
      "Settings": {
        "AuthType": "FederatedCredentials",
        "ClientId": "{{BOT_ID}}",
        "AuthorityEndpoint": "https://login.microsoftonline.com/{{BOT_TENANT_ID}}",
        "FederatedClientId": "{{BOT_FEDERATED_ID}}",
        "Scopes": [
          "https://api.botframework.com/.default"
        ]
      }
    }
  }
```

## Workload identity

Use these settings to configure workload identity authentication using a federated token file.

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| ClientId | String | Null | ClientId \(AppId\) to use when creating the Access token. |
| AuthorityEndpoint | String | Null | When present, used as the Authority to request a token from. |
| TenantId | String | Null | When present and AuthorityEndpoint is null, used to create an Authority to request a token from |
| Scopes | String list | Null | Default Lists of scopes to request tokens for. Is only used when no scopes are passed from the agent connection request |
| FederatedTokenFile | String | Null | The token file \(same as AKS `AZURE_FEDERATED_TOKEN_FILE` env var\) |

Here's an example appsettings for single-tenant `WorkloadIdentity`:

```json
  "Connections": {
    "ServiceConnection": {
      "Settings": {
        "AuthType": "WorkloadIdentity",
        "ClientId": "{{BOT_ID}}",
        "AuthorityEndpoint": "https://login.microsoftonline.com/{{BOT_TENANT_ID}}",
        "FederatedTokenFile": "{{BOT_FEDERATED_TOKENFILE}}",
        "Scopes": [
          "https://api.botframework.com/.default"
        ]
      }
    }
  }
```

### Optional federated credentials or workload identity client assertion options

Use these optional settings to customize client assertion content for federated credentials or workload identity flows.

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| ClientId | String | Null | Client ID for which a signed assertion is requested |
| TokenEndpoint | String | Null | The intended token endpoint |
| Claims | String | Null | Claims to be included in the client assertion |
| ClientCapabilities | String\[\] | Null | Capabilities that the client application declares. |

```json
  "Connections": {
    "ServiceConnection": {
      "Settings": {
        "AuthType": "WorkloadIdentity",
        "ClientId": "{{BOT_ID}}",
        "AuthorityEndpoint": "https://login.microsoftonline.com/{{BOT_TENANT_ID}}",
        "FederatedTokenFile": "{{BOT_FEDERATED_TOKENFILE}}",
        "Scopes": [
          "https://api.botframework.com/.default"
        ],
        "AssertionRequestOptions": {
            "ClientId": null,
            "TokenEndpoint": null,
            "Claims": null,
            "ClientCapabilities": null,
        }
      }
    }
  }
```

## Certificate using subject name \(including SN+I\)

Use these settings to configure certificate-based authentication by certificate subject name, including SN+I scenarios.

| AuthType | Type | Default Value | Description |
| --- | --- | --- | --- |
| AuthorityEndpoint | String | Null | When present, used as the Authority to request a token from. |
| TenantId | String | Null | When present and AuthorityEndpoint is null, used to create an Authority to request a token from |
| Scopes | String list | Null | Default Lists of scopes to request tokens for. Is only used when no scopes are passed from the agent connection request |
| ClientId | String | Null | ClientId \(AppId\) to use when creating the Access token. |
| CertSubjectName | String | Null | When AuthType is CertificateSubjectName, this is the subject name that is sought |
| CertStoreName | String | "My" | When AuthType is either CertificateSubjectName or Certificate, Indicates which certificate store to look in |
| ValidCertificateOnly | bool | True | Requires the certificate to have a valid chain. |
| SendX5C | bool | False | Enables certificate auto rotation with appropriate configuration. |

Here's an example appsettings for certificate using subject name for Subject Name and Issuer \(SNI\) and multitenant:

```json
  "Connections": {
    "ServiceConnection": {
      "Settings": {
        "AuthType": "CertificateSubjectName",
        "ClientId": "{{BOT_ID}}",
        "CertSubjectName": "{{BOT_CERT_SUBJECTNAME}}",
        "SendX5C": true,
        "AuthorityEndpoint": "https://login.microsoftonline.com/botframework.com",
        "Scopes": [
          "https://api.botframework.com/.default"
        ]
      }
    }
  },
```

Here's an example appsettings for Certificate Subject Name for SN+I and single-tenant:

```json
  "Connections": {
    "ServiceConnection": {
      "Settings": {
        "AuthType": "CertificateSubjectName",
        "ClientId": "{{BOT_ID}}",
        "CertSubjectName": "{{BOT_CERT_SUBJECTNAME}}",
        "SendX5C": true,
        "AuthorityEndpoint": "https://login.microsoftonline.com/{{BOT_TENANT_ID}}",
        "Scopes": [
          "https://api.botframework.com/.default"
        ]
      }
    }
  },
```

## Client certificate using thumbprint

Use these settings to configure certificate-based authentication by certificate thumbprint.

| AuthType | Type | Default Value | Description |
| --- | --- | --- | --- |
| AuthorityEndpoint | String | Null | When present, used as the Authority to request a token from. |
| TenantId | String | Null | When present and AuthorityEndpoint is null, used to create an Authority to request a token from |
| Scopes | String list | Null | Default Lists of scopes to request tokens for. Is only used when no scopes are passed from the agent connection request |
| ClientId | String | Null | ClientId \(AppId\) to use when creating the Access token. |
| CertThumbprint | String | Null | Thumbprint of the certificate to load, only valid when AuthType is set as Certificate |
| CertStoreName | String | "My" | When AuthType is either CertificateSubjectName or Certificate, Indicates which certificate store to look in |
| ValidCertificateOnly | bool | True | Requires the certificate to have a valid chain. |
| SendX5C | bool | False | Enables certificate auto rotation with appropriate configuration. |

Here's an example appsettings for certificate using the certificate thumbprint:

```json
  "Connections": {
    "ServiceConnection": {
      "Settings": {
        "AuthType": "Certificate",
        "ClientId": "{{BOT_ID}}",
        "CertThumbprint": "{{BOT_CERT_THUMBPRINT}}",
        "AuthorityEndpoint": "https://login.microsoftonline.com/botframework.com",
        "Scopes": [
          "https://api.botframework.com/.default"
        ]
      }
    }
  },
```

## Default configuration provider for MSAL

To ease setup, we provide a service provider extension to add the default configuration settings for MSAL to your Agent.

Here's an example of default MSAL configuration provider for an ASP.NET core host in a `Program.cs` class.

This is managed by the registered `IConnections` instance. The `IConnections` instance is added by default when you use `AddAgent`.

```csharp
// Register your AgentApplication
builder.AddAgent<MyAgent>();
```

However, if you're not using `AddAgent`, you have to explicitly register the `IConnections` instance.

```csharp
    // Add Connections object to access configured token connections.
    builder.Services.AddSingleton<IConnections, ConfigurationConnections>();
```

## More MSAL configuration options

There are several shared configuration options that control general settings for acquiring tokens from Microsoft Entra Identity.

These settings are:

Use the following shared settings to control MSAL request timeout, retry behavior, and logging detail.

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| MSALRequestTimeout | TimeSpan | 30seconds | This setting controls how long the client will wait for a response from Microsoft Entra ID after sending a request. |
| MSALRetryCount | Int | 3 | This setting controls how many retry attempts the provider makes for an individual request for a token. |
| MSALEnabledLogPII | Bool | False | This setting controls whether MSAL provides the attached logger with personal data data. |

These settings are shared with all clients creating using the MSAL Authentication Provider. These settings are intended to be read from an `IConfiguration` reader, in from a configuration section a section called "MSALConfiguration".

Note

MSALConfiguration is an optional configuration. If you don't set this configuration, the default configurations for these values are used.

Here's an example of the entry in an `appsettings.json` file:

```json
{
  "MSALConfiguration": {
    "MSALEnabledLogPII": "true",
    "MSALRequestTimeout": "00:00:40",
    "MSALRetryCount": "1"
  },
}
```

In this case, this settings block would instruct all MSAL clients created with the MSAL provider to enabled personal data logging, set the timeout to 40 seconds, and reduce the retry count to 1.

This extension looks for a configuration section named "MSALConfiguration" in your `IConfiguration` object and create an MSAL Configuration object from it.

If the MSALConfig section is **not** found, it creates the MSAL Configuration Object using default values.

```csharp
    // Add default agent MsalAuth support
    builder.Services.AddDefaultMsalAuth(builder.Configuration);

    // Register your AgentApplication
    builder.AddAgent<MyAgent>();
```

## Logging support for authentication

The MSAL authentication system allows for independent logging of authentication flows for telemetry integration should you need to troubleshoot token acquisition.

To enable logging, add an entry for Microsoft.Agents.Authentication.Msal to your applications app settings to set up an `ILogger` to report on token operations for your connections. If you add the `MSALEnabledLogPII` option, this also includes personal data for your connection.

Here's an example of the logging block in this case:

```json
  "Logging": {
    "LogLevel": {
      "Default": "Warning",
      "Microsoft.Agents": "Warning",
      "Microsoft.Hosting.Lifetime": "Information",
      "Microsoft.Agents.Authentication.Msal": "Trace"
    }
  }
```

In this case, logging is enabled for several modules include Microsoft.Agents.Authentication.Msal, where the trace level is "Trace" for MSAL.

The JavaScript SDK requires an *AuthenticationProvider* to get JSON Web Tokens \(JWT\) to send activities to the target channel. For more information, see [Access tokens in the Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/access-tokens).

The `@microsoft/agents-hosting` package provides a default authentication provider based on Microsoft Authentication Library \(MSAL\). You can configure it for the following authentication types:

- Single-tenant with client secret
- Multitenant with client secret
- User-Managed Identity
- System-Managed Identity
- Federated credentials
- Workload identity
- Certificate

## Install the authentication package

Install the MSAL authentication package from npm:

```bash
npm install @microsoft/agents-hosting
```

## Single-tenant vs. multitenant

Client secret and client certificate authentication support both single-tenant and multitenant configurations.

User Assigned Managed Identity, System Managed Identity, Federated Credentials, and Workload Identity only support single-tenant configurations.

Note

For multitenant, you need to configure the Azure Bot instance as multitenant and the Microsoft Entra ID app registration as *Accounts in any organizational directory \(Any Microsoft Entra ID tenant - Multitenant\)*. To learn more, see [Single and multitenant apps](https://learn.microsoft.com/en-us/entra/identity-platform/single-and-multi-tenant-apps).

## Configure a connection

The MSAL authentication library enables you to create and use multiple distinct clients with the Agents Framework hosting engine. By using the MSAL authentication library, you can provide multiple connection configurations in the application configuration file. Each connection configuration can create a named authentication client to support communications with external services or other agents.

The following sections describe the required and optional configuration settings for each of the supported authentication types for the MSAL authentication provider. They also include example configuration snippets for each type.

## Environment variables for each authentication type

The agent obtains MSAL configuration at runtime from environment variables by using the helper function `loadAuthConfigFromEnv(): AuthConfiguration`. The `CloudAdapter` gets initialized with the `AuthConfiguration`.

Connection settings use the format `CONNECTIONS__<CONNECTION_NAME>__SETTINGS__<PROPERTY>`.

When `AUTHTYPE` is present, the SDK uses that value to select the token acquisition flow. When `AUTHTYPE` is omitted, the SDK falls back to the legacy behavior and infers the authentication flow from the configured credential properties.

## Single-tenant with client secret

Use these settings to configure a single-tenant connection that authenticates with a client secret.

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| CLIENTID | String | None | The client ID \(app ID\) of the app registration. |
| CLIENTSECRET | String | None | The secret associated with the app registration. Use only for testing and development purposes. |
| TENANTID | String | None | The Microsoft Entra ID tenant ID for the app registration. |
| AUTHTYPE | String | None | Set to `ClientSecret`. |
| SCOPE | String | None | Default resource scope to request tokens for when one isn't supplied by the caller. |
| AUTHORITY | String | None | When present, used as the authority to request a token from. If not set, defaults to `https://login.microsoftonline.com/{TENANTID}`. |

```env
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHTYPE=ClientSecret
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTID={app-id-guid}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTSECRET={app-registration-secret}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__TENANTID={tenant-id-guid}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__SCOPE=https://api.botframework.com
```

Single-tenant with client secret is the recommended configuration for local development.

## Multitenant with client secret

For multitenant scenarios that use a client secret, set the authority endpoint to the `botframework.com` tenant:

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| CLIENTID | String | None | The client ID \(app ID\) of the app registration. |
| CLIENTSECRET | String | None | The secret associated with the app registration. Use only for testing and development purposes. |
| AUTHTYPE | String | None | Set to `ClientSecret`. |
| AUTHORITY | String | None | Set to `https://login.microsoftonline.com/botframework.com` for multitenant. |
| SCOPE | String | None | Default resource scope to request tokens for when one isn't supplied by the caller. |

```env
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHTYPE=ClientSecret
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTID={app-id-guid}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTSECRET={app-registration-secret}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHORITY=https://login.microsoftonline.com/botframework.com
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__SCOPE=https://api.botframework.com
```

## UserManagedIdentity

Use these settings to configure token acquisition with a User Assigned Managed Identity.

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| CLIENTID | String | None | The managed identity client ID to use when creating the access token. |
| AUTHTYPE | String | None | Set to `UserManagedIdentity`. |
| SCOPE | String | None | Default resource scope to request tokens for when one isn't supplied by the caller. |

```env
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHTYPE=UserManagedIdentity
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTID={managed-identity-client-id}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__SCOPE=https://api.botframework.com
```

Managed Identity is the recommended configuration for production scenarios. To learn more, see [Managed identities for Azure resources](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview).

Note

If you use managed identity types, your host or client must run within an Azure service that is set up with either a system-assigned or user-assigned managed identity. To see which Azure services support managed identities, see [Managed identities for Azure resources](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/managed-identities-status).

## SystemManagedIdentity

If you use auth type `SystemManagedIdentity`, the client ID is ignored and the system-managed identity for the service is used.

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| AUTHTYPE | String | None | Set to `SystemManagedIdentity`. |
| SCOPE | String | None | Default resource scope to request tokens for when one isn't supplied by the caller. |

```env
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHTYPE=SystemManagedIdentity
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__SCOPE=https://api.botframework.com
```

Note

If you use managed identity types, your host or client must run within an Azure service that is set up with either a system-assigned or user-assigned managed identity. To see which Azure services support managed identities, see [Managed identities for Azure resources](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/managed-identities-status).

## FederatedCredentials

Use these settings to configure a single-tenant app that authenticates through Federated Credentials.

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| CLIENTID | String | None | The client ID \(app ID\) of the app registration. |
| TENANTID | String | None | The Microsoft Entra ID tenant ID for the app registration. |
| AUTHTYPE | String | None | Set to `FederatedCredentials`. |
| AUTHORITY | String | None | When present, used as the authority to request a token from. If not set, defaults to `https://login.microsoftonline.com/{TENANTID}`. |
| SCOPE | String | None | Default resource scope to request tokens for when one isn't supplied by the caller. |
| FICCLIENTID | String | None | The managed identity client ID used to obtain the external token for federated credentials. |

```env
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHTYPE=FederatedCredentials
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTID={app-id-guid}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__TENANTID={tenant-id-guid}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHORITY=https://login.microsoftonline.com/{tenant-id-guid}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__FICCLIENTID={managed-identity-client-id}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__SCOPE=https://api.botframework.com
```

For more information, see [Authentication using Federated Identity Credentials](https://learn.microsoft.com/en-us/azure/bot-service/bot-builder-authentication-federated-credential).

## WorkloadIdentity

Use these settings to configure token acquisition through Microsoft Entra Workload Identity.

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| AUTHTYPE | String | None | Set to `WorkloadIdentity`. |
| CLIENTID | String | None | The client ID \(app ID\) of the app registration. |
| TENANTID | String | None | The Microsoft Entra ID tenant ID for the app registration. |
| AUTHORITY | String | None | When present, used as the authority to request a token from. If not set, defaults to `https://login.microsoftonline.com/{TENANTID}`. |
| SCOPE | String | None | Default resource scope to request tokens for when one isn't supplied by the caller. |
| FEDERATEDTOKENFILE | String | None | Path to the federated token file provided by the workload identity environment. |

```env
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHTYPE=WorkloadIdentity
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTID={app-id-guid}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__TENANTID={tenant-id-guid}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHORITY=https://login.microsoftonline.com/{tenant-id-guid}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__FEDERATEDTOKENFILE=/var/run/secrets/azure/tokens/azure-identity-token
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__SCOPE=https://api.botframework.com
```

## Single tenant with client certificate

Use these settings to configure a single-tenant connection that authenticates with a client certificate.

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| CLIENTID | String | None | The client ID \(app ID\) of the app registration. |
| TENANTID | String | None | The Microsoft Entra ID tenant ID for the app registration. |
| AUTHTYPE | String | None | Set to `Certificate`. |
| CERTPEMFILE | String | None | Path to the Privacy-Enhanced Mail \(PEM\) certificate file. |
| CERTKEYFILE | String | None | Path to the private key file for the certificate. |
| SCOPE | String | None | Default resource scope to request tokens for when one isn't supplied by the caller. |
| AUTHORITY | String | None | When present, used as the authority to request a token from. |
| SENDX5C | Boolean | False | Enables sending the x5c header during certificate-based token acquisition. |

```env
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHTYPE=Certificate
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTID={app-id-guid}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__TENANTID={tenant-id-guid}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CERTPEMFILE={path-to-pem-file}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CERTKEYFILE={path-to-key-file}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__SCOPE=https://api.botframework.com
```

Note

The JS SDK reads the PEM certificate and private key files directly from disk and computes the certificate thumbprint automatically. The key file shouldn't use a password.

### Multitenant with client certificate

For multitenant scenarios that use client certificate, set the authority endpoint to the `botframework.com` tenant:

```env
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHTYPE=Certificate
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTID={app-id-guid}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CERTPEMFILE={path-to-pem-file}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CERTKEYFILE={path-to-key-file}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHORITY=https://login.microsoftonline.com/botframework.com
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__SCOPE=https://api.botframework.com
```

## Backward compatibility with Azure Bot Framework SDK

To load the configuration by using the same format as the Azure Bot Framework SDK, use `loadPrevAuthConfigFromEnv(): AuthConfiguration`.

Use these legacy setting names when migrating existing Bot Framework SDK configurations.

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| MicrosoftAppTenantId | String | Null | The Microsoft Entra ID tenant ID \(legacy Bot Framework SDK format\). |
| MicrosoftAppId | String | Null | The client ID \(app ID\) of the app registration \(legacy Bot Framework SDK format\). |
| MicrosoftAppPassword | String | Null | The app secret \(legacy Bot Framework SDK format\). |

```env
MicrosoftAppTenantId={tenant-id-guid}
MicrosoftAppId={app-id-guid}
MicrosoftAppPassword={app-registration-secret}
```

## Custom authentication provider

Users requiring a customized authentication provider can implement the interface:

```ts
export interface AuthProvider {
  getAccessToken: (authConfig: AuthConfiguration, scope: string) => Promise<string>
}
```

As an example, implement the `AuthProvider` by using `@azure/identity`:

```ts
import { EnvironmentCredential } from "@azure/identity"
import { AuthProvider, AuthConfiguration } from "@microsoft/agents-hosting"
class DevTokenProvider implements AuthProvider {
  async getAccessToken(authConfig: AuthConfiguration): Promise<string> {
    const id = new EnvironmentCredential()
    const tokenResponse = await id.getToken("https://api.botframework.com/.default")
    return tokenResponse.token
  }
```

To instantiate the `CloudAdapter` by using the `DevTokenProvider`

```ts
const adapter = new CloudAdapter(authConfig, new DevTokenProvider())
```

amework.com/.default"\) return tokenResponse.token }

~~~

To instantiate the `CloudAdapter` by using the `DevTokenProvider`

```ts
const adapter = new CloudAdapter(authConfig, new DevTokenProvider())
~~~

The Python Agents SDK Microsoft Authentication Library \(MSAL\) package provides you with tools that help you create access tokens for agent clients and external services from a Microsoft 365 Agents SDK self-hosted agent.

The `microsoft-agents-authentication-msal` package provides the `MsalAuth` class, which is the core authentication provider. You can configure it for the following types of credentials:

- Client secret
- Client certificate
- User-Assigned Managed Identity
- System-Assigned Managed Identity

## Install the authentication package

Install the MSAL authentication package from PyPI:

```bash
pip install microsoft-agents-authentication-msal
```

## Single-tenant vs multitenant

Client secret and client certificate authentication support both single-tenant and multitenant configurations.

User-Assigned Managed Identity and System-Assigned Managed Identity only support single-tenant configurations.

Note

For multitenant, you need to configure the Azure Bot instance as multitenant and the Microsoft Entra ID app registration as *Accounts in any organizational directory \(Any Microsoft Entra ID tenant - Multitenant\)*. To learn more, see [Single and multitenant apps](https://learn.microsoft.com/en-us/entra/identity-platform/single-and-multi-tenant-apps).

## Configure a connection

The MSAL authentication library lets you create and use multiple distinct clients with the Agents Framework hosting engine. Each connection configuration creates a named authentication client to support communications with external services or other agents.

Provide configuration through environment variables that use the double-underscore \(`__`\) naming convention for nested settings. The `MsalConnectionManager` class reads these variables to construct `AgentAuthConfiguration` instances for each named connection.

Important

The connection manager requires at minimum a connection named `SERVICE_CONNECTION`.

## Environment variables for each authentication type

The agent obtains MSAL configuration at runtime from environment variables using the helper function `load_configuration_from_env()`.

The following sections describe the required configuration settings for each of the supported authentication types, along with example environment variable snippets for each type.

## Single-tenant with client secret

Use these settings to configure a single-tenant connection that authenticates with a client secret.

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| CLIENTID | String | None | The client ID \(app ID\) of the app registration. |
| CLIENTSECRET | String | None | The secret associated with the app registration. Use only for testing and development purposes. |
| TENANTID | String | None | The Microsoft Entra ID tenant ID for the app registration. |
| AUTHTYPE | String | ClientSecret | The authentication type. Set to `ClientSecret`. |
| SCOPES | String list | None | Default list of scopes to request tokens for. Only used when no scopes are passed from the agent connection request. |
| AUTHORITY | String | None | When present, used as the authority to request a token from. If not set, defaults to `https://login.microsoftonline.com/{TENANTID}`. |

```env
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHTYPE=ClientSecret
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTID={app-id-guid}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTSECRET={app-registration-secret}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__TENANTID={tenant-id-guid}
```

Single-tenant with client secret is the recommended configuration for local development.

## Multitenant with client secret

For multitenant scenarios that use a client secret, set the authority endpoint to the `botframework.com` tenant:

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| CLIENTID | String | None | The client ID \(app ID\) of the app registration. |
| CLIENTSECRET | String | None | The secret associated with the app registration. Use only for testing and development purposes. |
| AUTHTYPE | String | ClientSecret | The authentication type. Set to `ClientSecret`. |
| AUTHORITY | String | None | Set to `https://login.microsoftonline.com/botframework.com` for multitenant. |
| SCOPES | String list | None | Default list of scopes to request tokens for. |

```env
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHTYPE=ClientSecret
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTID={app-id-guid}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTSECRET={app-registration-secret}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHORITY=https://login.microsoftonline.com/botframework.com
```

## User-Assigned Managed Identity

Use these settings to configure token acquisition with a user-assigned managed identity.

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| CLIENTID | String | None | The managed identity client ID to use when creating the access token. |
| AUTHTYPE | String | ClientSecret | The authentication type. Set to `UserManagedIdentity`. |

```env
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTID={managed-identity-client-id}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHTYPE=UserManagedIdentity
```

Managed Identity is the recommended configuration for production scenarios. To learn more, see [Managed identities for Azure resources](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview).

Note

If you use managed identity types, your host or client must run within an Azure service that is set up with either a system-assigned or user-assigned managed identity. To see which Azure services support managed identities, see [Managed identities for Azure resources](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/managed-identities-status).

## System-Assigned Managed Identity

If you use auth type `SystemManagedIdentity`, the client ID is ignored and the system-managed identity for the service is used.

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| AUTHTYPE | String | ClientSecret | The authentication type. Set to `SystemManagedIdentity`. |

```env
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHTYPE=SystemManagedIdentity
```

Note

If you use managed identity types, your host or client must run within an Azure service that is set up with either a system-assigned or user-assigned managed identity. To see which Azure services support managed identities, see [Managed identities for Azure resources](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/managed-identities-status).

## Single-tenant with client certificate

Use these settings to configure a single-tenant connection that authenticates with a client certificate.

| Setting Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| CLIENTID | String | None | The client ID \(app ID\) of the app registration. |
| TENANTID | String | None | The Microsoft Entra ID tenant ID for the app registration. |
| AUTHTYPE | String | ClientSecret | The authentication type. Set to `certificate`. |
| CERTPEMFILE | String | None | Path to the Privacy-Enhanced Mail \(PEM\) certificate file. |
| CERTKEYFILE | String | None | Path to the private key file for the certificate. |
| SCOPES | String list | None | Default list of scopes to request tokens for. |
| AUTHORITY | String | None | When present, used as the authority to request a token from. |

```env
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHTYPE=certificate
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTID={app-id-guid}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__TENANTID={tenant-id-guid}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CERTPEMFILE={path-to-pem-file}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CERTKEYFILE={path-to-key-file}
```

Note

The Python SDK reads the PEM certificate and private key files directly from disk and computes the certificate thumbprint automatically. The key file shouldn't use a password.

### Multitenant with client certificate

For multitenant scenarios that use client certificate, set the authority endpoint to the `botframework.com` tenant:

```env
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHTYPE=certificate
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTID={app-id-guid}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CERTPEMFILE={path-to-pem-file}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CERTKEYFILE={path-to-key-file}
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__AUTHORITY=https://login.microsoftonline.com/botframework.com
```

## Set up the connection manager

The `MsalConnectionManager` class can manage multiple authentication connections for your agent. It reads connection configurations and creates `MsalAuth` instances for each named connection.

Here's an example of how to set up the connection manager and start your agent:

```python
from os import environ

from microsoft_agents.hosting.aiohttp import start_agent_process, CloudAdapter
from microsoft_agents.hosting.core import Authorization, AgentApplication, TurnState, MemoryStorage

from dotenv import load_dotenv
from aiohttp.web import Request, Response, Application, run_app
from microsoft_agents.authentication.msal import MsalConnectionManager
from microsoft_agents.activity import load_configuration_from_env

def start_server(
    agent_application: AgentApplication, auth_configuration: AgentAuthConfiguration
):
    async def entry_point(req: Request) -> Response:
        agent: AgentApplication = req.app["agent_app"]
        adapter: CloudAdapter = req.app["adapter"]
        return await start_agent_process(req, agent, adapter)

    APP = Application()
    APP.router.add_post("/api/messages", entry_point)
    APP["agent_configuration"] = auth_configuration
    APP["agent_app"] = agent_application
    APP["adapter"] = agent_application.adapter

    try:
        run_app(APP, host="localhost", port=environ.get("PORT", 3978))
    except Exception as error:
        raise error

load_dotenv()
agents_sdk_config = load_configuration_from_env(environ)

STORAGE = MemoryStorage()
CONNECTION_MANAGER = MsalConnectionManager(**agents_sdk_config)
ADAPTER = CloudAdapter(connection_manager=CONNECTION_MANAGER)
AUTHORIZATION = Authorization(STORAGE, CONNECTION_MANAGER, **agents_sdk_config)

AGENT_APP = AgentApplication[TurnState](
    storage=STORAGE, adapter=ADAPTER, authorization=AUTHORIZATION, **agents_sdk_config
)

start_server(
    agent_application=AGENT_APP, auth_configuration=CONNECTION_MANAGER.get_default_connection_configuration()
)
```

See the [Python quickstart sample](https://github.com/microsoft/Agents/tree/main/samples/python/quickstart/src) for a complete example of using the `MsalConnectionManager` in a Python agent.

## Custom authentication provider

Users requiring a customized authentication provider can implement the `AccessTokenProviderBase` base class:

```python
from microsoft_agents.hosting.core import AccessTokenProviderBase

class CustomAuthProvider(AccessTokenProviderBase):
    async def get_access_token(
        self, resource_url: str, scopes: list[str], force_refresh: bool = False
    ) -> str:
        # Implement custom token acquisition logic
        token = await your_custom_token_logic(resource_url, scopes)
        return token
```

## Logging support for authentication

The MSAL authentication system uses the standard Python `logging` module under the logger name `microsoft_agents.authentication.msal`. To enable detailed logging of authentication flows for troubleshooting token acquisition, configure the logger in your application:

```python
import logging

logging.basicConfig(level=logging.WARNING)
logging.getLogger("microsoft_agents.authentication.msal").setLevel(logging.DEBUG)
```

## Security best practices

- Store secrets in Azure Key Vault or environment variables; never commit them to source code.
- Use managed identities when possible, as they eliminate the need to manage secrets.
- Regularly rotate client secrets and certificates.
- Use the least-privilege principle for scopes and permissions.
