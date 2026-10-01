<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/configuration -->
<!-- Sitemap-Last-Modified: 2026-08-13 -->

# Configuration reference: Microsoft Entra ID Auth SDK \(sidecar\) settings

This guide provides configuration options for the Microsoft Entra ID Auth SDK \(sidecar\), a containerized authentication service that handles token acquisition and management for applications in containerized environments. The SDK simplifies identity integration by managing Microsoft Entra ID authentication, on-behalf-of \(OBO\) token flows, and downstream API calls without requiring applications to embed authentication libraries directly.

While this guide focuses on Kubernetes deployment patterns, the SDK can be deployed in any containerized environment including Docker, Azure Container Instances, and other container orchestration platforms.

If you're deploying to Azure Kubernetes Service \(AKS\), setting up development environments, or configuring production workloads, this reference covers configuration patterns, credential types, and environment variables needed to secure your applications with Microsoft Entra ID.

## Configuration overview

The Microsoft Entra ID Auth SDK \(sidecar\) is configured using configuration sources following ASP.NET Core conventions. Configuration values can be provided via multiple methods, including:

- Environment variables \(recommended for Kubernetes\)
- Entra ID configuration - `appsettings.json` file attached to the container, or embedded in the yaml file.
- Command-line arguments
- Azure App Configuration or Key Vault \(for advanced scenarios\)

## Core Entra ID settings

Microsoft Entra ID Auth SDK \(sidecar\) deployments require core Entra ID settings to authenticate incoming tokens and acquire tokens for downstream APIs. Use the appropriate client credentials in the following YAML format, typically as environment variables, to ensure secure authentication.

### Required configuration

First, configure the core Entra ID settings for the SDK to authenticate incoming tokens and acquire tokens for downstream APIs.

```yaml
env:
- name: AzureAd__Instance
  value: "https://login.microsoftonline.com/"
- name: AzureAd__TenantId
  value: "<your-tenant-id>"
- name: AzureAd__ClientId
  value: "<your-client-id>"
```

| Key | Description | Required | Default |
| --- | --- | --- | --- |
| `AzureAd__Instance` | Microsoft Entra authority URL | No | `https://login.microsoftonline.com/` |
| `AzureAd__TenantId` | Your Microsoft Entra tenant ID | Yes | - |
| `AzureAd__ClientId` | Application \(client\) ID | Yes | - |
| `AzureAd__Audience` | Expected audience in incoming tokens | No | `api://{ClientId}` |
| `AzureAd__Scopes` | Required scopes for incoming tokens \(space-separated\) | No | - |

Note

The expected audience value depends on your app registration's [**requestedAccessTokenVersion**](https://learn.microsoft.com/en-us/entra/identity-platform/reference-app-manifest#requestedaccesstokenversion-attribute):

- **Version 2**: Use the `{ClientId}` value directly
- **Version 1** or **null**: Use the App ID URI \(typically `api://{ClientId}` unless you customized it\)

## Client credentials configuration

The Microsoft Entra ID Auth SDK \(sidecar\) supports multiple client credential types for authenticating with Microsoft Entra ID when acquiring tokens for downstream APIs. Choose the credential type that best fits your deployment environment and security requirements, and ensure that the configuration you choose is appropriate for your scenario.

Each credential type serves different scenarios:

- **Client Secret**: Simple setup for development and testing \(not recommended for production\)
- **Key Vault Certificate**: Production environments with centralized certificate management
- **File Certificate**: When certificates are mounted as files \(e.g., via Kubernetes secrets\)
- **Certificate Store**: Windows environments with certificate stores
- **Workload Identity for Containers**: Recommended for AKS, using Microsoft Entra Workload ID with file-based token projection
- **Managed Identity for VMs/App Services**: Azure Virtual Machines and App Services with system or user-assigned managed identities \(not for containers\)

Configure one or more credential sources in the following YAML format:

### Choose a credential by environment

Select the credential based on where the sidecar runs. Both `SignedAssertionFilePath` and `SignedAssertionFromManagedIdentity` are federated identity credentials \(FIC\). They differ in how the sidecar obtains the signed assertion.

