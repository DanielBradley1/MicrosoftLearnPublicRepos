<!-- Source: https://learn.microsoft.com/en-us/entra/msal/javascript/node/mcp -->
<!-- Sitemap-Last-Modified: 2026-03-15 -->

# Use MCP flows with MSAL Node

When building [Model Context Protocol \(MCP\)](https://modelcontextprotocol.io/) applications, you can configure MSAL Node to enforce resource-scoped token acquisition and caching. When MCP mode is enabled, MSAL requires every token request to include a `resource` parameter and caches access tokens keyed by that resource.

Note

MCP flows are available for public client applications only.

## Prerequisites

- [Register an application with the Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app)
- An application configured as a public client \(for example, a desktop or CLI application\)
- `@azure/msal-node` v5 or later installed in your project

## Enable MCP mode

Set `isMcp: true` in the `auth` configuration when creating your `PublicClientApplication`:

```javascript
const config = {
    auth: {
        clientId: "your-client-id",
        authority: "https://login.microsoftonline.com/common",
        isMcp: true,
    },
};

const pca = new msal.PublicClientApplication(config);
```

## Include the resource parameter

When `isMcp` is `true`, every token request **must** include a `resource` parameter. Omitting it throws a `resource_parameter_required` error.

```javascript
const tokenRequest = {
    scopes: ["User.Read"],
    redirectUri: "http://localhost:3000/redirect",
    resource: "https://example.microsoft.com",
    code: authorizationCode,
};

const response = await pca.acquireTokenByCode(tokenRequest);
```

Important

Set the `resource` parameter directly on the request object. Do **not** pass it via `extraQueryParameters` at the same time as the `resource` property — doing so throws a `misplaced_resource_parameter` error.

The following example shows the correct and incorrect ways to set the `resource` parameter:

```javascript
// Correct — resource on the request object
const request = {
    scopes: ["User.Read"],
    resource: "https://example.microsoft.com",
};

// Wrong — resource in both locations
const request = {
    scopes: ["User.Read"],
    resource: "https://example.microsoft.com",
    extraQueryParameters: { resource: "https://example.microsoft.com" },
};
```

## Resource-scoped caching

When `isMcp` is enabled, access tokens are cached with their associated resource. This affects silent token acquisition:

- **Cache hit**: If a cached access token exists for the same scopes **and** resource, it's returned from cache.
- **Cache miss**: If the requested resource doesn't match any cached token, MSAL falls back to the network to acquire a new token for the requested resource.

```javascript
const msalTokenCache = pca.getTokenCache();
const accounts = await msalTokenCache.getAllAccounts();

// First request — acquires token from network
const token1 = await pca.acquireTokenSilent({
    scopes: ["User.Read"],
    resource: "https://resource-a.microsoft.com",
    account: accounts[0],
});

// Same resource — returns cached token
const token2 = await pca.acquireTokenSilent({
    scopes: ["User.Read"],
    resource: "https://resource-a.microsoft.com",
    account: accounts[0],
});

// Different resource — falls back to network
const token3 = await pca.acquireTokenSilent({
    scopes: ["User.Read"],
    resource: "https://resource-b.microsoft.com",
    account: accounts[0],
});
```

## Error handling

Two errors are specific to MCP flows:

| Error code | Description |
| --- | --- |
| `resource_parameter_required` | `isMcp` is `true` but the request doesn't include a `resource` parameter. |
| `misplaced_resource_parameter` | A `resource` was found both in the `resource` property and in `extraQueryParameters`. Use only one. |

Both errors are thrown as `ClientAuthError`. For more information, see [MSAL Node FAQs](https://learn.microsoft.com/en-us/entra/msal/javascript/node/faq).

## Samples

- [MCP Flows Sample](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/samples/msal-node-samples/mcp-flows) — Express app demonstrating MCP with authorization code and silent flows.

## Next steps

[Initialize public client applications](https://learn.microsoft.com/en-us/entra/msal/javascript/node/initialize-public-client-application)

- [Supported authorization code grants](https://learn.microsoft.com/en-us/entra/msal/javascript/node/acquire-token-requests)
- [Token caching in MSAL Node](https://learn.microsoft.com/en-us/entra/msal/javascript/node/caching)
- [MSAL Node FAQs](https://learn.microsoft.com/en-us/entra/msal/javascript/node/faq)
