<!-- Source: https://learn.microsoft.com/en-us/entra/msal/javascript/browser/mcp -->
<!-- Sitemap-Last-Modified: 2026-03-15 -->

# Use MCP flows with MSAL Browser

[Model Context Protocol \(MCP\)](https://modelcontextprotocol.io/) is an open standard that enables AI applications to connect securely with external tools, data sources, and services. MSAL Browser supports MCP flows by enforcing that all token requests include a `resource` parameter and caching access tokens keyed by that resource.

Note

MCP flows are supported for both standard browser applications using `PublicClientApplication` and Nested App Authentication \(NAA\) applications using `createNestablePublicClientApplication`.

For server-side implementations, see [MSAL Node MCP flows](https://learn.microsoft.com/en-us/entra/msal/javascript/node/mcp).

## Prerequisites

- [Register an application with the Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app)
- `@azure/msal-browser` v5 or later installed in your project

## Enabling MCP

Set `isMcp: true` in the `auth` configuration when creating your `PublicClientApplication`:

```javascript
const msalConfig = {
    auth: {
        clientId: "your-client-id",
        authority: "https://login.microsoftonline.com/common",
        isMcp: true,
    },
};

const pca = new msal.PublicClientApplication(msalConfig);
```

For NAA applications, use the same configuration with `createNestablePublicClientApplication`:

```javascript
const pca = await msal.createNestablePublicClientApplication(msalConfig);
```

## Resource parameter

When `isMcp` is `true`, every token request **must** include a `resource` parameter. Omitting it throws a `resource_parameter_required` error.

```javascript
const tokenRequest = {
    scopes: ["User.Read"],
    resource: "https://example.microsoft.com",
};
```

Important

Set the `resource` parameter directly on the request object. Don't pass it via `extraQueryParameters` or `extraParameters` at the same time as the `resource` property—doing so throws a `misplaced_resource_parameter` error.

The following example shows the correct and incorrect ways to set the `resource` parameter:

```javascript
// Correct
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

When `isMcp` is enabled, access tokens are cached with their associated resource. This behavior affects silent token acquisition:

- **Cache hit**: If a cached access token exists for the same scopes **and** resource, it's returned from the cache.
- **Cache miss**: If the requested resource doesn't match any cached token, MSAL falls back to the network to acquire a new token for the requested resource.

```javascript
// First request — acquires token from network
const token1 = await pca.acquireTokenSilent({
    scopes: ["User.Read"],
    resource: "https://resource-a.microsoft.com",
    account: account,
});

// Same resource — returns cached token
const token2 = await pca.acquireTokenSilent({
    scopes: ["User.Read"],
    resource: "https://resource-a.microsoft.com",
    account: account,
});

// Different resource — falls back to network
const token3 = await pca.acquireTokenSilent({
    scopes: ["User.Read"],
    resource: "https://resource-b.microsoft.com",
    account: account,
});
```

## Error handling

Two errors are specific to MCP flows:

| Error code | Description |
| --- | --- |
| `resource_parameter_required` | `isMcp` is `true` but the request doesn't include a `resource` parameter. |
| `misplaced_resource_parameter` | A `resource` was found both in the `resource` property and in `extraQueryParameters` or `extraParameters`. Use only one. |

Both errors are thrown as `ClientAuthError`. For more information, see the [errors documentation](https://learn.microsoft.com/en-us/entra/msal/javascript/browser/errors).

## Next steps

[Initialize applications](https://learn.microsoft.com/en-us/entra/msal/javascript/browser/initialization)

- [Acquire tokens](https://learn.microsoft.com/en-us/entra/msal/javascript/browser/acquire-token)
- [Caching in MSAL.js](https://learn.microsoft.com/en-us/entra/msal/javascript/browser/caching)
- [MSAL Node MCP flows](https://learn.microsoft.com/en-us/entra/msal/javascript/node/mcp)
