<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/pagerduty-schedules-admin-setup -->
<!-- Sitemap-Last-Modified: 2026-05-29 -->

# Set up the PagerDuty service for PagerDuty Schedules connector ingestion

The PagerDuty Schedules Microsoft 365 Copilot connector integrates PagerDuty schedule data into Microsoft 365, enabling Copilot and Microsoft Search to surface schedule information directly within apps like Teams, Outlook, and SharePoint.

This article provides information about the configuration steps that PagerDuty admins need to complete in order for your organization to deploy the [PagerDuty Schedules connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/pagerduty-schedules-overview).

For information about how to deploy the connector, see [Deploy the PagerDuty Schedules connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/pagerduty-schedules-deployment).

## Setup checklist

The following checklist lists the steps involved in configuring the PagerDuty environment and setting up the connector prerequisites.

### Configure the PagerDuty environment

| Task | Role |
| --- | --- |
| [Identify the PagerDuty service region](#identify-the-pagerduty-service-region) | PagerDuty admin |
| [Enable Developer Mode in PagerDuty](#enable-developer-mode-in-pagerduty) | PagerDuty admin |

### Set up OAuth prerequisites

| Task | Role |
| --- | --- |
| [Register an OAuth 2.0 app in PagerDuty](#register-an-oauth-20-app-in-pagerduty) | PagerDuty admin |
| [Configure redirect URLs](#configure-redirect-urls) | PagerDuty admin |
| [Configure OAuth scopes](#configure-oauth-scopes) | PagerDuty admin |
| [Obtain Client ID and Client Secret](#obtain-client-id-and-client-secret) | PagerDuty admin |

## Configure the PagerDuty environment

The following sections describe the admin tasks to configure the PagerDuty environment to enable and optimize the connection.

### Identify the PagerDuty service region

PagerDuty allows customers to choose the geographic service region of the PagerDuty data centers that host their account. The REST API URL varies depending on your service region:

- **US service region**: `https://api.pagerduty.com`
- **EU service region**: `https://api.eu.pagerduty.com`

To identify your PagerDuty service region:

1. Sign in to your PagerDuty account.
2. Review the URL in your browser address bar:

   - For the US region, your URL typically appears as `https://[your-subdomain].pagerduty.com`
   - For the EU region, your URL typically appears as `https://[your-subdomain].eu.pagerduty.com`

Make note of your REST API URL as you'll need it when deploying the connector in the Microsoft 365 admin center.

For more information, see [Service regions](https://support.pagerduty.com/main/docs/service-regions) in the PagerDuty documentation.

### Enable Developer Mode in PagerDuty

To register OAuth apps in PagerDuty, you must first enable Developer Mode.

To enable Developer Mode:

1. Sign in to your PagerDuty account with administrator permissions.
2. Navigate to **Integrations** > **Developer Mode**.
3. If Developer Mode is not already enabled, choose **Enable Developer Mode**.

Note

You must be a PagerDuty account administrator to enable Developer Mode. If you don't see this option, contact your PagerDuty account owner.

## Set up OAuth prerequisites

The following sections describe the prerequisite steps to complete before you deploy the PagerDuty Schedules connector.

### Register an OAuth 2.0 app in PagerDuty

The PagerDuty Schedules connector uses OAuth 2.0 for authentication. You must register an OAuth app in PagerDuty to obtain the client credentials required for connector authentication.

To register an OAuth 2.0 app:

1. Sign in to your PagerDuty account with administrator permissions.
2. Go to **Integrations** > **Developer Mode**.
3. Select **Create New App**.
4. In the app registration form, enter the following information:

   - **App Name**: Enter a descriptive name such as "Microsoft 365 Copilot Connector"
   - **Description**: Enter a description such as "OAuth app for Microsoft 365 Copilot connector integration"
   - **Category**: Select **Integration**

5. Select **Scoped OAuth** as the OAuth type.

   Important

   You must select **Scoped OAuth** to ensure proper authentication. Standard OAuth is not supported by the connector.
6. Continue to configure the redirect URLs and OAuth scopes as described in the following sections.

For more information about OAuth functionality in PagerDuty, see [OAuth Functionality](https://developer.pagerduty.com/docs/oauth-functionality) and [Register an App](https://developer.pagerduty.com/docs/register-an-app) in the PagerDuty developer documentation.

### Configure redirect URLs

OAuth 2.0 authentication requires redirect URLs \(also called callback URLs\) to complete the authorization flow. The redirect URL varies based on your Microsoft 365 environment.

In your PagerDuty OAuth app settings, add the appropriate redirect URL for your environment:

- **For Microsoft 365 Enterprise**: `https://gcs.office.com/v1.0/admin/oauth/callback`
- **For Microsoft 365 Government**: `https://gcsgcc.office.com/v1.0/admin/oauth/callback`

Important

Make sure that you use the correct redirect URL for your environment. Using an incorrect redirect URL prevents the OAuth authorization flow from completing successfully.

### Configure OAuth scopes

The PagerDuty Schedules connector requires specific OAuth scopes to access schedule data and enforce permissions. In your OAuth app settings in PagerDuty, select the following scopes:

| Scope | Access level | Description |
| --- | --- | --- |
| Audit records | Read Access | Required to access audit log information for schedules. |
| Schedules | Read Access | Required to read schedule data including on-call rotations and coverage information. |
| Teams | Read Access | Required when Advanced Permissions is enabled to enforce team-based access controls. |
| Users | Read Access | Required to map PagerDuty users to Microsoft 365 identities for permission enforcement. |

Note

The connector requires read-only access. It doesn't require write or delete permissions.

To configure OAuth scopes:

1. In your PagerDuty OAuth app settings, scroll to the **OAuth Scopes** section.
2. Select the checkbox next to each required scope:

   - **Audit records** – Read Access
   - **Schedules** – Read Access
   - **Teams** – Read Access
   - **Users** – Read Access

3. Review the selected scopes to ensure all required permissions are enabled.

### Obtain Client ID and Client Secret

After configuring your OAuth app, you need to obtain the Client ID and Client Secret that you'll use to authenticate the connector during deployment.

To obtain your Client ID and Client Secret:

1. In your PagerDuty OAuth app settings, choose **Save** to save your app configuration.
2. After saving, the **Client ID** appears in the app details section. Copy this value.
3. Choose **Generate Client Secret** or **Show Client Secret** \(depending on whether a secret already exists\).
4. Copy the **Client Secret** value.

Important

Store the Client ID and Client Secret securely. You'll need these credentials when deploying the connector in the Microsoft 365 admin center. The Client Secret is shown only once. If you lose it, you'll need to generate a new secret.

## Next step

[Deploy the PagerDuty Schedules connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/pagerduty-schedules-deployment)
