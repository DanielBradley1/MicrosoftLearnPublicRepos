<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/formssettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# formsSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Company-wide settings for Microsoft Forms. This object is configured in the **settings** property of [adminForms](https://learn.microsoft.com/en-us/graph/api/resources/adminforms?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isBingImageSearchEnabled | Boolean | Controls whether users can add images from Bing to forms. |
| isExternalSendFormEnabled | Boolean | Controls whether users can send a link to a form to an external user. |
| isExternalShareCollaborationEnabled | Boolean | Controls whether users can collaborate on a form layout and structure with an external user. |
| isExternalShareResultEnabled | Boolean | Controls whether users can share form results with external users. |
| isExternalShareTemplateEnabled | Boolean | Controls whether users can share form templates with external users. |
| isInOrgFormsPhishingScanEnabled | Boolean | Controls whether phishing protection is run on forms created by users, blocking the creation of forms if common phishing questions are detected. |
| isRecordIdentityByDefaultEnabled | Boolean | Controls whether the names of users who fill out forms are recorded. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.formsSettings",
  "isExternalSendFormEnabled": "Boolean",
  "isExternalShareCollaborationEnabled": "Boolean",
  "isExternalShareResultEnabled": "Boolean",
  "isExternalShareTemplateEnabled": "Boolean",
  "isRecordIdentityByDefaultEnabled": "Boolean",
  "isBingImageSearchEnabled": "Boolean",
  "isInOrgFormsPhishingScanEnabled": "Boolean"
}
```
