<!-- Source: https://learn.microsoft.com/en-us/graph/teams-licenses -->
<!-- Sitemap-Last-Modified: 2025-05-08 -->

# Payment models and licensing requirements for Microsoft Teams APIs

Important

Starting August 25, 2025, the Teams APIs listed in this article are no longer metered, and no billing configuration is required to use these APIs. If your application is configured for billing, no action is required. This article is provided for reference as the final billing cycle for metered Microsoft Teams APIs concludes.

As a result of this change, the `model` query parameter is no longer required and is ignored when supplied. License enforcement isn't applicable unless explicitly specified in the documentation for the respective API.

The following exceptions apply:

- Teams meeting AI insights APIs continue to require [Microsoft 365 Copilot](https://www.microsoft.com/microsoft-365/copilot) license.
- [Data Loss Protection](https://learn.microsoft.com/en-us/graph/api/chatmessage-update) \(DLP\) PATCH APIs require a [license](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-data-loss-prevention-graph-apis-for-teams-data-loss-prevention-dlp-and-for-teams-export) that includes the Microsoft Communications DLP [service plan](https://learn.microsoft.com/en-us/azure/active-directory/enterprise-users/licensing-service-plan-reference).

This article is deprecated and will be removed in June 2026. It's provided for reference only.

This article describes the payment models and licensing requirements for Microsoft Teams APIs in Microsoft Graph. For a high-level description of metered APIs and services in Microsoft Graph, see [Overview of metered APIs and services in Microsoft Graph](https://learn.microsoft.com/en-us/graph/metered-api-overview).

Some APIs provide the option to choose a licensing and payment model via the `model` query parameter; others only support one model or don't support a licensing and payment model.

The following table lists the APIs and [change notification](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions) `resources` that currently support payment models.

| APIs or [change notification](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions) `resources` | Payment models |
| :--- | :--- |
| [Change notification](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions) `resources`:<br><br>- /chats/getAllMessges<br>- /teams/getAllMessages<br>- /chats/getAllMembers<br>- /teams/getAllMembers | A, B |
| [Change notification](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions) `resources`:<br><br>- /users/{user-id}/chats/getAllMessages<br>- /me/chats/getAllMessages<br>- /appCatalogs/teamsApps/{app-id}/installedToChats<br>- /appCatalogs/teamsApps/{app-id}/installedToChats/getAllMessages<br>- /appCatalogs/teamsApps/{app-id}/installedToChats/getAllMembers | B |
| [Export APIs](https://learn.microsoft.com/en-us/microsoftteams/export-teams-content):<br><br>- [GET /users/{user-id}/chats/getAllMessages](https://learn.microsoft.com/en-us/graph/api/chats-getallmessages)<br>- [GET /users/{user-id}/chats/getAllRetainedMessages](https://learn.microsoft.com/en-us/graph/api/chat-getallretainedmessages)<br>- [GET /me/chats/getAllMessages](https://learn.microsoft.com/en-us/graph/api/chats-getallmessages)<br>- [GET /teams/{team-id}/channels/getAllMessages](https://learn.microsoft.com/en-us/graph/api/channel-getallmessages)<br>- [GET /teams/{team-id}/channels/getAllRetainedMessages](https://learn.microsoft.com/en-us/graph/api/channel-getallretainedmessages)<br>- [GET /teamwork/deletedTeams/{deletedTeamId}/channels/getAllMessages](https://learn.microsoft.com/en-us/graph/api/deletedteam-getallmessages) | A, B |
| PATCH APIs, when updating the `policyViolation` property:<br><br>- [PATCH /teams/{team-id}/channels/{channel-id}/messages/{message-id}](https://learn.microsoft.com/en-us/graph/api/chatmessage-update)<br>- [PATCH /teams/\(team-id\)/channels/{channel-id}/messages/{message-id}/replies/{reply-id}](https://learn.microsoft.com/en-us/graph/api/chatmessage-update)<br>- [PATCH /chats/{chatThread-id}/messages/{message-id}](https://learn.microsoft.com/en-us/graph/api/chatmessage-update) | A |
| Teams meeting APIs:<br><br>- [GET /users/{userId}/onlineMeetings/{meetingId}/transcripts/{transcriptId}/content](https://learn.microsoft.com/en-us/graph/api/calltranscript-get#example-2-get-a-calltranscript-content)<br>- [GET /users/{userId}/onlineMeetings/{meetingId}/transcripts/{transcriptId}/metadataContent](https://learn.microsoft.com/en-us/graph/api/calltranscript-get#example-4-get-a-calltranscript-metadatacontent)<br>- [GET /users/{userId}/onlineMeetings/{meetingId}/recordings/{recordingId}/content](https://learn.microsoft.com/en-us/graph/api/callrecording-get#example-2-get-callrecording-content)<br>- [GET /copilot/users/{userId}/onlineMeetings/{meetingId}/aiInsights/{aiInsightId}](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api/ai-services/meeting-insights/callaiinsight-get) | No model parameter |

Note

To set up an active Azure subscription for your application for billing purposes, see [Enable metered Microsoft 365 APIs and services](https://learn.microsoft.com/en-us/graph/metered-api-setup). For more information, see [Payment and billing updates](#payment-and-billing).

## Payment models

The following payment models are available:

- [`model=A`](#modela-requirements) is restricted to applications performing a [security or compliance function](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftAzure/MCA#ServiceSpecificTerms), and requires a [supported license](#required-licenses-for-modela).
- [`model=B`](#modelb-requirements) is restricted to applications that don't perform a [security or compliance function](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftAzure/MCA#ServiceSpecificTerms). There are no licensing requirements for `model=B`.
- [Evaluation mode \(default\)](#evaluation-mode-default-requirements) enables access to APIs with limited usage per requesting application for evaluation purposes. Change notifications aren't sent if the limit is exceeded.

Note

To add or change a payment model for a subscribed resource of a change notification, you must create a new change notification subscription with the new payment model. Updating an existing change notification does not work.

### `model=A` requirements

`model=A` is restricted to applications performing a security or compliance function. For details, see the API Terms for Security & Compliance Applications section of the [product terms for Microsoft Azure Services](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftAzure/MCA#ServiceSpecificTerms).

The following APIs support the `model=A` parameter.

| APIs or [change notification](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions) `resources` | Who needs a [license](#required-licenses-for-modela) | [Seeded capacity](#seeded-capacity) | [Price for additional use](#payment-and-billing) | Notes |
| :--- | :--- | :--- | :--- | :--- |
| [Change notification](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions) `resources`:<br><br>- /chats/getAllMessges<br>- /teams/getAllMessages | Message sender | \(800 messages × supported licenses with DLP enabled\) per month per app | $0.00075 per message | Seeded capacity is shared with conversationMember change notifications |
| [Change notification](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions) `resources`:<br><br>- /chats/getAllMembers<br>- /teams/getAllMembers | Any user in the tenant | \(800 notifications × supported licenses with DLP enabled\) per month per app | $0.00075 per notification | Seeded capacity is shared with chatMessage change notifications |
| APIs:<br><br>- [GET /users/{user-id}/chats/getAllMessages](https://learn.microsoft.com/en-us/graph/api/chats-getallmessages)<br>- [GET /users/{user-id}/chats/getAllRetainedMessages](https://learn.microsoft.com/en-us/graph/api/chat-getallretainedmessages)<br>- [GET /me/chats/getAllMessages](https://learn.microsoft.com/en-us/graph/api/chats-getallmessages) | Named user | \(1600 messages × supported licenses with DLP enabled\) per month per app | $0.00075 per message | The named user is the user identified in the GET request URL. Requests that return an empty list isn't charged. Seeded capacity is shared with channel export. |
| APIs:<br><br>- [GET /teams/{team-id}/channels/getAllMessages](https://learn.microsoft.com/en-us/graph/api/channel-getallmessages)<br>- [GET /teams/{team-id}/channels/getAllRetainedMessages](https://learn.microsoft.com/en-us/graph/api/channel-getallretainedmessages)<br>- [GET /teamwork/deletedTeams/{deletedTeamId}/channels/getAllMessages](https://learn.microsoft.com/en-us/graph/api/deletedteam-getallmessages) | Any team member | \(1600 messages × supported licenses with DLP enabled\) per month per app | $0.00075 per message | Requests that return an empty list isn't charged. Seeded capacity is shared with chat export. |
| APIs, when updating the `policyViolation` property:<br><br>- [PATCH /teams{team-id}/channels/{channel-id}/messages/{message-id}](https://learn.microsoft.com/en-us/graph/api/chatmessage-update)<br>- [PATCH /teams/\(team-id\)/channels/{channel-id}/messages/{message-id}/replies/{reply-id}](https://learn.microsoft.com/en-us/graph/api/chatmessage-update)<br>- [PATCH /chats/{chatThread-id}/messages/{message-id}](https://learn.microsoft.com/en-us/graph/api/chatmessage-update) | Message sender | \(800 messages × supported licenses with DLP enabled\) per month per app | $0.00075 per message |  |

#### Required licenses for `model=A`

The user needs a license that supports the Microsoft Communications DLP [service plan](https://learn.microsoft.com/en-us/azure/active-directory/enterprise-users/licensing-service-plan-reference), such as one of these [supported licenses](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-data-loss-prevention-graph-apis-for-teams-data-loss-prevention-dlp-and-for-teams-export). Which user needs the license varies by API; for details, see [`model=A` requirements](#modela-requirements).

Guest users are exempt from these licensing requirements. Similarly, messages sent from outside the tenant \(federated chat\) are exempt. Consumption meters still apply.

It's the responsibility of the tenant owner \(not the app owner\) to ensure that users are properly licensed. Admins can use the [Information protection license report](https://learn.microsoft.com/en-us/microsoftteams/teams-analytics-and-reports/information-protection-license-report) in [Teams admin center](https://admin.teams.microsoft.com/analytics/reports) to see which users don't have a supported license.

Many supported licenses offer free trials. [Office 365 E5](https://www.microsoft.com/microsoft-365/enterprise/office-365-e5?activetab=pivot%3aoverviewtab) for instance has a **Free trial** link under the **Buy** button.

You might qualify for one through the [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program); for details, see the [FAQ](https://learn.microsoft.com/en-us/office/developer-program/microsoft-365-developer-program-faq#who-qualifies-for-a-microsoft-365-e5-developer-subscription-). Alternatively, you can [sign up for a 1-month free trial or purchase a Microsoft 365 plan](https://www.microsoft.com/en-us/microsoft-365/try).

Note

The Microsoft Communications DLP [service plan](https://learn.microsoft.com/en-us/azure/active-directory/enterprise-users/licensing-service-plan-reference) must be enabled before it can be licensed. You can manage licenses in the [Microsoft Entra admin center](https://entra.microsoft.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products) or the [Microsoft 365 admin center](https://admin.microsoft.com). You can also assign licenses to a group account by using [Microsoft Graph Graph REST API and PowerShell SDK](https://learn.microsoft.com/en-us/azure/active-directory/enterprise-users/licensing-ps-examples).

### `model=B` requirements

`model=B` is restricted to applications that don't perform a security or compliance function. For details, see the [API Terms for Security & Compliance Applications](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftAzure/MCA#ServiceSpecificTerms) section of the product terms for Microsoft Azure Services.

The following APIs support the `model=B` parameter.

| APIs or [change notification](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions) `resources` | [Seeded capacity](#seeded-capacity) | [Price for use](#payment-and-billing) | Notes |
| :--- | :--- | :--- | :--- |
| [Change notification](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions) `resources`:<br><br>- /chats/getAllMessages<br>- /teams/getAllMessages<br>- /users/{user-id}/chats/getAllMessages<br>- /me/chats/getAllMessages<br>- /appCatalogs/teamsApps/{app-id}/installedToChats/getAllMessages | None | $0.00075 per message |  |
| [Change notification](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions) `resources`:<br><br>- /chats/getAllMembers<br>- /teams/getAllMembers<br>- /appCatalogs/teamsApps/{app-id}/installedToChats/getAllMembers | None | $0.00075 per notification |  |
| [Change notification](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions) `resources`:<br><br>- /appCatalogs/teamsApps/{app-id}/installedToChats | None | $0.00075 per message |  |
| APIs:<br><br>- [GET /users/{user-id}/chats/getAllMessages](https://learn.microsoft.com/en-us/graph/api/chats-getallmessages)<br>- [GET /users/{user-id}/chats/getAllRetainedMessages](https://learn.microsoft.com/en-us/graph/api/chat-getallretainedmessages)<br>- [GET /me/chats/getAllMessages](https://learn.microsoft.com/en-us/graph/api/chats-getallmessages) | None | $0.00075 per message | Requests that return an empty list isn't charged. |
| APIs:<br><br>- [GET /teams/{team-id}/channels/getAllMessages](https://learn.microsoft.com/en-us/graph/api/channel-getallmessages)<br>- [GET /teams/{team-id}/channels/getAllRetainedMessages](https://learn.microsoft.com/en-us/graph/api/channel-getallretainedmessages)<br>- [GET /teamwork/deletedTeams/{deletedTeamId}/channels/getAllMessages](https://learn.microsoft.com/en-us/graph/api/deletedteam-getallmessages) | None | $0.00075 per message | Requests that return an empty list isn't charged. |

### Evaluation mode \(default\) requirements

The following APIs support evaluation mode. The evaluation quota is enforced per app, per tenant, per month. The quota is reset at the beginning of each calendar month, and any unused amount doesn't get carried over to the next month.

| APIs or [change notification](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions) `resources` | Evaluation quota | [Price for additional use](#payment-and-billing) | Notes |
| :--- | :--- | :--- | :--- |
| [Change notification](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions) `resources`:<br><br>- /chats/getAllMessges<br>- /teams/getAllMessages<br>- /users/{user-id}/chats/getAllMessages<br>- /me/chats/getAllMessages<br>- /appCatalogs/teamsApps/{app-id}/installedToChats/getAllMessages | 500 messages per month per tenant per app | N/A |  |
| [Change notification](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions) `resources`:<br><br>- /chats/getAllMembers<br>- /teams/getAllMembers<br>- /appCatalogs/teamsApps/{app-id}/installedToChats/getAllMembers | 500 messages per month per tenant per app | N/A |  |
| [Change notification](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions) `resources`:<br><br>- /appCatalogs/teamsApps/{app-id}/installedToChats | 500 messages per month per app | N/A |  |
| APIs:<br><br>- [GET /users/{user-id}/chats/getAllMessages](https://learn.microsoft.com/en-us/graph/api/chats-getallmessages)<br>- [GET /users/{user-id}/chats/getAllRetainedMessages](https://learn.microsoft.com/en-us/graph/api/chat-getallretainedmessages)<br>- [GET /me/chats/getAllMessages](https://learn.microsoft.com/en-us/graph/api/chats-getallmessages) | 500 messages per month per tenant per app | N/A | Requests that return an empty list isn't charged. |
| APIs:<br><br>- [GET /teams/{team-id}/channels/getAllMessages](https://learn.microsoft.com/en-us/graph/api/channel-getallmessages)<br>- [GET /teams/{team-id}/channels/getAllRetainedMessages](https://learn.microsoft.com/en-us/graph/api/channel-getallretainedmessages)<br>- [GET /teamwork/deletedTeams/{deletedTeamId}/channels/getAllMessages](https://learn.microsoft.com/en-us/graph/api/deletedteam-getallmessages) | 500 messages per month per tenant per app | N/A | Requests that return an empty list isn't charged. |
| APIs, when updating the `policyViolation` property:<br><br>- [PATCH /teams{team-id}/channels/{channel-id}/messages/{message-id}](https://learn.microsoft.com/en-us/graph/api/chatmessage-update)<br>- [PATCH /teams/\(team-id\)/channels/{channel-id}/messages/{message-id}/replies/{reply-id}](https://learn.microsoft.com/en-us/graph/api/chatmessage-update)<br>- [PATCH /chats/{chatThread-id}/messages/{message-id}](https://learn.microsoft.com/en-us/graph/api/chatmessage-update) | 500 messages per month per tenant per app | N/A |  |
| Teams meeting transcript APIs:<br><br>- [GET /users/{userId}/onlineMeetings/{meetingId}/transcripts/{transcriptId}/content](https://learn.microsoft.com/en-us/graph/api/calltranscript-get#example-2-get-a-calltranscript-content)<br>- [GET /users/{userId}/onlineMeetings/{meetingId}/transcripts/{transcriptId}/metadataContent](https://learn.microsoft.com/en-us/graph/api/calltranscript-get#example-4-get-a-calltranscript-metadatacontent) | 600 minutes per month per tenant per app | N/A |  |
| Teams meeting recording APIs:<br><br>- [GET /users/{userId}/onlineMeetings/{meetingId}/recordings/{recordingId}/content](https://learn.microsoft.com/en-us/graph/api/callrecording-get#example-2-get-callrecording-content) | 600 minutes per month per tenant per app | N/A |  |

## Seeded capacity

Seeded capacity is the amount of capacity that an app can use before a consumption meter is charged. Capacity is pooled at the tenant level—the seeded capacity for all users in the tenant is compared against the app's usage in the tenant. Seeded capacity is per app per tenant—an app doesn't run out of seeded capacity if another app runs out. Seeded capacity is reset at the beginning of each calendar month, and any unused amount doesn't get carried over to the next month.

| Payment model | Use cases | Seeded capacity | License required | Azure subscription required |
| :--- | :--- | :--- | :--- | :--- |
| `model=A` | Security and Compliance | See [`model=A` requirements](#modela-requirements) | Yes \(Microsoft 365 E5 eligible license\) | Yes |
| `model=B` | Backup and restore, migration, sentiment analysis, analytics and insights | None | No | Yes |

Seeded capacity isn't applicable for Teams meeting APIs. For details, see [Payment requirements for Meeting APIs](#payment-requirements-for-meeting-apis).

## Payment requirements for meeting APIs

This section describes the payment requirements for Teams meeting transcript and recording APIs. These APIs don't support the model A and model B payment models and can be used by any application, regardless of the use case.

These APIs support an [evaluation mode](#evaluation-mode-default-requirements) that apps can use without configuring Azure billing. The following table summarizes the evaluation mode behavior.

| Azure billing setup | Result |
| --- | --- |
| Not configured | Evaluation mode capacity is available for download. The API fails with error code `402` \(Payment Required\). |
| Configured | Unlimited meeting content is available for download and priced based on per minute of content, as described in the following table. Engineering RPS limits still apply. |

The following table lists the prices for using Teams meeting APIs, applicable to both beta and v1.0 endpoints.

| APIs | [Seeded capacity](#seeded-capacity) | [Price for use](#payment-and-billing) | Notes |
| :--- | :--- | :--- | :--- |
| Teams meeting recording APIs:<br><br>- [GET /users/{userId}/onlineMeetings/{meetingId}/recordings/{recordingId}/content](https://learn.microsoft.com/en-us/graph/api/callrecording-get#example-2-get-callrecording-content) | None | $0.003 per minute | The duration is rounded down to the nearest minute. |
| Teams meeting transcript APIs:<br><br>- [GET /users/{userId}/onlineMeetings/{meetingId}/transcripts/{transcriptId}/content](https://learn.microsoft.com/en-us/graph/api/calltranscript-get#example-2-get-a-calltranscript-content)<br>- [GET /users/{userId}/onlineMeetings/{meetingId}/transcripts/{transcriptId}/metadataContent](https://learn.microsoft.com/en-us/graph/api/calltranscript-get#example-4-get-a-calltranscript-metadatacontent) | None | $0.0022 per minute | The duration is rounded down to the nearest minute. |

## License requirements for Teams meeting AI insights APIs

This section describes the license requirements for Teams meeting AI insights APIs. To access the beta endpoint, users must have a [Microsoft 365 Copilot](https://www.microsoft.com/en-us/microsoft-365/copilot) license. Payment models or evaluation mode aren't applicable for these APIs; they can be used by any application for users who have the required license.

## Payment and billing

If your applications are using any of the aforementioned APIs or [change notification](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions) `resources`, you must follow the steps described in [Enable metered Microsoft 365 APIs and services](https://learn.microsoft.com/en-us/graph/metered-api-setup) to set up an active Azure subscription for billing purposes.

The organization that owns the app registration is responsible for the payment. The Azure subscription should also be active in the same tenant. For multitenant apps, the organization that registered the app might be different than the organization that runs the app.

## Payment-related errors

If incorrect licensing is detected, the API call fails and data isn't returned. Specifically, for most APIs, attempting to GET messages for an unlicensed user, results in a `402` error code. For change notifications, messages sent by unlicensed users don't generate a change notification. API calls and change notifications used in evaluation mode in excess of the evaluation quota fails.

| Error code | Scenario | Sample error message |
| :--- | :--- | :--- |
| 402 \(Payment Required\) | Missing an active Azure billing subscription | `...To call this API, the app must be associated with an Azure subscription, see https://aka.ms/teams-api-payment-requirements for details....` |
| 402 \(Payment Required\) | Passing `model=A` without a Microsoft E5 license or without DLP enabled | `...needs a valid license to access this API...`, `...tenant needs a valid license to access this API...` |
| 402 \(Payment Required\) | Calling Patch API passing `model=B` | `...query parameter 'model' does not support value 'B' for this API. Use billing model 'A'...` |
| 402 \(Payment Required\) | `Evaluation mode` capacity exceeded | `...evaluation capacity for the month has exceeded. To continue beyond the evalution limits complete billing onboarding...` |

Note

A successful API call does not mean that the required licensing is in place. Similarly, API success in evaluation model does not guarantee that the call is within seeded capacity.

## View the costs billed for the metered Microsoft Teams APIs

This section describes how to monitor costs billed for the metered Microsoft Teams APIs.

A subscription owner, or anyone with appropriate [RBAC \(Roles Based Access Control\) permissions](https://learn.microsoft.com/en-us/azure/cost-management-billing/costs/assign-access-acm-data), can use **Cost Analysis** to track metered API consumption, as follows:

1. Sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com).
2. Go to [**Cost Management + Billing > Cost Management > Cost analysis**](https://ms.portal.azure.com/#view/Microsoft_Azure_CostManagement/Menu/%7E/costanalysis).
3. For the filter near the top, select **Service name: Microsoft Graph Services**.
4. For the **Group by** dropdown menu near the right, select **Meter**.

This view offers a convenient way to observe API consumption per day over a period of time.

You can also use the pie charts near the bottom to further breakdown the costs for analysis, using the **Resource** and **Meter** filters.

![Screenshot of the Cost Management and Billing page in the Azure portal](https://learn.microsoft.com/en-us/graph/images/cost-analysis-sample.png)

For more information about cost management, see [Cost Management + Billing documentation](https://learn.microsoft.com/en-us/azure/cost-management-billing/).

## Monitor the number of messages billed for the metered Teams APIs

This section describes how to monitor the number of messages billed for the metered Teams APIs. Unlike with cost analysis, you can analyze the usage of messages within the seeded capacity, not just the ones above the seeded capacity for billing, if applicable to the selected licensing models.

A subscription owner, or anyone with required [RBAC \(Roles Based Access Control\) permissions](https://learn.microsoft.com/en-us/azure/cost-management-billing/costs/assign-access-acm-data), can set up a report, in CSV format, with the billing details for the entire subscription. You can export the report periodically \(daily, weekly, monthly\). For details, see [Tutorial: Create and manage exported data](https://learn.microsoft.com/en-us/azure/cost-management-billing/costs/tutorial-export-acm-data?tabs=azure-portal).

![Screenshot of an exported CSV file](https://learn.microsoft.com/en-us/graph/images/teams-export-csv-sample.png)

## Estimate the number of messages in your Teams

This section describes how to look up the number of messages in your Teams tenant. It can help you estimate the cost for using the metered APIs. If a message is retrieved through metered APIs multiple times, it's billed multiple times. Keep it in mind when you estimate the cost based on the number of messages in your Teams tenant. For example, if you called `getAllMessages` \(without any filters\) yesterday, and then call it again \(without any filters\) today, all messages from earlier than today are billed twice. For this reason, when using metered APIs, we recommend that you use filters \(for example, `$top=10`, `$filter=lastModifiedDateTime gt 2019-03-17T07:13:28.000z`\) or [change notifications](https://learn.microsoft.com/en-us/graph/teams-change-notification-in-microsoft-teams-overview) to avoid retrieving the same message multiple times.

You can also call the [getTeamsUserActivityUserDetail](https://learn.microsoft.com/en-us/graph/api/reportroot-getteamsuseractivityuserdetail) API, or you can use the [Microsoft Teams Admin Center](https://admin.teams.microsoft.com/) as follows:

> **Note:** You must be either a Global Reader or Teams service admin to view the report in the [Microsoft Teams Admin Center](https://admin.teams.microsoft.com/). For details, see [Use Teams administrator roles to manage Teams](https://learn.microsoft.com/en-us/microsoftteams/using-admin-roles).

1. In the left pane, choose **Analytics & reports** > **Usage reports**.
2. On the **View reports** tab, under **Report**, choose **Teams user activity**.
3. Under **Date range**, select a range.
4. Choose **Run report**.

![Screenshot of the Teams User Activity report](https://learn.microsoft.com/en-us/graph/images/teams-user-activity-report-sample.png)

## Frequently asked questions

| Scenario | Details |
| :--- | :--- |
| Why was the number of messages billed higher than the number of messages in my Teams? | If your app is retrieving the same message multiple times, it is billed for multiple times. One way to avoid it is to use [change notifications](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions) instead of [export APIs](https://learn.microsoft.com/en-us/microsoftteams/export-teams-content). If you must use export APIs, make sure to use filters \(for example, `$filter=lastModifiedDateTime`, `$filter=from`\). |
| Did billing actually started on July 5? | Yes, we're onboarding partners in phases. For continued access, follow the instructions on [Enable metered Microsoft 365 APIs and services](https://learn.microsoft.com/en-us/graph/metered-api-setup) to set up an active Azure subscription for billing purposes. |
| What should I expect after setting up an Azure subscription? | Billing is effective immediately. You can monitor the costs as described in the [View the costs billed for the metered Microsoft Teams APIs](#view-the-costs-billed-for-the-metered-microsoft-teams-apis) section above. |
| Do I need to provide an Azure subscription if my application isn't calling metered APIs? | We recommend that you provide an Azure subscription because most scenarios use metered APIs. |
| What happens if no Azure subscription is provided? | \* No payment-related errors occur if the application isn't calling metered APIs.  <br>\* If no model parameter is passed, the `evaluation model` value is used by default.  <br>\* If calling a metered API passing `model=A`, provide a Microsoft 365 E5 eligible license and Azure subscription.  <br>\* If passing `model=B` when calling metered APIs, provide an active Azure subscription.  <br> |
| How do I create an Azure subscription? | The Azure subscription must be available in the same tenant where the app is registered. Customers with MCA or EA agreements can get a subscription from their existing account. Is also possible to create a PAYG subscription using a credit card or pay by check or wire transfer. For details, see [Enable metered Microsoft 365 APIs and services](https://learn.microsoft.com/en-us/graph/metered-api-setup) and [cost management and billing](https://learn.microsoft.com/en-us/azure/cost-management-billing/microsoft-customer-agreement). |
| Who is responsible for the payment in the case of multitenant apps? | The organization that owns the app registration. |
| Is possible to differentiate billing from multitenant or single tenant app? | Yes, this information must be provided as part of Azure billing details. |
| Is there a charge when no message is returned using any model? | To discourage frequent [polling](https://learn.microsoft.com/en-us/graph/api/resources/teams-api-overview), API requests that return an empty list of messages aren't charged. |
| Where can I monitor the cost and billing? | A subscription owner, or anyone with appropriate RBAC \(Roles Based Access Control\) can use Azure Cost Analysis tool to track consumption per day or filter by meter, service name, resource ID among other parameters. For more details, please see [View the costs billed for the metered Microsoft Teams APIs](#view-the-costs-billed-for-the-metered-microsoft-teams-apis) above. |
| Is there a volume discount? | Flat rates apply. |
| Are these APIs enrolled in [Microsoft Azure Consumption Commitment \(MACC\) program](https://learn.microsoft.com/en-us/azure/marketplace/azure-consumption-commitment-enrollment)? | Not at this time. |