| Environment | `SourceType` | Notes |
| --- | --- | --- |
| Azure Kubernetes Service \(AKS\) | `SignedAssertionFilePath` | The Azure Workload Identity webhook projects and rotates the token. |
| Non-Azure or on-premises Kubernetes | `SignedAssertionFilePath` | You set the projected token path. This is supported through workload identity federation. |
| Azure VMs, App Service, or Container Apps with managed identity | `SignedAssertionFromManagedIdentity` | Uses Azure Managed Identity through IMDS. Azure-only. |
| Docker or any host without an OIDC issuer | `KeyVault`, `Path`, or `StoreWithThumbprint` | Use a certificate when the platform can't project an OIDC token. |
| Development or testing | `ClientSecret` | Not recommended for production. |

**Important**: `SignedAssertionFromManagedIdentity` isn't a general-purpose Kubernetes credential, and it isn't a fallback for `SignedAssertionFilePath`. It uses Azure Managed Identity and probes Azure hosting environments such as Service Fabric, App Service, and IMDS. On a non-Azure host, it finds none of these, and the request eventually times out against IMDS. If your sidecar unexpectedly reaches IMDS, you selected this source type. Use `SignedAssertionFilePath` instead.

### Client secret

This configuration sets up Entra ID authentication using a client secret for service-to-service authentication.

```yaml
- name: AzureAd__ClientCredentials__0__SourceType
  value: "ClientSecret"
- name: AzureAd__ClientCredentials__0__ClientSecret
  value: "<your-client-secret>"
```

### Certificate from Key Vault

This configuration sets up Entra ID authentication using a certificate stored in Azure Key Vault.

```yaml
- name: AzureAd__ClientCredentials__0__SourceType
  value: "KeyVault"
- name: AzureAd__ClientCredentials__0__KeyVaultUrl
  value: "https://<your-keyvault>.vault.azure.net"
- name: AzureAd__ClientCredentials__0__KeyVaultCertificateName
  value: "<certificate-name>"
```

### Certificate from file

This configuration sets up Entra ID authentication using a certificate stored as a file.

```yaml
- name: AzureAd__ClientCredentials__0__SourceType
  value: "Path"
- name: AzureAd__ClientCredentials__0__CertificateDiskPath
  value: "/path/to/certificate.pfx"
- name: AzureAd__ClientCredentials__0__CertificatePassword
  value: "<certificate-password>"
```

### Certificate from store

This configuration sets up Entra ID authentication using a certificate from the local certificate store.

```yaml
- name: AzureAd__ClientCredentials__0__SourceType
  value: "StoreWithThumbprint"
- name: AzureAd__ClientCredentials__0__CertificateStorePath
  value: "CurrentUser/My"
- name: AzureAd__ClientCredentials__0__CertificateThumbprint
  value: "<thumbprint>"
```

### Workload Identity on AKS \(recommended for AKS\)

This configuration sets up Entra ID authentication using Microsoft Entra Workload ID on AKS. This is the recommended approach on AKS because the Azure Workload Identity webhook projects and rotates the token for you.

```yaml
- name: AzureAd__ClientCredentials__0__SourceType
  value: "SignedAssertionFilePath"
```

**Note**: On AKS, the token file path `/var/run/secrets/azure/tokens/azure-identity-token` or an environment variable is automatically projected by the Azure Workload Identity webhook when your pod is properly configured with the service account annotation and pod label. See [Using Managed Identity](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/managed-identity) for complete setup instructions.

### Workload Identity for non-Azure or on-premises Kubernetes

The Agent Identity flow isn't limited to AKS. Any Kubernetes platform, including on-premises and other clouds, can use `SignedAssertionFilePath` with workload identity federation. Because there's no Azure Workload Identity webhook outside AKS, you point the sidecar at the projected service account token that your platform mounts.

```yaml
- name: AzureAd__ClientCredentials__0__SourceType
  value: "SignedAssertionFilePath"
- name: AzureAd__ClientCredentials__0__SignedAssertionFileDiskPath
  value: "/var/run/secrets/tokens/sa-token"
```

The sidecar rereads the file on each token request, so platform-driven rotation of the projected assertion is supported automatically.

To use this credential on non-Azure Kubernetes, your environment must meet these prerequisites:

