<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/dropbox-admin-setup -->
<!-- Sitemap-Last-Modified: 2026-04-03 -->

# Set up the Dropbox service for Dropbox connector ingestion

The Dropbox connector for Microsoft 365 Copilot enables your organization to index Dropbox content - including team folders, shared folders, private folders, and Dropbox Paper documents - and surface the content in Microsoft 365 Copilot and Microsoft Search experiences. This article provides information about the configuration steps that Dropbox admins need to complete to deploy the [Dropbox connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/dropbox-overview).

For information about how to deploy the connector, see [Deploy the Dropbox connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/dropbox-deployment).

## Setup checklist

The following checklist lists the steps involved in configuring the environment and setting up the connector prerequisites.

| Task | Role |
| --- | --- |
| [Set up a team admin user](#set-up-a-team-admin-user) | Dropbox admin |
| [Configure a Dropbox app](#configure-a-dropbox-app) | Dropbox admin |
| [Add redirect URIs](#add-redirect-uris) | Dropbox admin |
| [Add API scopes](#add-api-scopes) | Dropbox admin |
| [Get app key and app secret](#get-app-key-and-app-secret) | Dropbox admin |

## Set up a team admin user

Create a Dropbox Business account and assign a team admin user. This account is used to authorize the connector.

## Configure a Dropbox app

To configure a Dropbox app:

- Go to the [Dropbox developer portal](https://www.dropbox.com/developers/apps/) and select **Create app**.

  [![Screenshot of the Create app button in the Dropbox developer portal.](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/dropbox/dropbpx-create-app.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/dropbox/dropbpx-create-app.png#lightbox)
- Configure the app with:

  - A unique app name
  - Scoped access
  - Full Dropbox access permissions

[![Screenshot of the app configuration fields.](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/dropbox/dropbox-prerequisites-2.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/dropbox/dropbox-prerequisites-2.png#lightbox)

For more information, see [Getting started with Dropbox](https://www.dropbox.com/developers/reference/getting-started).

## Add redirect URIs

In the **OAuth 2.0** section of the Dropbox App Console, add the following URLs:

- For Microsoft 365 Enterprise: `https://gcs.office.com/v1.0/admin/oauth/callback`
- For Microsoft 365 Government: `https://gcsgcc.office.com/v1.0/admin/oauth/callback`

[![Screenshot of the Redirect URIs field.](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/dropbox/dropbox-add-directurl.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/dropbox/dropbox-add-directurl.png#lightbox)

## Add API scopes

Go to the **Permissions** tab and add the following API scopes:

**Individual scopes**

- files.metadata.read
- files.content.read
- sharing.read
- file\_requests.read

**Team scopes**

- team\_info.read
- team\_data.member
- team\_data.governance.write
- team\_data.governance.read
- team\_data.content.read
- files.team\_metadata.read
- members.read
- groups.read
- events.read

[![Screenshot of the permissions tab.](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/dropbox/dropbox-api-scopes.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/media/dropbox/dropbox-api-scopes.png#lightbox)

## Get app key and app secret

From the **Settings** tab in the Dropbox App Console, copy the app key and app secret. These credentials are required for connector authentication.

## Next step

[Deploy the Dropbox connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/dropbox-deployment)
