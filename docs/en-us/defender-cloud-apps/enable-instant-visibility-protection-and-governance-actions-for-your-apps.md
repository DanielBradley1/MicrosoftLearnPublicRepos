<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/enable-instant-visibility-protection-and-governance-actions-for-your-apps -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# Connect apps to get visibility and control with Microsoft Defender for Cloud Apps

App connectors use the APIs of app providers to enable greater visibility and control by Microsoft Defender for Cloud Apps over the apps you connect to. This article describes the supported app connectors, how they scan and collect data, how to enable or disable connectors, and the prerequisites for connecting apps.

Microsoft Defender for Cloud Apps uses the APIs provided by the cloud provider. All communication between Defender for Cloud Apps and connected apps is encrypted using HTTPS. Each connected cloud service has its own framework and API limitations such as throttling, API limits, dynamic time-shifting API windows, and others. Microsoft Defender for Cloud Apps works with connected cloud services to optimize the usage of the APIs and to provide the best performance. Taking into account different limitations that connected cloud services impose on the APIs, the Microsoft Defender for Cloud Apps engines use the allowed capacity. Some operations, such as scanning all files in the tenant, require numerous APIs so they're spread over a longer period. Expect some policies to run for several hours or several days.

Important

Starting **September 1, 2024**, Microsoft deprecated the **Files** page from Microsoft Defender for Cloud Apps. For more information, see [File policies in Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/data-protection-policies).

## Multi-instance support

Defender for Cloud Apps supports multiple instances of the same connected app. For example, if you have more than one instance of Salesforce \(one for sales, one for marketing\) you can connect both to Defender for Cloud Apps. You can manage the different instances from the same console to create granular policies and deeper investigation. Multi-instance support applies only to API connected apps, not to Cloud Discovered apps, or Proxy connected apps.

Note

Multi-instance isn't supported for Microsoft 365 and Azure.

## How app connectors scan and collect data

Defender for Cloud Apps is deployed with system admin privileges to allow full access to all objects in your environment.

The App Connector flow is as follows:

1. Defender for Cloud Apps scans and saves authentication permissions.
2. Defender for Cloud Apps requests the user list. The first time Defender for Cloud Apps makes the request, the scan might take some time to complete. After the user scan finishes, Defender for Cloud Apps moves on to activities and files. As soon as the scan starts, some activities are available in Defender for Cloud Apps.
3. After completion of the user request, Defender for Cloud Apps periodically scans users, groups, activities, and files. All activities are available after the first full scan.

The initial app connector setup and first scan might take some time depending on the size of the tenant, the number of users, and the size and number of files that need to be scanned.

Depending on the app to which you're connecting, API connection enables the following items:

- **Account information** - Visibility into users, accounts, profile information, status \(suspended, active, disabled\) groups, and privileges.
- **Audit trail** - Visibility into user activities, admin activities, sign-in activities.
- **Account governance** - Ability to suspend users, revoke passwords, and more.
- **App permissions** - Visibility into issued tokens and their permissions.
- **App permission governance** - Ability to remove tokens.
- **Data scan** - Scanning of unstructured data using two processes -periodically \(every 12 hours\) and in real-time scan \(triggered each time a change is detected\).
- **Data governance** - Ability to quarantine files, including files in trash, and overwrite files.

The tables in this section list, for each cloud app, the abilities supported with App connectors:

Note

Since not all app connectors support all abilities, some rows might be empty.

### User and activity visibility per connected app

This section lists the user and activity visibility capabilities that each app connector supports.

