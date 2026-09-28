<!-- Source: https://learn.microsoft.com/en-us/entra/msal/python/advanced/managed-identity -->
<!-- Sitemap-Last-Modified: 2024-06-29 -->

# Using Managed Identity

[Managed identity](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview) enables developers to remove the need to store, rotate, and otherwise handle credentials for their applications running in the Microsoft Azure cloud. Microsoft Authentication Library \(MSAL\) for Python supports using authentication with managed identity on supported Azure workloads.

Note

Managed Identity in MSAL Python is supported since version [1.29.0](https://pypi.org/project/msal/1.29.0/) of the [`msal` package](https://pypi.org/project/msal/).

MSAL Python supports acquiring tokens through the managed identity service when used with applications running inside Azure infrastructure, such as:

- [Azure App Service](https://azure.microsoft.com/products/app-service/) \(API version `2019-08-01`\)
- [Azure VMs](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn)
- [Azure Arc](https://learn.microsoft.com/en-us/azure/azure-arc/overview)
- [Azure Cloud Shell](https://learn.microsoft.com/en-us/azure/cloud-shell/overview)
- [Azure Service Fabric](https://learn.microsoft.com/en-us/azure/service-fabric/service-fabric-overview)
- [Azure ML](https://learn.microsoft.com/en-us/azure/machine-learning/how-to-identity-based-service-authentication)

For a complete list, refer to [Azure services that can use managed identities to access other services](https://learn.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/managed-identities-status).

## Which SDK to use - Azure SDK or MSAL?

MSAL libraries provide lower level APIs that are closer to the OAuth2 and OIDC protocols.

Both MSAL Python and Azure SDK allow to acquire tokens via managed identity. Internally, Azure SDK uses MSAL Python, and it provides a higher-level API via its [`DefaultAzureCredential`](https://learn.microsoft.com/en-us/python/api/azure-identity/azure.identity.defaultazurecredential) and [`ManagedIdentityCredential`](https://learn.microsoft.com/en-us/python/api/azure-identity/azure.identity.ManagedIdentityCredential) abstractions.

If your application already uses one of the SDKs, continue using the same SDK.

- Use Azure SDK if you are writing a new application and plan to call other Azure resources, as this SDK provides a better developer experience by allowing the app to run on private developer machines where managed identity doesn't exist.
- Use MSAL if you need to call other downstream web APIs like Microsoft Graph or your own web API.

## How to use managed identities

There are two types of managed identities available to developers - **system-assigned** and **user-assigned**. You can learn more about the differences in the [Managed identity types](https://learn.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/overview#managed-identity-types) article. MSAL Python supports acquiring tokens with both. MSAL Python logging allows to keep track of requests and related metadata.

Prior to using managed identities from MSAL Python, developers must enable them for the resources they want to use through Azure CLI or the Azure Portal.

## Examples

In both system- and user-assigned identities, developers need to use [ManagedIdentityClient](https://learn.microsoft.com/en-us/python/api/msal/msal.managed_identity.managedidentityclient) to access managed identities.

### System-assigned managed identities

System-assigned managed identities can be used by instantiating [SystemAssignedManagedIdentity](https://learn.microsoft.com/en-us/python/api/msal/msal.managed_identity.systemassignedmanagedidentity) and passing to [ManagedIdentityClient](https://learn.microsoft.com/en-us/python/api/msal/msal.managed_identity.managedidentityclient).

Note

You need to include a `http_client` reference, which can be set to `requests.Session()`. This enables MSAL to maintain a pool of connections to the IMDS endpoint.

You can specify the target resource scope when calling [`acquire_token_for_client`](https://learn.microsoft.com/en-us/python/api/msal/msal.managed_identity.managedidentityclient#msal-managed-identity-managedidentityclient-acquire-token-for-client).

```python
import msal
import requests

managed_identity = msal.SystemAssignedManagedIdentity()

global_app = msal.ManagedIdentityClient(managed_identity, http_client=requests.Session())

result = global_app.acquire_token_for_client(resource='https://vault.azure.net')

if "access_token" in result:
    print("Token obtained!")
```

Important

You need to enable a system-assigned identity for the resource where the Python code runs; otherwise, no token will be returned.

### User-assigned managed identities

User-assigned managed identities can be used by instantiating [UserAssignedManagedIdentity](https://learn.microsoft.com/en-us/python/api/msal/msal.managed_identity.userassignedmanagedidentity) and passing to [ManagedIdentityClient](https://learn.microsoft.com/en-us/python/api/msal/msal.managed_identity.managedidentityclient). You will need to specify the **one of the following**:

- Client ID \(`client_id`\)
- Resource ID \(`resource_id`\)
- Object ID \(`object_id`\)

Note

You need to include a `http_client` reference, which can be set to `requests.Session()`. This enables MSAL to maintain a pool of connections to the IMDS endpoint.

You can specify the target resource scope when calling [`acquire_token_for_client`](https://learn.microsoft.com/en-us/python/api/msal/msal.managed_identity.managedidentityclient#msal-managed-identity-managedidentityclient-acquire-token-for-client).

```python
import msal
import requests

managed_identity = msal.UserAssignedManagedIdentity(client_id='YOUR_CLIENT_ID')

global_app = msal.ManagedIdentityClient(managed_identity, http_client=requests.Session())

result = global_app.acquire_token_for_client(resource='https://vault.azure.net')

if "access_token" in result:
    print("Token obtained!")
```

Note

MSAL Python's [built-in managed identity sample](https://github.com/AzureAD/microsoft-authentication-library-for-python/blob/1.29.0/sample/managed_identity_sample.py#L38-L42) showcases how user-assigned managed identity can be inferred from environment variables. It's an advanced usage pattern that can be used instead of explicit definition of the client ID in code.

Important

You need to attach a user-assigned identity for the resource where the Python code runs; otherwise, no token will be returned. If an incorrect identifier is used for the user-assigned managed identity, no token will be returned as well.

## Caching

By default, MSAL Python supports in-memory caching.

Important

MSAL Python also supports cache extensibility for managed identity, so that you may persist the token cache on disk. This can be useful if you are writing a command-line script and a few other limited scenarios. We **do not recommend** sharing managed identity token cache among multiple machines as this can result in unexpected access behaviors for users of the cache. A token acquired for a node/machine, if cached in a distributed cache, can be used for another machine for which it is not intended.
