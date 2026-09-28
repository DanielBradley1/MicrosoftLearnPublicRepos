<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/set-up-custom-federated-connectors -->
<!-- Sitemap-Last-Modified: 2026-08-17 -->

# Set up custom federated connectors

Important

**Work IQ Dev Tools \(preview\)** - Work IQ Dev Tools \(`wiqd`\) are experimental, prerelease tools for building, validating, provisioning, packaging, publishing, evaluating, and monitoring Microsoft 365 Copilot declarative agents from the terminal. They're not production-ready or officially supported, and breaking changes are expected. For more information, see the [Work IQ Dev Tools documentation](https://aka.ms/wiqd/docs).

Many organizations have proprietary systems, internal databases, and line-of-business applications that hold critical operational data. By using custom federated connectors, you can bring this data into Microsoft 365 Copilot by using Model Context Protocol \(MCP\), unlocking real-time access and natural language interaction for your organization's unique workflows. After you connect your data source, users can interact with the data in real time by using natural language - just as they do with Microsoft 365 data.

A custom federated connector starts with a Model Context Protocol \(MCP\) server that exposes read-only tools to safely surface your data. The MCP server acts as a bridge between Microsoft 365 Copilot and your internal systems. To keep access secure and user-scoped, custom federated connectors use industry-standard authentication.

## Prerequisites

Before you begin, make sure you have the following items:

