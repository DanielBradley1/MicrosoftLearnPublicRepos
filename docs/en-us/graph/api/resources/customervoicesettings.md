<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customervoicesettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# customerVoiceSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Company-wide settings for Microsoft Dynamics 365 Customer Voice. This object is configured in the **customerVoice** property of [adminDynamics](https://learn.microsoft.com/en-us/graph/api/resources/admindynamics?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isInOrgFormsPhishingScanEnabled | Boolean | Controls whether phishing protection is run on forms created by users, blocking the creation of forms if common phishing questions are detected. |
| isRecordIdentityByDefaultEnabled | Boolean | Controls whether the names of users who fill out forms are recorded. |
| isRestrictedSurveyAccessEnabled | Boolean | Controls whether only users inside your organization can submit a response. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customerVoiceSettings",
  "isRestrictedSurveyAccessEnabled": "Boolean",
  "isRecordIdentityByDefaultEnabled": "Boolean",
  "isInOrgFormsPhishingScanEnabled": "Boolean"
}
```
