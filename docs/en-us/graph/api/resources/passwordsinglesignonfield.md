<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/passwordsinglesignonfield?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# passwordSingleSignOnField resource type

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains the fields to capture to fill the use credentials for Password-based single sign-on.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customizedLabel | String | Title/label override for customization. |
| defaultLabel | String | Label that would be used if no customizedLabel is provided. Read-only. |
| fieldId | String | Id used to identity the field type. This is an internal ID and possible values are `param_1`, `param_2`, `param_userName`, `param_password`. |
| type | String | Type of the credential. The values can be `text`, `password`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "customizedLabel": "String",
  "defaultLabel": "String",
  "fieldId": "String",
  "type": "String"
}
```