- An **MCP server** URL with read-only tools exposed \(for example, `search`, `fetch`, or `query`\).
- **Admin permissions**

  - Global Administrator or AI Administrator role in the [Microsoft 365 admin center](https://admin.microsoft.com/).
  - An appropriate Microsoft Entra admin role for single sign-on \(SSO\) authentication.
  - Access to the [Teams Developer Portal](https://dev.teams.microsoft.com/).

- **Developer and legal information**

  - Developer name: The developer or company name.
  - Website URL: Link to documentation for the MCP server.
  - Privacy policy URL: Link to the MCP server privacy policy.
  - Terms of use URL: Link to the MCP server terms of use.

- **Authentication setup**

  - If your data source requires authentication, [set up authentication](#set-up-authentication) before you create the connector.

## Set up authentication

Custom federated connectors support three authentication methods. Choose the method that matches your data source.

| Method | Use case | Setup required |
| --- | --- | --- |
| **Microsoft Entra SSO** | Users authenticate with their Microsoft 365 credentials. | Microsoft Entra app registration and Teams Developer Portal registration. |
| **OAuth 2.0** | Users authenticate with a third-party identity provider. | OAuth app in the source system and Teams Developer Portal registration. |
| **No Auth** | Users don't need to authenticate. | None |

### Microsoft Entra SSO

Microsoft Entra SSO simplifies access management by letting users sign in to your MCP server with their existing Microsoft Entra credentials, so they don't need extra credentials. To use this option, your MCP server or API must use Microsoft Entra ID for access control.

To set up Microsoft Entra SSO:

1. [Update the Microsoft Entra app registration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api-plugin-authentication#update-the-microsoft-entra-app-registration).
2. [Add the new token audience to your API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api-plugin-authentication#add-the-new-token-audience-to-your-api).
3. [Register an SSO client in the Teams Developer Portal](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api-plugin-authentication#register-an-sso-client-in-teams-developer-portal).

When registration finishes, the Teams Developer Portal generates a **Microsoft Entra SSO registration ID**. Copy this ID - you need it when you configure the connector.

### OAuth 2.0

Use OAuth 2.0 when your data source authenticates with an external identity provider.

#### Register your app with the OAuth 2.0 provider

Before you begin, register your app with your OAuth 2.0 provider to get a client ID and secret. If your provider requires you to specify allowed redirect URIs during app registration, include the following URI:

```
https://teams.microsoft.com/api/platform/v1.0/oAuthRedirect
```

Copy the following credentials from your OAuth provider:

- **Client ID**
- **Client secret**

#### Register the OAuth app in the Teams Developer Portal

1. Sign in to the [Teams Developer Portal](https://dev.teams.microsoft.com/).
2. Select **Tools** > **OAuth Client Registration**.
3. Select **+ New OAuth connection**.
4. Enter the connection details:
   | Field | Value |
   | --- | --- |
   | **Name** | A descriptive name for your data source. |
   | **Client ID** | The client ID from your OAuth provider. |
   | **Client secret** | The client secret from your OAuth provider. |
   | **Authorization endpoint** | The URL your app uses to [request an authorization code](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow#request-an-authorization-code). |
   | **Token endpoint** | The URL your app uses to [redeem a code for an access token](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow#redeem-a-code-for-an-access-token). |
   | **Refresh endpoint** | The URL your app uses to [refresh the access token](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow#refresh-the-access-token). |
   | **Scopes** | The permission scopes that your API defines for access. |
5. \(Optional\) Enable **Proof Key for Code Exchange \(PKCE\)** if your OAuth provider supports it.
6. Select **Save**.

   [![Screenshot of the OAuth client registration form in the Teams Developer Portal, showing the App settings, Restrict usage, and OAuth settings sections.](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/federated-connectors/oauth-client-registration-form.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/federated-connectors/oauth-client-registration-form.png#lightbox)

After the registration is saved, the Teams Developer Portal displays the **OAuth client registration ID**. Copy this ID—you'll need it when you configure the connector.

[![Screenshot of the OAuth client registration confirmation page, with the registration ID highlighted.](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/federated-connectors/oauth-registration-id.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/federated-connectors/oauth-registration-id.png#lightbox)

## Create the connector

After you set up authentication, create the connector in the Microsoft 365 admin center.

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com/).
2. In the left pane, select **Copilot** > **Connectors**.
3. Select the **Gallery** tab.
4. Under **Created by your org**, find the **Create a new connector** tile and select **Add**.

   [![Screenshot of the Connectors page in the Microsoft 365 admin center, with the Gallery tab and the Create a new connector tile highlighted.](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/federated-connectors/admin-center-connectors-gallery.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/federated-connectors/admin-center-connectors-gallery.png#lightbox)
5. On the **Custom connector** page, under **Connect to MCP server**, select **Add**.

   [![Screenshot of the Custom connector page, with the Connect to MCP server option highlighted.](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/federated-connectors/connect-to-mcp-server.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/federated-connectors/connect-to-mcp-server.png#lightbox)
6. Enter the following information about your connector.
   | Field | Description | Example |
   | --- | --- | --- |
   | **Display name** | The user-facing name for your connector. | Company Intranet |
   | **Base URL** | Your MCP server endpoint. | `https://mcp.contoso.com` |
7. Enter the registration ID that matches the authentication method you set up previously:

   - For **Microsoft Entra SSO**, enter the **SSO registration ID** from the Teams Developer Portal.
   - For **OAuth 2.0**, enter the **OAuth registration ID** from the Teams Developer Portal.

8. Select **Save** to create the connector.

## Manage the connector

After you create a connector, it appears in the **Your Connections** list. From there, you can roll it out to users and manage its lifecycle.

### Stage the rollout

You can deploy the connector to selected users or groups before you release it to everyone in the tenant:

1. Select your connector.
2. Select **Staged rollout**.
3. Choose **Users** or **Groups**.
4. Add the test users or groups.
5. When you're ready to release the connector, select **Deploy to all users**.

### Enable, disable, or delete the connector

From the **Your Connections** list, you can take the following actions.

| Action | Result |
| --- | --- |
| **Enable** | Makes the connector available to its assigned audience. |
| **Disable** | Pauses the connector without removing its configuration. |
| **Delete** | Permanently removes the connector and its configuration. |

Note

Changes to a connector can take up to 15 minutes to take effect.

## Related content

- [Model Context Protocol \(MCP\) overview](https://modelcontextprotocol.io/)
- [Federated connectors overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/federated-connectors-overview)
- [Manage federated connectors](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/manage-federated-connectors)
- [Submit a federated connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/submit-federated-connector)
