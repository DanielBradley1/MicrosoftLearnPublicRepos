<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/github-server-pull-requests-deployment -->
<!-- Sitemap-Last-Modified: 2026-09-22 -->

# Deploy the GitHub Server Pull Requests connector

The GitHub Server Pull Requests Microsoft 365 Copilot connector integrates pull request metadata from GitHub Enterprise Server into Microsoft 365. After deployment, the connector indexes PR titles, descriptions, labels, timestamps, authors, reviewers, milestones, and repository context so users can search, summarize, and retrieve PR insights using Microsoft 365 Copilot, Copilot Search, and Microsoft Search.

This article describes the steps to deploy and customize the GitHub Server Pull Requests connector.

For advanced GitHub service configuration information, see [Set up the GitHub service for GitHub Server Pull Requests connector ingestion](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/github-server-pull-requests-admin-setup).

## Prerequisites

Before you deploy the GitHub Server Pull Requests connector, make sure that the GitHub Enterprise Server environment is configured for ingestion. The following table summarizes the steps to configure the GitHub service environment and deploy the connector.

| Task | Role |
| --- | --- |
| [Configure the environment](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/github-server-pull-requests-admin-setup) | GitHub admin |
| [Deploy the connector in the Microsoft 365 admin center](#deploy-the-connector) | Microsoft 365 admin |
| [Customize connector settings](#customize-settings-optional) \(optional\) | Microsoft 365 admin |

Before you deploy the connector, make sure that you meet the following prerequisites:

- You're a Microsoft 365 admin.
- Your GitHub Enterprise Server instance must be accessible via API.
- The GitHub app must be fully configured and installed in the target organization.
- The Microsoft Graph Connector Agent must be installed on a device with access to your GitHub instance \(version 3.1.11.0 or later\).
- The user account used for authentication must have access to the repositories and pull requests to be indexed.
- Users accessing indexed PR data must have Microsoft Entra ID identities to enable permission mapping.

## Deploy the connector

To add the GitHub Server Pull Requests connector for your organization:

1. In the Microsoft 365 admin center, in the left pane, choose **Copilot** > **Connectors**.
2. Choose the **Gallery** tab.
3. From the list of available connectors, choose **GitHub Server Pull Requests**.

### Set display name

The display name is used to identify references in Copilot responses so users can recognize content sources. You can keep the default name **GitHub Server Pull Requests**, or replace it with a custom display name that's relevant to your organization.

For more information, see [Enhance Copilot discovery of connector content](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/enhance-copilot-discovery).

### Set instance URL

Enter the instance URL of your GitHub Enterprise Server. For example:

`https://github.<yourdomain>.com`

The connector uses this URL to request PR metadata during ingestion.

### Choose authentication type

The GitHub Server Pull Requests connector supports the following authentication types:

- **GitHub app \(on behalf of user\):**

  - Enter the **App ID** and **Client secret** of your GitHub App.
  - Authorize access.
  - Recommended when using separate user accounts for rate‑limit isolation.

- **GitHub app \(installation\):**

  - Generate a private key from the GitHub app configuration page.
  - Enter the **App ID**, organization name, and upload the private key.


  Note


  This authentication type is currently in preview. To use this authentication type, contact Microsoft support.

### Roll out

To roll out the connector to a limited audience, select the toggle next to **Rollout to limited audience** and specify the users and groups who get early access. For more information, see  
[Staged rollout for Copilot connectors](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/staged-rollout).

Choose **Create** to deploy the connection. The connector begins indexing content immediately.

The following table lists the default values that are set.

| Category | Default value |
| --- | --- |
| Users | Identity mapping available through Email, Login, Name options |
| Content | Full PR metadata; default time‑range filter: 365 days |
| Sync | Incremental crawl every 15 minutes; full crawl daily |

To customize these values, choose **Custom setup**. For more information, see [Customize settings](#customize-settings-optional).

After you create your connection, you can review the status in the **Connectors** section of the [Microsoft 365 admin center](https://admin.microsoft.com/).

## Customize settings \(optional\)

You can customize the default values for the GitHub Server Pull Requests connector settings. To customize settings, on the connector page in the admin center, choose **Custom setup**.

### Customize user settings

#### Access permissions

Access to PR data respects the GitHub app permissions and GitHub repository access controls.

#### Mapping identities

To ensure that permissions are applied correctly, map GitHub user identities to Microsoft Entra ID. Choose one of the following options for mapping:

- **Email:** Maps GitHub email to Microsoft Entra ID user properties.
- **Login:** Maps GitHub logins with Microsoft Entra ID user properties.
- **Name:** Maps GitHub name with Microsoft Entra ID user properties.

If direct mapping fails, use regular expressions \(regex\) to transform the data. For example: `[a-zA-Z0-9]+`. For more information, see [Map Microsoft Entra identities](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/map-entra-id).

### Customize content settings

#### Query string

Specify or refine the query parameters used to filter or identify pull request content.

#### Manage properties

The following table describes the properties the connector indexes by default.

| Property | Semantic label | Description | Schema attributes |
| --- | --- | --- | --- |
| Title | Title | Pull request title | Text |
| Description | Body | PR description | Text |
| Labels | Tags | Pull request labels | Collection |
| State | Status | Open/closed state | Enum |
| Author | Author | PR creator | User |
| Reviewers | Reviewers | Assigned reviewers | Collection |
| Assignees | Owners | Assigned contributors | Collection |
| Milestones | Milestone | Target milestone | Text |
| Timestamps | Timestamps | Created/updated times | DateTime |

### Customize sync intervals

Two crawl types are available:

- **Incremental crawl:** Runs every 15 minutes by default.
- **Full crawl:** Runs daily to refresh the PR index.

You can customize these values according to the needs of your organization. For more information, see [Guidelines for crawl settings](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/deployment-overview#guidelines-for-crawl-settings).

## Related content

- [GitHub Server Pull Requests connector overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/github-server-pull-requests-overview)
- [Troubleshoot issues with the GitHub Server Pull Requests connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/github-server-pull-requests-troubleshooting)
- [Set up Copilot connectors in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/deployment-overview)
