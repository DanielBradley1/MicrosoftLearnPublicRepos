<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/aha-admin-setup -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Set up the Aha! service for connector ingestion

The Aha! Features and Ideas Microsoft 365 Copilot connectors empower your organization to index and search Aha! features and ideas across your enterprise. This article provides information about the configuration steps that Aha! admins need to complete in order for your organization to deploy the [Aha! connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/aha-overview).

For information about how to deploy the connector, see [Deploy the Aha! connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/aha-deployment).

## Identify the Aha! instance URL

- Sign in to Aha! Cloud and go to your account: `https://<company>.aha.io`.
- Use the base URL \(for example, `https://contoso.aha.io`\) and avoid workspace- or record-specific URLs.
- Verify that the URL resolves to your Aha! home page.

## Enable API access

- Confirm that no network restrictions or API access limitations block the connector.
- If your organization enforces network-level restrictions, add Microsoft 365 Copilot connector IP addresses.
- Go to **Account** > **Security and single sign-on** > **IP address–based access control** and add Microsoft IPs to the allow list. For the list of IP addresses, see [Set up Microsoft 365 Copilot connectors in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/deployment-overview).

## Create OAuth application

To use Aha! OAuth for authentication:

1. In Aha!, go to **Settings** > **Personal** > **Developer** > **OAuth applications**.
2. Choose **Register OAuth application** and provide the name and redirect URI:

   - For Microsoft 365 Enterprise: `https://gcs.office.com/v1.0/admin/oauth/callback`
   - For Microsoft 365 Government: `https://gcsgcc.office.com/v1.0/admin/oauth/callback`

3. Record the **Client ID** and **Client secret** for use in connector setup.

## Next step

[Deploy the Aha! connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/aha-deployment)
