<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/passwordsinglesignonsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-16 -->

# passwordSingleSignOnSettings resource type

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains the collection of password-based single sign-on settings.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| fields | [passwordSingleSignOnField](https://learn.microsoft.com/en-us/graph/api/resources/passwordsinglesignonfield?view=graph-rest-beta) collection | The fields to capture to fill the user credentials for password-based single sign-on. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "fields": [{"@odata.type": "microsoft.graph.passwordSingleSignOnField"}]
}
```
