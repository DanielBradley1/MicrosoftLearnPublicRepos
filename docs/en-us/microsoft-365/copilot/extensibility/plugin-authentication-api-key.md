<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-authentication-api-key -->
<!-- Sitemap-Last-Modified: 2026-07-16 -->

# Configure API key authentication

Tip

**Recommended:** Start with [Work IQ Dev Tools](https://aka.ms/wiqd/docs) for supported pro-code declarative-agent and plugin scenarios. See the [WIQD quickstart](https://microsoft.github.io/wiqd/getting-started/quickstart/). Toolkit-based instructions remain available for existing projects and workflows that require them. Check [capability and target-experience support](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/choose-plugin-development-tools) before choosing a tool: WIQD doesn't target custom engine agents.

Some APIs use API keys for authorization. An API key is a shared secret that the client includes in API requests to authenticate and gain access. API plugins support sending the API key in three ways:

- As a bearer token in the `Authorization` header
- As a value in a custom header
- As a query parameter

Note

For declarative-agent actions, API key authentication applies to API plugins built from an OpenAPI document, not MCP plugins. For an agent's MCP plugin, use [OAuth 2.0](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-authentication-oauth) \(including [dynamic client registration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-authentication-dynamic-client-registration)\) or [Microsoft Entra SSO](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-authentication-entra-sso). A package-level remote MCP connection uses a different configuration; see [authentication in the app manifest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/configure-plugin-mcp-servers#configure-authentication).

Configure API key authentication in two steps: add the API key to your OpenAPI document and create the API key auth config.

## Step 1: Add the API key to your OpenAPI document

Microsoft 365 Copilot determines how to send the API key based on the `securitySchemes` entry in your OpenAPI document.

### Bearer token

If your API accepts the API key as a bearer token, enable Bearer authentication in your OpenAPI document. For more information, see [Bearer authentication](https://swagger.io/docs/specification/v3_0/authentication/bearer-authentication/).

```yml
securitySchemes:
  BearerAuth:
    type: http
    scheme: bearer
```

### Custom header

If your API accepts the API key in a custom header, enable API key authentication in your OpenAPI document with the `in` property set to `header` and the `name` property set to the header name. For more information, see [API Keys](https://swagger.io/docs/specification/v3_0/authentication/api-keys/).

```yml
securitySchemes:
  ApiKeyAuth:
    type: apiKey
    in: header
    name: X-API-KEY
```

### Query parameter

If your API accepts the API key in a query parameter, enable API key authentication in your OpenAPI document by setting the `in` property to `query` and the `name` property to the name of the query parameter. For more information, see [API Keys](https://swagger.io/docs/specification/v3_0/authentication/api-keys/).

```yml
securitySchemes:
  ApiKeyAuth:
    type: apiKey
    in: query
    name: api_key
```

## Step 2: Create the API key auth config

API key authentication relies on an **authentication configuration** \(auth config\) - a record stored in the Microsoft Enterprise token store that Microsoft 365 Copilot uses to send the API key when your plugin calls the API. Start with WIQD for a supported pro-code project. Toolkit and Microsoft Teams developer portal procedures remain available as alternatives. The declarative agent developer skill doesn't support API key authentication, because it builds MCP plugins.

### Use Work IQ Dev Tools \(recommended\)

For an existing API plugin manifest, use [`wiqd agent add auth`](https://microsoft.github.io/wiqd/cli/reference/#wiqd-agent-add-auth) with `--plugin-manifest`, `--auth-name`, and `--auth-type api-key`. Set `--api-key-in` to `header` or `query` and `--api-key-name` to the name from your OpenAPI security scheme. If the API accepts its key as a bearer token instead, select `--auth-type bearer-token`.

When adding an action from an OpenAPI document, [`wiqd agent add action`](https://microsoft.github.io/wiqd/cli/reference/#wiqd-agent-add-action) accepts `--api-key` for API-key or bearer credentials. The command documents environment placeholders when the value is omitted. Follow the selected command's credential handling and complete the project's provisioning workflow. These API-key options don't establish API key support for an agent's MCP plugin.

### Use Microsoft 365 Agents Toolkit

When you [create an API plugin from an existing OpenAPI document](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-api-plugins-existing-api) in [Microsoft 365 Agents Toolkit](https://aka.ms/M365AgentsToolkit), the toolkit registers the API key, creates the auth config, and updates your plugin manifest for you. You must define the `securitySchemes` property in your OpenAPI document.

### Use the Teams developer portal

Registering in the Teams developer portal is optional if you use Agents Toolkit. Use it to create the auth config manually, or to manage an auth config that Agents Toolkit already created.

1. Open [Teams developer portal](https://dev.teams.microsoft.com/tools). Select **Tools** -> **API key registration**.
2. If you have no existing registrations, select **Create an API key**. If you have existing registrations, select **New API key**.
3. Select **Add secret** and enter the API key.
4. Fill in the following fields.

   - **API key name**: A friendly name for your registration.
   - **Base URL**: Your API's base URL. This value should correspond to an entry in the [`servers` array](https://swagger.io/docs/specification/v3_0/api-host-and-base-path/) in your OpenAPI document.
   - **Target tenant**: Limit API access to your home tenant, or allow any tenant.
   - **Target Teams App**: Select **Any Teams app** if you don't know your final app ID. After you publish your app, bind this registration with your published app ID.

5. Select **Save**.
6. Completing the registration generates an **auth config ID** \(currently labeled **API key registration ID** in the Teams developer portal\).

#### Add the auth config ID to the plugin manifest

When you create the auth config manually in the Teams developer portal, set the `type` property of the [runtime authentication object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-manifest-2.4#runtime-authentication-object) to `ApiKeyPluginVault`, and set the `reference_id` to the **auth config ID**. Agents Toolkit does this for you.

```json
"auth": {
  "type": "ApiKeyPluginVault",
  "reference_id": "auth config ID"
},
```

## Related content

- [Configure authentication for MCP and API plugins in agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-authentication)
- [Configure OAuth 2.0 authentication](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-authentication-oauth)
- [Troubleshoot MCP and API plugin authentication](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-authentication-troubleshooting)
