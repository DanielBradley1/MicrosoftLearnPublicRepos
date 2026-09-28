<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/bamboohr-admin-setup -->
<!-- Sitemap-Last-Modified: 2026-08-17 -->

# Set up the BambooHR service for connector ingestion

The BambooHR Microsoft 365 Copilot connector indexes employee profiles from BambooHR into Microsoft Graph, making them accessible across Microsoft 365 experiences including Microsoft 365 Copilot and Microsoft Search. This article provides information about the configuration steps that BambooHR admins need to complete in order for your organization to deploy the [BambooHR connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/bamboohr-overview).

For information about how to deploy the connector, see [Deploy the BambooHR connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/bamboohr-deployment).

## Setup checklist

The following checklist lists the steps involved in configuring the BambooHR environment and setting up the connector prerequisites.

| Task | Role |
| --- | --- |
| [Create a BambooHR developer account](#create-a-bamboohr-developer-account) | BambooHR admin |
| [Register a BambooHR application](#register-a-bamboohr-application) | BambooHR admin |
| [Configure redirect URLs](#configure-redirect-urls) | BambooHR admin |
| [Select application scopes](#select-application-scopes) | BambooHR admin |
| [Obtain client credentials](#obtain-client-credentials) | BambooHR admin |

## Create a BambooHR developer account

1. Go to the [BambooHR developer portal](https://developers.bamboohr.com/).
2. Sign in with your existing BambooHR developer account credentials, or create a new developer account.

Note

The developer portal is separate from your main BambooHR instance and is used specifically for creating and managing API applications that integrate with BambooHR.

## Register a BambooHR application

1. In the developer portal, create a new BambooHR app.
2. Enter a unique application name, such as "Microsoft 365 Copilot connector" or your organization's name.

[![Screenshot of Add application.](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/bamboohr-connector/bamboohr-add-application.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/bamboohr-connector/bamboohr-add-application.png#lightbox)

## Configure redirect URLs

1. In the app details section, add the redirect URL that Microsoft 365 uses to communicate with BambooHR during authentication.
2. Copy and paste the following URL: `https://gcs.office.com/v1.0/admin/oauth/callback`

[![Screenshot of App Details.](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/bamboohr-connector/bamboohr-application-details.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/bamboohr-connector/bamboohr-application-details.png#lightbox)

[![Screenshot of Redirect URLs form.](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/bamboohr-connector/bamboohr-redirect-uri.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/bamboohr-connector/bamboohr-redirect-uri.png#lightbox)

## Select application scopes

In the application scopes section, select the required permissions with read-only access to ensure the connector can retrieve the necessary profile information:

| Category | Required scopes |
| --- | --- |
| Claims | email, openid |
| Employee | employee, employee:contact, employee:identification, employee:job, employee:management, employee:name, employee\_directory, sensitive\_employee:protected\_info |
| Miscellaneous | field, offline\_access, public.user |
| Reports | report |

[![Screenshot of Select Scopes.](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/bamboohr-connector/bamboohr-select-scopes.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/bamboohr-connector/bamboohr-select-scopes.png#lightbox)

[![Screenshot of Scope Selection.](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/bamboohr-connector/bamboohr-scope-selection.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/bamboohr-connector/bamboohr-scope-selection.png#lightbox)

## Obtain client credentials

1. Go to the **App credentials** section.
2. Record the **App client ID** and **App client secret**. Use these credentials to authenticate the Microsoft 365 connector with your BambooHR application during setup.

[![Screenshot of Client ID and Client Secret section.](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/bamboohr-connector/bamboohr-client-id-and-secret.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/bamboohr-connector/bamboohr-client-id-and-secret.png#lightbox)

## Next step

[Deploy the BambooHR connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/bamboohr-deployment)
