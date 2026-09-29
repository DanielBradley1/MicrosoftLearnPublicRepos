<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/api-access -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Access the Microsoft Defender XDR APIs

Note

**Try our new APIs using MS Graph security API**. Find out more at: [Use the Microsoft Graph security API - Microsoft Graph \| Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview).

Important

Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Microsoft Defender exposes much of its data and actions through a set of programmatic APIs. These APIs help you automate workflows and make full use of Microsoft Defender's capabilities.

In general, you'll need to take the following steps to use the APIs:

- Create a Microsoft Entra application
- Get an access token using this application
- Use the token to access the Microsoft Defender API

Note

API access requires OAuth2.0 authentication. For more information, see [OAuth 2.0 Authorization Code Flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Once you've accomplished these steps, you're ready to access the Microsoft Defender API using a particular context.

## Application context \(Recommended\)

Use this context for apps that run without a signed-in user present, such as background services or daemons.

1. Create a Microsoft Entra web application.
2. Assign the desired permissions to the application.
3. Create a key for the application.
4. Get a security token using the application and its key.
5. Use the token to access the Microsoft Defender API.

For more information, see **[Create an app to access Microsoft Defender without a user](https://learn.microsoft.com/en-us/defender-xdr/api-create-app-web)**.

## User context

Use this context to perform actions on behalf of a single user.

1. Create a Microsoft Entra native application.
2. Assign the desired permission to the application.
3. Get a security token using the user credentials for the application.
4. Use the token to access the Microsoft Defender API.

For more information, see **[Create an app to access Microsoft Defender APIs on behalf of a user](https://learn.microsoft.com/en-us/defender-xdr/api-create-app-user-context)**.

## Partner context

Use this context when you need to provide an app to many users in [multiple tenants](https://learn.microsoft.com/en-us/azure/active-directory/develop/single-and-multi-tenant-apps).

1. Create a Microsoft Entra multi-tenant application.
2. Assign the desired permission to the application.
3. Get [admin consent](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-permissions-and-consent#requesting-consent-for-an-entire-tenant) for the app from each tenant.
4. Get a security token using user credentials based on a customer's tenant ID.
5. Use the token to access the Microsoft Defender API.

For more information, see **[Create an app with partner access to Microsoft Defender APIs](https://learn.microsoft.com/en-us/defender-xdr/api-partner-access)**.

## Related articles

- [Use the Microsoft Graph security API - Microsoft Graph \| Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview)
- [Microsoft Defender XDR APIs overview](https://learn.microsoft.com/en-us/defender-xdr/api-overview)
- [OAuth 2.0 authorization for user sign in and API access](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
- [Manage secrets in your server apps with Azure Key Vault](https://learn.microsoft.com/en-us/training/modules/manage-secrets-with-azure-key-vault/)
- [Create a 'Hello world' application that accesses the Microsoft 365 APIs](https://learn.microsoft.com/en-us/defender-xdr/api-hello-world)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
