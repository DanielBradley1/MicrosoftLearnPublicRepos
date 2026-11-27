<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/siem-defender-configure-integration-profiles -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Configure integration profiles for generated playbooks

Integration profiles define the API connection details used by generated playbooks. Configure integration profiles before you create or run generated playbooks that call Microsoft or third-party services.

Each integration profile includes connection details such as the base API URL, authentication method, and required credentials.

## Prerequisites

Before you begin, make sure that:

- You have access to the [Microsoft Defender portal](https://security.microsoft.com/).
- You have the **Automation Integration** Unified RBAC permission with **Read** and **Write** access.
- You have the credentials required for the target API.
- To run automation on third-party data ingested through Log Analytics, you have a [Microsoft Sentinel workspace](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-onboard).

## Create an integration profile

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
2. Go to **Microsoft Sentinel** > **Configuration** > **Automation**.
3. Select the **Integration Profiles** tab.
4. Select **Create**.
5. Enter an integration name.
6. Enter a description.
7. Enter the base API URL for the service.
8. Select the authentication method.

   Supported authentication methods include:

   - OAuth2 Client Credentials
   - API Key
   - AWS Auth
   - User and Password
   - Bearer/JWT Authentication
   - Hawk

9. Enter the required authentication details.
10. Review the integration profile settings.
11. Select **Create**.

## Create a Microsoft Graph integration profile

Use a Microsoft Graph integration profile when a generated playbook needs to call Microsoft Graph APIs.

1. In the Azure portal, go to **Microsoft Entra ID** > **App registrations**.
2. Select **New registration**.
3. Enter a name for the application.
4. Complete the app registration.
5. Copy the **Application \(client\) ID** and **Directory \(tenant\) ID**.
6. Go to **Certificates & secrets**.
7. Select **New client secret**.
8. Copy the client secret value and store it securely.

   Important

   You can't retrieve the client secret value after leaving the page.
9. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
10. Go to **Microsoft Sentinel** > **Configuration** > **Automation**.
11. Select the **Integration Profiles** tab.
12. Select **Create**.
13. Configure the profile with the following values:
    | Field | Value |
    | --- | --- |
    | Integration name | Enter a descriptive name, such as `Graph Integration`. |
    | Description | Enter a short description. |
    | Base API URL | `https://graph.microsoft.com` |
    | Authentication method | OAuth2 |
    | Client ID | Enter the Application client ID. |
    | Client secret | Enter the client secret value. |
    | Token endpoint | `https://login.microsoftonline.com/{TENANT_ID}/oauth2/v2.0/token` |
    | Scopes | `https://graph.microsoft.com/.default` |
14. Replace `{TENANT_ID}` with the Directory tenant ID.
15. Select **Create**.

## Edit an integration profile

You can edit the integration name and description after the profile is created.

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
2. Go to **Microsoft Sentinel** > **Configuration** > **Automation**.
3. Select the **Integration Profiles** tab.
4. Select the integration profile.
5. Update the name or description.
6. Save your changes.

Note

The API URL and authentication method can't be changed after an integration profile is created. To change the API URL or authentication method, create a new integration profile.

## Limitations

Integration profiles have the following limitations:

- Microsoft Graph and Azure Resource Manager integrations aren't enabled by default and must be manually created.
- The API URL and authentication method can't be changed after an integration profile is created.
- The maximum number of integrations per tenant is 500.

## Related content

- [Automation in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-automation)
- [Generate playbooks using AI](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-generate-playbooks)
- [Create automation rules](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-create-automation-rules)