| App | List accounts | List groups | List privileges | Log on activity | User activity | Administrative activity |
| --- | --- | --- | --- | --- | --- | --- |
| [Asana](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-asana) | ✔ |  |  | ✔ | ✔ |  |
| [Atlassian](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-atlassian) | ✔ |  |  | ✔ | ✔ | ✔ |
| [AWS](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-aws) | ✔ |  |  | ✔ | Not applicable | ✔ |
| [Azure](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-azure) | ✔ | ✔ |  | ✔ | ✔ |  |
| [Box](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-box) | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| [Citrix ShareFile](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-citrix-sharefile) |  |  |  |  |  |  |
| [DocuSign](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-docusign) | Supported with DocuSign Monitor |  |  | Supported with DocuSign Monitor | Supported with DocuSign Monitor | Supported with DocuSign Monitor |
| [Dropbox](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-dropbox) | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| [Egnyte](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-egnyte) | ✔ |  | ✔ | ✔ | ✔ | ✔ |
| [GitHub](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-github) | ✔ |  | ✔ |  | ✔ | ✔ |
| [GCP](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-gcp) | Subject Google Workspace connection | Subject Google Workspace connection | Subject Google Workspace connection | Subject Google Workspace connection | ✔ | ✔ |
| [Google Workspace](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-google-workspace) | ✔ | ✔ | ✔ | ✔ | ✔ - requires Google Business or Enterprise | ✔ |
| [Microsoft 365](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-office-365) | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| [Miro](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-miro) | ✔ |  |  | ✔ | ✔ |  |
| [Mural](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-mural) | ✔ |  |  | ✔ | ✔ |  |
| [NetDocuments](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-netdocuments) | ✔ |  | ✔ |  | ✔ | ✔ |
| [Okta](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-okta) | ✔ |  | Not supported by provider | ✔ | ✔ | ✔ |
| [OneLogin](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-onelogin) | ✔ |  | ✔ | ✔ | ✔ | ✔ |
| [ServiceNow](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-servicenow) | ✔ | ✔ | ✔ | ✔ | Partial | Partial |
| [Salesforce](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-salesforce) | Supported with Salesforce Shield | Supported with Salesforce Shield | Supported with Salesforce Shield | Supported with Salesforce Shield | Supported with Salesforce Shield | Supported with Salesforce Shield |
| [Slack](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-slack) | ✔ |  | ✔ | ✔ | ✔ | ✔ |
| [Smartsheet](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-smartsheet) | ✔ |  | ✔ |  | ✔ | ✔ |
| [Webex](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-webex) | ✔ |  | ✔ |  | ✔ | Not supported by provider |
| [Workday](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-workday) | ✔ | Not supported by provider | Not supported by provider | ✔ | ✔ | Not supported by provider |
| [Workplace by Meta](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-workplace) | ✔ |  | ✔ | ✔ | ✔ | ✔ |
| [Zendesk](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-zendesk) | ✔ |  | ✔ | ✔ | ✔ | ✔ |
| [Zoom](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-zoom) |  |  |  |  |  |  |

### User, app governance, and security configuration visibility

This section lists the governance and security configuration visibility features available for each connected app.

| App | User governance | View app permissions | Revoke app permissions | SaaS Security Posture Management \(SSPM\) |
| --- | --- | --- | --- | --- |
| [Asana](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-asana) |  |  |  |  |
| [Atlassian](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-atlassian) |  |  |  | ✔ |
| [AWS](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-aws) |  | Not applicable | Not applicable |  |
| [Azure](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-azure) |  |  | Not supported by provider |  |
| [Box](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-box) | ✔ | Not supported by provider |  |  |
| [Citrix ShareFile](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-citrix-sharefile) |  |  |  | ✔ |
| [DocuSign](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-docusign) |  |  |  | ✔ |
| [Dropbox](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-dropbox) |  |  |  | ✔ |
| [Egnyte](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-egnyte) |  |  |  |  |
| [GitHub](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-github) |  | ✔ |  | ✔ |
| [GCP](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-gcp) | Subject Google Workspace connection | Not applicable | Not applicable |  |
| [Google Workspace](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-google-workspace) | ✔ | ✔ | ✔ | ✔ |
| [Microsoft 365](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-office-365) | ✔ | ✔ | ✔ | ✔ |
| [Miro](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-miro) |  |  |  |  |
| [Mural](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-mural) |  |  |  |  |
| [NetDocuments](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-netdocuments) |  |  |  | Preview |
| [Okta](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-okta) |  | Not applicable | Not applicable | ✔ |
| [OneLogin](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-onelogin) |  |  |  |  |
| [ServiceNow](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-servicenow) |  |  |  | ✔ |
| [Salesforce](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-salesforce) | ✔ |  | ✔ | ✔ |
| [Slack](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-slack) |  |  |  |  |
| [Smartsheet](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-smartsheet) |  |  |  |  |
| [Webex](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-webex) |  | Not applicable | Not applicable |  |
| [Workday](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-workday) | Not supported by provider | Not applicable | Not applicable |  |
| [Workplace by Meta](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-workplace) |  |  |  | Preview |
| [Zendesk](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-zendesk) |  |  |  | ✔ |
| [Zoom](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-zoom) |  |  |  | Preview |

### Information protection capabilities per connected app

This section summarizes the information protection features supported by each app connector.