- Your Kubernetes platform projects a service account token into the sidecar pod, for example through a projected `serviceAccountToken` volume.
- The cluster exposes a publicly reachable OIDC issuer and JWKS endpoint so that Microsoft Entra can validate the assertion.
- A federated identity credential \(FIC\) is configured on the Blueprint application, with the issuer and subject that match the projected token.

If your platform can't provide a projected OIDC token or a public issuer, use a certificate credential such as [Certificate from Key Vault](#certificate-from-key-vault) or [Certificate from file](#certificate-from-file) instead.

### Managed Identity for VMs and App Services

For classic Azure Managed Identity scenarios on Virtual Machines or App Services \(not containers\), use `SignedAssertionFromManagedIdentity`:

```yaml
- name: AzureAd__ClientCredentials__0__SourceType
  value: "SignedAssertionFromManagedIdentity"
- name: AzureAd__ClientCredentials__0__ManagedIdentityClientId
  value: "<managed-identity-client-id>"
```

**Important**: Do not use `SignedAssertionFromManagedIdentity` in non-Azure or on-premises environments. It uses Azure Managed Identity through IMDS and works only on Azure compute that provides managed identity. On a non-Azure host, it probes Azure hosting endpoints and then times out against IMDS, which can look like the SDK being hardcoded to IMDS. For Kubernetes anywhere, including AKS, use `SignedAssertionFilePath`. For details, see [https://aka.ms/idweb/client-credentials](https://aka.ms/idweb/client-credentials)

### Additional resources

For complete details on all credential configuration options and their usage, see the [CredentialDescription specification](https://github.com/AzureAD/microsoft-identity-abstractions-for-dotnet/blob/main/docs/credentialdescription.md) in the microsoft-identity-abstractions-for-dotnet repository.

## Credentials priority

Configure multiple credentials with priority-based selection:

```yaml
# First priority - Key Vault certificate
- name: AzureAd__ClientCredentials__0__SourceType
  value: "KeyVault"
- name: AzureAd__ClientCredentials__0__KeyVaultUrl
  value: "https://prod-keyvault.vault.azure.net"
- name: AzureAd__ClientCredentials__0__KeyVaultCertificateName
  value: "prod-cert"

# Second priority - Client secret (fallback)
- name: AzureAd__ClientCredentials__1__SourceType
  value: "ClientSecret"
- name: AzureAd__ClientCredentials__1__ClientSecret
  valueFrom:
    secretKeyRef:
      name: app-secrets
      key: client-secret
```

The Microsoft Entra ID Auth SDK \(sidecar\) evaluates credentials in numerical order \(0, 1, 2, etc.\) and uses the first credential that successfully authenticates.

## Downstream APIs configuration

Configure downstream APIs that your application needs to call using on-behalf-of \(OBO\) token flows. The Microsoft Entra ID Auth SDK \(sidecar\) manages token acquisition and provides authentication headers for these API calls. Each downstream API requires a unique configuration name and specific parameters for token acquisition and HTTP request handling.

Define each downstream API with its base URL, required scopes, and optional parameters. The SDK will automatically handle token acquisition using the incoming user token and provide the appropriate authorization headers for your application's API calls.

```yaml
- name: DownstreamApis__Graph__BaseUrl
  value: "https://graph.microsoft.com/v1.0"
- name: DownstreamApis__Graph__Scopes
  value: "User.Read Mail.Read"
- name: DownstreamApis__Graph__RelativePath
  value: "/me"

- name: DownstreamApis__MyApi__BaseUrl
  value: "https://api.contoso.com"
- name: DownstreamApis__MyApi__Scopes
  value: "api://myapi/.default"
```

| Key Pattern | Description | Required |
| --- | --- | --- |
| `DownstreamApis__<Name>__BaseUrl` | Base URL of the API | Yes |
| `DownstreamApis__<Name>__Scopes` | Space-separated scopes to request | Yes |
| `DownstreamApis__<Name>__HttpMethod` | Default HTTP method | No \(GET\) |
| `DownstreamApis__<Name>__RelativePath` | Default relative path | No |
| `DownstreamApis__<Name>__RequestAppToken` | Use app token instead of OBO | No \(false\) |

## Token acquisition options

Fine-tune token acquisition behavior:

```yaml
- name: DownstreamApis__Graph__AcquireTokenOptions__Tenant
  value: "<specific-tenant-id>"

- name: DownstreamApis__Graph__AcquireTokenOptions__AuthenticationScheme
  value: "Bearer"

- name: DownstreamApis__Graph__AcquireTokenOptions__CorrelationId
  value: "<correlation-id>"
```

## Signed HTTP request \(SHR\) configuration for outbound token acquisition

Enable Signed HTTP Requests for enhanced security:

```yaml
- name: DownstreamApis__SecureApi__AcquireTokenOptions__PopPublicKey
  value: "<base64-encoded-public-key>"

- name: DownstreamApis__SecureApi__AcquireTokenOptions__PopClaims
  value: '{"custom_claim": "value"}'
```

## Logging configuration

Configure logging levels:

```yaml
- name: Logging__LogLevel__Default
  value: "Information"
- name: Logging__LogLevel__Microsoft.Identity.Web
  value: "Debug"
- name: Logging__LogLevel__Microsoft.AspNetCore
  value: "Warning"
```

## ASP.NET Core settings

```yaml
- name: ASPNETCORE_ENVIRONMENT
  value: "Production"
- name: ASPNETCORE_URLS
  value: "http://+:5000"
```

## Per-Request configuration overrides

All token acquisition endpoints accept query parameters to override configuration:

```bash
# Override scopes
GET /AuthorizationHeader/Graph?optionsOverride.Scopes=User.Read&optionsOverride.Scopes=Mail.Read

# Request app token instead of OBO
GET /AuthorizationHeader/Graph?optionsOverride.RequestAppToken=true

GET /AuthorizationHeaderUnauthenticated/Graph?optionsOverride.RequestAppToken=true

# Override tenant
GET /AuthorizationHeader/Graph?optionsOverride.AcquireTokenOptions.Tenant=<tenant-id>

# Override relative path
GET /DownstreamApi/Graph?optionsOverride.RelativePath=me/messages

# Enable SHR for this request
GET /AuthorizationHeader/Graph?optionsOverride.AcquireTokenOptions.PopPublicKey=<base64-key>
```

## Agent Identity overrides

Specify agent identity at request time:

```bash
# Autonomous agent
GET /AuthorizationHeader/Graph?AgentIdentity=<agent-client-id>

# Autonomous agent with specific agent user identity (by username)
GET /AuthorizationHeader/Graph?AgentIdentity=<agent-client-id>&AgentUsername=user@contoso.com

# Autonomous agent with specific agent user identity (by object ID)
GET /AuthorizationHeader/Graph?AgentIdentity=<agent-client-id>&AgentUserId=<user-object-id>
```

**Important Rules:**

- `AgentUsername` and `AgentUserId` require `AgentIdentity`
- `AgentUsername` and `AgentUserId` are mutually exclusive

See [Agent Identities](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/agent-identities) for detailed semantics.

## Complete configuration example

The following provides a production-ready example showing how to deploy the SDK with proper separation of configuration and secrets. This example demonstrates configuring multiple downstream APIs, using Kubernetes ConfigMaps for non-sensitive settings, storing credentials securely in Secrets, and applying environment-specific configurations for secure deployment.

This pattern follows Kubernetes best practices by separating configuration data from sensitive credentials, enabling effective management of different environments while maintaining security.

### Kubernetes ConfigMap

The ConfigMap stores non-sensitive configuration settings for the SDK, including Entra ID settings, downstream APIs, and logging levels.

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: sidecar-config
data:
  ASPNETCORE_ENVIRONMENT: "Production"
  ASPNETCORE_URLS: "http://+:5000"
  
  AzureAd__Instance: "https://login.microsoftonline.com/"
  AzureAd__TenantId: "common"
  AzureAd__ClientId: "your-app-client-id"
  AzureAd__Scopes: "access_as_user"
  
  DownstreamApis__Graph__BaseUrl: "https://graph.microsoft.com/v1.0"
  DownstreamApis__Graph__Scopes: "User.Read Mail.Read"
  
  DownstreamApis__MyApi__BaseUrl: "https://api.contoso.com"
  DownstreamApis__MyApi__Scopes: "api://myapi/.default"
  
  Logging__LogLevel__Default: "Information"
  Logging__LogLevel__Microsoft.Identity.Web: "Debug"
```

### Kubernetes secret

The Secret stores sensitive credentials, such as client secrets, separately from the ConfigMap.

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: sidecar-secrets
type: Opaque
stringData:
  AzureAd__ClientCredentials__0__ClientSecret: "your-client-secret"
```

### Deployment with ConfigMap and secret

The Deployment mounts both the ConfigMap and Secret into the SDK container, ensuring that configuration and credentials are properly separated.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp
spec:
  template:
    spec:
      containers:
      - name: sidecar
        image: mcr.microsoft.com/entra-sdk/auth-sidecar:1.0.0
        envFrom:
        - configMapRef:
            name: sidecar-config
        - secretRef:
            name: sidecar-secrets
```

## Environment-specific configuration

Configure environment-specific settings to tailor security, logging, and tenant isolation for your deployment environments. Each environment requires different configuration approaches to balance development efficiency, staging validation, and production security requirements.

### Development

```yaml
- name: ASPNETCORE_ENVIRONMENT
  value: "Development"
- name: Logging__LogLevel__Default
  value: "Debug"
- name: AzureAd__TenantId
  value: "<dev-tenant-id>"
```

### Staging

```yaml
- name: ASPNETCORE_ENVIRONMENT
  value: "Staging"
- name: Logging__LogLevel__Default
  value: "Information"
- name: AzureAd__TenantId
  value: "<staging-tenant-id>"
```

### Production

```yaml
- name: ASPNETCORE_ENVIRONMENT
  value: "Production"
- name: Logging__LogLevel__Default
  value: "Warning"
- name: Logging__LogLevel__Microsoft.Identity.Web
  value: "Information"
- name: AzureAd__TenantId
  value: "<prod-tenant-id>"
- name: ApplicationInsights__ConnectionString
  value: "<app-insights-connection>"
```

## Validation

The Microsoft Entra ID Auth SDK \(sidecar\) validates configuration at startup and logs errors for:

- Missing required settings \(`TenantId`, `ClientId`\)
- Invalid credential configurations
- Malformed downstream API definitions
- Invalid URLs or scope formats

Check container logs for validation messages:

```bash
kubectl logs <pod-name> -c sidecar
```

## Troubleshooting credentials

### Requests unexpectedly reach IMDS or time out

**Symptom**: The sidecar hangs or times out acquiring a downstream token, and logs show requests to the IMDS endpoint \(`169.254.169.254`\), even on a non-Azure host.

**Cause**: The credential is configured as `SignedAssertionFromManagedIdentity`. That source type intentionally probes Azure hosting environments and IMDS, which don't exist outside Azure. This is a configuration choice, not a fallback from `SignedAssertionFilePath`.

**Resolution**:

1. Confirm that the effective `SourceType` is `SignedAssertionFilePath`, not `SignedAssertionFromManagedIdentity`.
2. Check that no environment variable or ConfigMap override reintroduces `SignedAssertionFromManagedIdentity`.
3. Verify that `SignedAssertionFileDiskPath` points to the projected token that's mounted in the sidecar container.
4. On non-Azure Kubernetes, confirm that the cluster's OIDC issuer and JWKS are publicly reachable, and that a matching FIC exists on the Blueprint application.

When you report a persistent issue, capture the sidecar version, the effective runtime configuration, and the container logs from one failing request.

## Best practices

1. **Use Secrets for Credentials**: Store client secrets and certificates in Kubernetes Secrets or Azure Key Vault. See also [https://aka.ms/msidweb/client-credentials](https://aka.ms/msidweb/client-credentials)
2. **Separate Configuration per Environment**: Use ConfigMaps to manage environment-specific settings
3. **Enable Appropriate Logging**: Use Debug logging in development, Information/Warning in production
4. **Configure Health Checks**: Ensure health check endpoints are properly configured
5. **Use Workload Identity for Containers**: For containerized deployments \(AKS\), prefer Microsoft Entra Workload ID with `SignedAssertionFilePath` over client secrets for enhanced security
6. **Use Managed Identity for VMs/App Services**: For Azure VMs and App Services, use system or user-assigned managed identities
7. **Validate at Deploy Time**: Test configuration in staging before production deployment

## Related content

- [Agent Identities](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/agent-identities)
- [Endpoints Reference](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/endpoints)
- [Security Best Practices](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/security)
- [Troubleshooting](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/troubleshooting)
