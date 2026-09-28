<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-authentication-none -->
<!-- Sitemap-Last-Modified: 2026-07-16 -->

# Configure anonymous authentication

For Model Context Protocol \(MCP\) servers or APIs that don't require any authentication, or for developer environments where authentication isn't yet implemented, plugins can access the MCP server or API anonymously.

This article uses MCP plugins as the default walkthrough. The same steps apply to API plugins built from an OpenAPI document, except where noted.

Unlike the other authentication schemes, anonymous access requires no registration, credentials, or auth config - you set the authentication type to `None` directly in the plugin manifest.

## Add anonymous authentication to the plugin manifest

When you add an MCP server that requires no authentication in Microsoft 365 Agents Toolkit or through the declarative agent developer skill, the plugin manifest is set to `None` for you. Set it manually only when you edit an existing plugin manifest yourself.

To configure anonymous access, set the `type` property of the [runtime authentication object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-manifest-2.4#runtime-authentication-object) to `None`.

```json
"auth": {
  "type": "None"
},
```

Note

Anonymous access is intended for development and testing. Add authentication before you deploy your plugin to production.

## Related content

- [Configure authentication for MCP and API plugins in agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-authentication)
- [Configure OAuth 2.0 authentication](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-authentication-oauth)
- [Configure Microsoft Entra SSO authentication](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-authentication-entra-sso)
- [Troubleshoot MCP and API plugin authentication](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-authentication-troubleshooting)