| App | DLP - Periodic backlog scan | DLP - Near real-time scan | Sharing control | File governance | Apply sensitivity labels from Microsoft Purview Information Protection |
| --- | --- | --- | --- | --- | --- |
| [Asana](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-asana) |  |  |  |  |  |
| [Atlassian](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-atlassian) |  |  |  |  |  |
| [AWS](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-aws) |  | ✔ - S3 Bucket discovery only | ✔ | ✔ | Not applicable |
| [Azure](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-azure) |  |  |  |  |  |
| [Box](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-box) | ✔ | ✔ | ✔ | ✔ | ✔ |
| [Citrix ShareFile](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-citrix-sharefile) |  |  |  |  |  |
| [DocuSign](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-docusign) |  |  |  |  |  |
| [Dropbox](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-dropbox) | ✔ | ✔ | ✔ | ✔ |  |
| [Egnyte](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-egnyte) |  |  |  |  |  |
| [GitHub](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-github) |  |  |  |  |  |
| [GCP](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-gcp) | Not applicable | Not applicable | Not applicable | Not applicable | Not applicable |
| [Google Workspace](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-google-workspace) | ✔ | ✔ - requires Google Business Enterprise | ✔ | ✔ | ✔ |
| [Okta](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-okta) | Not applicable | Not applicable | Not applicable | Not applicable | Not applicable |
| [Miro](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-miro) |  |  |  |  |  |
| [Mural](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-mural) |  |  |  |  |  |
| [NetDocuments](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-netdocuments) |  |  |  |  |  |
| [Okta](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-okta) | Not applicable | Not applicable | Not applicable | Not applicable | Not applicable |
| [OneLogin](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-onelogin) |  |  |  |  |  |
| [ServiceNow](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-servicenow) | ✔ | ✔ | Not applicable |  |  |
| [Salesforce](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-salesforce) | ✔ | ✔ |  | ✔ |  |
| [Slack](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-slack) |  |  |  |  |  |
| [Smartsheet](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-smartsheet) |  |  |  |  |  |
| [Webex](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-webex) | ✔ | ✔ | ✔ | ✔ | Not applicable |
| [Workday](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-workday) | Not supported by provider | Not supported by provider | Not supported by provider | Not supported by provider | Not applicable |
| [Workplace by Meta](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-workplace) |  |  |  |  |  |
| [Zendesk](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-zendesk) |  |  |  |  | Preview |
| [Zoom](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-zoom) |  |  |  |  |  |

## Prerequisites

Review these requirements before you enable app connectors.

- When working with the [Microsoft 365 connector](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-office-365), you'll need a license for each service where you want to view security recommendations. For example, to view recommendations for Microsoft Forms, you'll need a license that supports Forms.
- For some apps, you might need to allow list IP addresses to enable Defender for Cloud Apps to collect logs and provide access for the Defender for Cloud Apps console. For more information, see [Network requirements](https://learn.microsoft.com/en-us/defender-cloud-apps/network-requirements).

Note

To get updates when URLs and IP addresses change, subscribe to the RSS as explained in: [Microsoft 365 URLs and IP address ranges](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges).

## Enable app connectors

To enable an app connector for the first time, configure an API connection for the specific cloud app you want to connect. For detailed instructions, see the [app connector guides](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-connected-apps) for each app.

### Enable an app connector

To enable an app connector, perform these steps:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
2. Go to **Cloud Apps** > **Connected apps**.
3. Select **Connect an app** or **Add a new connector**.
4. Choose the cloud app you want to connect.
5. Follow the instructions in the corresponding app-specific API connector guide. These instructions include the required permissions and authentication steps.

Each cloud app has its own enablement process based on the APIs it supports.

### ExpressRoute integration with Defender for Cloud Apps

Defender for Cloud Apps is deployed in Azure and fully integrated with [ExpressRoute](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-introduction). All interactions with the Defender for Cloud Apps apps and traffic sent to Defender for Cloud Apps, including upload of discovery logs, is routed via ExpressRoute for improved latency, performance, and security. For more information about Microsoft Peering, see [ExpressRoute circuits and routing domains](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-circuit-peerings).

## Disable app connectors

Review this information before you disable an app connector.

Note

- Before disabling an app connector, make sure you have the connection details available as you'll need them if you want to re-enable the connector.
- These steps can't be used to disable conditional access app control apps and security configuration apps.

To disable connected apps:

1. Go to **Connected apps**.
2. Select **Disable App connector**.
3. Select **Disable App connector instance** to confirm the action.

Once disabled, the connector instance stops consuming data from the connector.

## Re-enable app connectors

To re-enable connected apps:

1. Go to **Connected apps**.
2. Select **Edit settings**. This action starts the process to add a connector.
3. Add the connector using the steps in the relevant API connector guide. For example, if you're re-enabling GitHub, use the steps in [Connect GitHub Enterprise Cloud to Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-github#connect-github-enterprise-cloud-to-microsoft-defender-for-cloud-apps).

## Troubleshoot missing activities

If expected activities don't appear after you connect an app, see [Troubleshoot missing activities after connecting an app](https://learn.microsoft.com/en-us/defender-cloud-apps/troubleshooting-api-connectors-errors#troubleshoot-missing-activities-after-you-connect-an-app).

## Next steps

- [Best practices for protecting your organization](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices)
